# Padrões de Arquitetura e Engenharia de Software

Este repositório centraliza as diretrizes técnicas, padrões arquiteturais e fluxos de dados oficiais adotados no desenvolvimento e manutenção de todas as nossas aplicações.

---

## Topologia Geral da Nossa Infraestrutura

O diagrama abaixo ilustra o fluxo completo de uma requisição desde a borda até o banco de dados corporativo:

```mermaid
flowchart TD
    subgraph C1 [Camada 1: Borda e Roteamento - Gateways]
        GW_EXT[Acesso das Fábricas e Filiais - HTTPS 443]
        GW_FRONT[Gateway Front-End - Aplicações Vue 3]
        GW_BACK[Gateway Back-End - Rotas de API]
    end

    subgraph C2 [Camada 2: Servidor Web e Autenticação]
        APACHE[Apache HTTP Server - Proxy Reverso e SSL]
        AUTH_JWT[Serviço de Autenticação - JWT e Validação de Filial]
    end

    subgraph C3 [Camada 3: Execução de Aplicações - Workloads]
        subgraph DOCKER_BOX [Ambiente Docker]
            API_DK1[Nossas APIs em Container - Node.js e TypeORM]
            API_DK2[Serviços Isolados]
        end
        subgraph PM2_BOX [Ambiente PM2]
            APP_PM1[Aplicações em Node.js - Cluster PM2]
            APP_PM2[Workers e Rotinas em Segundo Plano]
        end
    end

    subgraph C4 [Camada 4: Persistência de Dados]
        DB[(PostgreSQL Único - RLS e Isolamento por unit_id)]
    end

    GW_EXT --> GW_FRONT
    GW_EXT --> GW_BACK

    GW_FRONT -.-> APACHE
    GW_BACK --> APACHE

    APACHE <-->|Validação de Token e Sessão| AUTH_JWT

    APACHE -->|Proxy Pass| API_DK1
    APACHE -->|Proxy Pass| API_DK2
    APACHE -->|Proxy Pass localhost| APP_PM1
    APACHE -->|Proxy Pass localhost| APP_PM2

    API_DK1 --> DB
    API_DK2 --> DB
    APP_PM1 --> DB
    APP_PM2 --> DB
```

---

## Índice da Documentação

* [Padrões de Acesso a Dados (TypeORM)](docs/04-padroes-backend/orm-e-acesso-a-dados.md)
* [Convenções de Banco, UUIDv7 e Índices](docs/06-padroes-dados/convencoes-banco.md)
* [Estratégia Multi-Tenancy (Isolamento por unit_id)](docs/06-padroes-dados/estrategia-multi-tenancy.md)
* [Topologia de Camadas e Fluxos de Servidor](docs/03-arquitetura-infra/topologia-camadas-e-fluxos.md)