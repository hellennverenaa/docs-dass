# ADR 0001: Adoção Mandatória de UUIDv7 como Chave Primária

* **Status:** Aceita
* **Data:** 2026-09-01
* **Decisores:** Comitê de Arquitetura e Engenharia de Software

---

## 1. Contexto e Declaração do Problema
O ecossistema opera com múltiplas fábricas distribuídas e bancos de dados transacionais com milhões de registros diários. O uso de identificadores inteiros auto-incrementais gerava riscos críticos de colisão de dados durante a consolidação de relatórios multi-unidade, além de permitir ataques de enumeração em endpoints de API. Por outro lado, o UUIDv4 tradicional provocava fragmentação severa de índices B-Tree no PostgreSQL devido à natureza puramente aleatória de seus bits.

---

## 2. Opções Avaliadas
* **Opção A (Inteiros Auto-increment / BigSerial):** Simples, mas causava risco de colisão entre unidades e fragilidade em APIs.
* **Opção B (UUIDv4 Aleatório):** Seguro contra colisão e enumeração, mas degradava a performance de escrita no banco devido a *index bloat* e fragmentação de páginas B-Tree.
* **Opção C (UUIDv7 Temporalmente Ordenável):** Combina timestamp UTC ordenado nos bits mais significativos com entropia aleatória global nos bits restantes.

---

## 3. Decisão
Adotar oficialmente o padrão **UUIDv7** como chave primária obrigatória (`id`) para todas as tabelas e entidades relacionais.

---

## 4. Consequências e Impactos

### Positivas:
* Eliminação total de colisões de chave em consolidações de dados entre fábricas.
* Manutenção da alta performance de inserção em índices B-Tree do PostgreSQL sem fragmentação, pois as chaves são sequenciais no tempo.
* Geração cliente-lado em terminais Offline-First com garantia de unicidade e idempotência.

### Negativas / Trade-offs Mitigados:
* Consumo de 16 bytes por registro no banco (em comparação com 8 bytes de `BIGINT`), considerado insignificante frente aos ganhos de governança e escalabilidade.
