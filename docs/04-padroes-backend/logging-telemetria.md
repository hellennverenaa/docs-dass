# Diretriz Corporativa: Logging Estruturado e Telemetria

## 1. Visão Geral e Princípios
A observabilidade das aplicações em produção e ambientes de chão de fábrica exige rastreabilidade centralizada e análise automatizada. Toda aplicação backend deve emitir logs em **stdout/stderr** formatados exclusivamente em **JSON estruturado**.

---

## 2. Esquema Obrigatório de Log (JSON Schema)

Todo registro de log deve conter obrigatoriamente as seguintes propriedades na raiz do objeto JSON:

```json
{
  "timestamp": "2026-09-17T13:50:00.123Z",
  "level": "INFO",
  "trace_id": "018e4f1a-bc3d-789a-b123-c456789abcde",
  "unit_id": "SEST",
  "service": "api-apontamentos",
  "message": "Apontamento de lote finalizado com sucesso.",
  "context": {
    "ordem_id": "018e4f1a-aa11-7000-8000-000000000001",
    "operador_id": "USR_982",
    "quantidade_processada": 120
  }
}
```

### Detalhamento dos Campos Obrigatórios:
* `timestamp` *(string)*: Carimbo temporal em ISO-8601 com precisão em milissegundos e fuso UTC.
* `level` *(string)*: Nível de severidade padronizado (`DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL`).
* `trace_id` *(string)*: Identificador de rastreamento distribuído (`UUID` ou padrão W3C TraceContext) propagado entre gateways e microsserviços.
* `unit_id` *(string)*: Identificador corporativo da fábrica de origem da operação.
* `message` *(string)*: Mensagem textual descritiva da ocorrência.
* `context` *(object, opcional)*: Objeto aninhado contendo metadados relevantes para a depuração.

---

## 3. Níveis de Log e Diretrizes de Uso

* **`ERROR` / `FATAL`:** Falhas não tratadas, indisponibilidade de banco/Redis, erros de integridade transacional e quedas de dependências externas.
* **`WARN`:** Comportamentos inesperados recuperados automaticamente (ex: retry de conexão MQTT bem-sucedido, payload com formato depreciado).
* **`INFO`:** Eventos significativos de negócio (ex: inicialização do servidor, fechamento de ordem de produção, login bem-sucedido).
* **`DEBUG`:** Detalhes granulares de execução, restritos a ambientes de desenvolvimento e homologação (desativados por padrão em produção).

---

## 4. Regras de Segurança e Conformidade
* **Dados Sensíveis (PII):** É terminantemente proibido registrar senhas, tokens JWT completos, números de cartão ou dados pessoais sensíveis nos logs.
* **Saída Padrão:** Logs devem ser emitidos no console (`stdout`/`stderr`) para coleta desacoplada pelos agentes de telemetria do Docker e PM2.
