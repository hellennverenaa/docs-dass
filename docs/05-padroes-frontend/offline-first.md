# Diretriz Corporativa: Arquitetura Offline-First para Terminais Industriais

## 1. Visão Geral e Necessidade Operacional
Em ambientes fabris, instabilidades temporárias de rede local (Wi-Fi de galpão, manutenções em switches ou oscilações de link) não podem paralisar o apontamento de operadores em esteiras e bancadas.

As interfaces industriais devem operar sob a arquitetura **Offline-First**, permitindo o registro ininterrupto de eventos mesmo sem conexão ativa com o backend.

---

## 2. Diagrama de Fluxo de Contingência e Sincronização

```mermaid
flowchart TD
    subgraph OPERACAO_LOCAL [Terminal de Bancada / SPA Vue 3]
        APONTAMENTO[Operador Realiza Apontamento / Leitura]
        CHECK_NET{Status da Rede Online?}
        INDEXED_DB[(Fila Local: IndexedDB)]
        SYNC_ENGINE[Motor de Sincronizacao em Lote]
    end

    subgraph BACKEND_CENTRAL [Servidor Central]
        API_BACK[Endpoint de Ingestao em Lote / Bulk Sync]
        DB_POSTGRES[(PostgreSQL - Persistencia Final)]
    end

    APONTAMENTO --> CHECK_NET
    CHECK_NET -->|Nao - Modo Offline| INDEXED_DB
    CHECK_NET -->|Sim - Modo Online| API_BACK
    
    INDEXED_DB -->|Detecta Evento window:online| SYNC_ENGINE
    SYNC_ENGINE -->|Envia Lote Pendente via POST| API_BACK
    API_BACK --> DB_POSTGRES
    API_BACK -->|Confirmacao de Gravacao| SYNC_ENGINE
    SYNC_ENGINE -->|Limpa Registros Sincronizados| INDEXED_DB
```

---

## 3. Regras de Implementação no Front-End

### 3.1. Armazenamento Local via IndexedDB
* **Mecanismo:** Utilização da API nativa `IndexedDB` (preferencialmente encapsulada por bibliotecas leves e tipadas como `idb` ou `Dexie.js`).
* **Estrutura do Registro:** Todo apontamento enfileirado localmente deve possuir:
  * `client_id`: UUIDv7 gerado no próprio front-end para garantir unicidade e idempotência.
  * `unit_id`: Código da fábrica do operador.
  * `payload`: Dados estruturados da operação.
  * `created_at`: Carimbo de hora exata em que o operador realizou a ação física.
  * `sync_status`: Estado da fila (`PENDING`, `SYNCING`, `FAILED`).

### 3.2. Sincronização Automática e Idempotência
* **Gatilhos de Reenvio:**
  1. Evento nativo do navegador `window.addEventListener('online', ...)`.
  2. Heartbeat em segundo plano a cada 30 segundos verificando a disponibilidade do endpoint de healthcheck.
* **Envio em Lote (Bulk Sync):** O motor de sincronização deve despachar os registros pendentes em blocos únicos (ex: até 100 registros por chamada) para a rota `/api/v1/apontamentos/sync-batch`.
* **Proteção contra Duplicidade:** O backend deve utilizar o `client_id` (UUIDv7) como chave de desduplicação, garantindo que retransmissões não dupliquem apontamentos operacionais no banco.
