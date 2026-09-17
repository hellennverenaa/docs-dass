# Diretriz Corporativa: Checklist de Homologação e Entrada em Produção (Go/No-Go)

## 1. Visão Geral
Nenhuma aplicação, microsserviço ou rotina em segundo plano pode ser promovida para os ambientes de produção (Docker ou PM2) sem a validação formal dos itens deste checklist. O objetivo é eliminar paradas inesperadas de esteiras e garantir a integridade dos dados operacionais.

---

## 2. Checklist Obrigatório de Pré-Deploy

### 2.1. Banco de Dados e Migrations
- [ ] **Migrations Versionadas:** Todas as alterações estruturais de banco estão em arquivos de migração TypeORM testados e aprovados em ambiente de homologação.
- [ ] **Sincronização Desativada:** A flag `synchronize: false` está garantida nas configurações de produção.
- [ ] **Presença de `unit_id` e RLS:** Todas as novas tabelas transacionais contêm `unit_id VARCHAR(20) NOT NULL` e políticas de Row-Level Security habilitadas.
- [ ] **Índices Criados:** Índices de FK e compostos estão criados para evitar bloqueios (*table locks*) na carga operacional.

### 2.2. Containers e Configuração de Infraestrutura
- [ ] **Healthcheck Configurado:** O `Dockerfile` ou manifesto de orquestração possui instrução explícita de `HEALTHCHECK` apontando para o endpoint `/health` da aplicação.
- [ ] **Bind Local:** As portas de escuta estão configuradas estritamente em interfaces internas (`127.0.0.1` ou rede virtual interna do Docker), sem exposição direta na borda sem passar pelo Apache/Gateway.
- [ ] **Limites de Recursos:** Definição de limites máximos de memória e CPU configurados para o container ou processo PM2.

### 2.3. Configurações e Variáveis de Ambiente
- [ ] **Arquivo `.env.example` Atualizado:** Todas as variáveis de ambiente necessárias estão documentadas com descrições claras no repositório.
- [ ] **Segurança de Segredos:** Nenhuma senha, token JWT ou chave de API está hardcoded no código fonte ou na imagem Docker.
- [ ] **Conexão Redis e Pool PgBouncer:** URLs e portas apontam para o pool de conexões e instâncias corretas de produção.

### 2.4. Qualidade e Testes
- [ ] **Testes Automatizados:** Suíte de testes unitários e de integração aprovada sem falhas na pipeline de CI.
- [ ] **Contratos RFC 7807:** Respostas de erro formatadas no padrão corporativo de problem details.
- [ ] **Logging Estruturado:** Emissão de logs em formato JSON com `timestamp`, `level`, `trace_id`, `unit_id` e `message`.

---

## 3. Critérios de Rollback Imediato (No-Go)

O procedimento de rollback para a versão estável anterior deve ser acionado imediatamente se:
1. O endpoint de healthcheck falhar consecutivamente por mais de 60 segundos após o deploy.
2. A taxa de erros HTTP `5xx` na API ultrapassar 1% do volume total de requisições.
3. Ocorrer bloqueio ou contenção severa de conexões no PostgreSQL/PgBouncer.
