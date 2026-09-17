# Diretriz Corporativa: Gestão de Migrations de Banco de Dados

## 1. Visão Geral e Princípios
Toda evolução estrutural de esquema no PostgreSQL deve ser gerenciada exclusivamente por meio de **Migrations versionadas do TypeORM**.

---

## 2. Regras Rígidas de Governança

1. **Proibição do `synchronize`:** A sincronização automática do TypeORM (`synchronize: true`) é expressamente proibida em Homologação, QA e Produção. O esquema é alterado única e exclusivamente pela execução sequencial de migrations.
2. **Imutabilidade de Migrations Executadas:** Nunca edite um arquivo de migration que já tenha sido executado em ambientes compartilhados ou produção. Havendo necessidade de ajuste, crie uma nova migration corretiva.
3. **Compatibilidade Zero-Downtime:**
   * Evite renomear ou deletar colunas em uma única release. Adote a estratégia de duas fases (adicionar nova coluna $\rightarrow$ migrar dados $\rightarrow$ remover coluna legada na release seguinte).
   * Adicione colunas com valor padrão (`DEFAULT`) ou permitindo `NULL` para evitar bloqueios exclusivos de tabela (*exclusive table locks*).

---

## 3. Convenções de Nomenclatura e Comandos

### 3.1. Nomenclatura dos Arquivos
Os arquivos de migração gerados automaticamente pelo TypeORM devem possuir sufixos semânticos claros:
`{TIMESTAMP}-Create{NomeEntidade}Table.ts`
`{TIMESTAMP}-Add{NomeColuna}To{NomeEntidade}Table.ts`
`{TIMESTAMP}-Create{NomeIndice}Index.ts`

### 3.2. Comandos Padrão no `package.json`
```bash
# Gerar migration a partir de alterações nas entidades
npm run typeorm:migration:generate -- src/database/migrations/NomeDaAlteracao

# Criar arquivo de migration vazio para scripts SQL customizados
npm run typeorm:migration:create -- src/database/migrations/NomeDoScript

# Executar migrations pendentes
npm run typeorm:migration:run

# Reverter a última migration aplicada (apenas desenvolvimento)
npm run typeorm:migration:revert
```
