# Glossário Corporativo de Arquitetura e Engenharia de Software

Este documento unifica a terminologia técnica e de domínio de negócio adotada em todos os projetos, repositórios e comunicações da engenharia.

---

## Termos Chave

### 1. `unit_id` (Identificador de Unidade / Tenant)
* **Definição:** Código alfanumérico curto (`VARCHAR(20)`) que identifica de forma unívoca cada fábrica, filial ou unidade fabril da corporação (ex: `SEST`, `ITAB`, `VDC`).
* **Aplicação:** É a chave primária de partição lógica multi-tenant em todas as tabelas operacionais e transacionais, extraído diretamente do token JWT na camada de autenticação.

### 2. `RLS` (Row-Level Security / Segurança a Nível de Linha)
* **Definição:** Mecanismo de segurança nativo do PostgreSQL que intercepta consultas SQL e restringe o acesso aos registros com base em políticas de segurança da sessão do banco.
* **Aplicação:** Garante que mesmo que uma query não possua cláusula `WHERE unit_id = ...`, o próprio motor do banco isole estritamente os dados da filial do operador autenticado.

### 3. `Workload` (Carga de Trabalho / Unidade de Execução)
* **Definição:** Todo processo computacional em execução que processa requisições HTTP, consome filas de mensageria ou executa rotinas agendadas em segundo plano.
* **Aplicação:** No ecossistema corporativo, os workloads são distribuídos entre containers Docker (APIs e microsserviços) e processos gerenciados pelo PM2 (clusters Node.js e workers locais).

### 4. `Data Mapper` (Padrão de Mapeamento Objeto-Relacional)
* **Definição:** Padrão arquitetural de acesso a dados onde as entidades de domínio são objetos puros desprovidos de lógica de persistência, ficando a cargo de repositórios dedicados (`Repository` no TypeORM) a comunicação com o banco.
* **Aplicação:** Padrão oficial e obrigatório para todas as entidades corporativas, sendo proibido o uso de *Active Record*.

### 5. `Apontamento` (Registro Transacional Fabril)
* **Definição:** Registro operacional de chão de fábrica emitido por operadores ou sensores industriais para indicar a execução de uma etapa produtiva (ex: pesagem de insumos, leitura de tag RFID em esteira, início/fim de lote ou parada de máquina).
* **Aplicação:** Eventos de alta criticidade e volume, tratados sob arquitetura Offline-First nos terminais e com ingestão em lote no backend.
