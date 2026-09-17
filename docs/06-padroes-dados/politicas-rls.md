# Diretriz: Estratégia de Isolamento Multi-Tenancy e Políticas RLS

## 1. Visão Geral
Adotamos oficialmente o padrão de **Banco Único com Isolamento Lógico por Identificador de Unidade (Shared Database)**, reforçado por políticas de segurança a nível de linha (**Row-Level Security - RLS**).

* **Objetivo:** Centralizar manutenções e custos em uma única infraestrutura, simplificar migrações do TypeORM e viabilizar relatórios gerenciais consolidados em tempo real entre todas as unidades.

---

## 2. Diagrama de Isolamento das Unidades

```mermaid
graph TD
    subgraph FABRICAS [Nossas Fábricas e Unidades]
        U1[Unidade 01 - Ex: SEST]
        U2[Unidade 02 - Outra Filial]
        GESTAO[Nossa Gestão e Supervisão]
    end

    subgraph NOSSOS_SISTEMAS [Nossas Aplicações Internas]
        API[Nossa API Backend - Node.js e TypeORM]
    end

    subgraph BANCO [Nosso Banco de Dados - PostgreSQL]
        subgraph SEGURANCA [Filtro Automático de Linha - RLS]
            RLS_CHECK{O registro pertence a esta unidade?}
        end
        
        subgraph DADOS [Nossas Tabelas]
            T_U1[Registros da Unidade 01]
            T_U2[Registros da Unidade 02]
        end
    end

    U1 -->|Acessa nossa aplicação| API
    U2 -->|Acessa nossa aplicação| API
    GESTAO -->|Visão Geral| API

    API -->|Informa a unidade da requisição| RLS_CHECK
    RLS_CHECK -->|Libera apenas| T_U1
    RLS_CHECK -->|Libera apenas| T_U2
    RLS_CHECK -->|Gestão com acesso total| DADOS
```

---

## 3. Fluxograma de Execução de uma Consulta

```mermaid
sequenceDiagram
    autonumber
    actor Operador as Operador na Fábrica
    participant Tela as Nosso Front-end (Vue 3)
    participant Back as Nossa API (Node.js)
    participant DB as Nosso PostgreSQL (RLS Ativo)

    Operador->>Tela: Solicita visualização de registros
    Tela->>Back: GET /api/v1/registros (Envia nosso token)
    Note over Back: API valida o token e extrai o identificador da unidade
    Back->>DB: Inicia transação e define o tenant da sessão
    Back->>DB: Executa a consulta
    Note over DB: Motor RLS restringe o resultado apenas a unidade informada
    DB-->>Back: Retorna estritamente os dados da fábrica do operador
    Back-->>Tela: Envia os dados estruturados
    Tela-->>Operador: Renderiza a listagem na tela
```

---

## 4. Regras Obrigatórias para Nossas Aplicações

### 4.1. Presença Obrigatória de `unit_id`
* Toda tabela transacional ou de cadastro operacional deve conter a coluna `unit_id VARCHAR(20) NOT NULL`.
* É proibido persistir registros operacionais sem a identificação da unidade de origem.
* O valor de `unit_id` deve ser extraído sempre do token validado na nossa API, nunca confiando em dados livres enviados pelo front-end.

### 4.2. Segurança Nativa (RLS)
* As tabelas devem ter o RLS habilitado no banco (`ALTER TABLE nome_tabela ENABLE ROW LEVEL SECURITY`).
* O banco de dados bloqueia consultas que tentem ler ou alterar registros de outras unidades.

### 4.3. Indexação Composta
* Índices em tabelas transacionais devem incluir `unit_id` no início da composição (ex: `unit_id, created_at` ou `unit_id, status`) para otimizar os planos de execução com o filtro do RLS.