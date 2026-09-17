# Diretriz Corporativa: Padrões de API REST e Contratos de Resposta

## 1. Visão Geral e Princípios
Todas as APIs transacionais e serviços internos desenvolvidos no ecossistema corporativo devem seguir a arquitetura **RESTful**, garantindo consistência de contratos, previsibilidade e facilidade de integração entre módulos.

---

## 2. Convenções de URI e Verbos HTTP

* **Formato de Recursos:** Nomes no plural, em minúsculo e utilizando kebab-case (ex: `/api/v1/ordens-producao`, `/api/v1/materiais`).
* **Versionamento Obrigatório:** A versão da API deve estar presente no prefixo da rota (`/api/v1/`).
* **Uso Semântico dos Verbos HTTP:**
  * `GET`: Leitura e consulta de recursos (idempotente e seguro).
  * `POST`: Criação de recursos ou acionamento de processamentos específicos.
  * `PUT`: Substituição integral de um recurso existente.
  * `PATCH`: Atualização parcial de atributos específicos.
  * `DELETE`: Exclusão lógica do recurso.

---

## 3. Padrão de Erros: RFC 7807 (Problem Details)

Toda resposta com código de erro HTTP (`4xx` ou `5xx`) deve retornar obrigatoriamente o cabeçalho `Content-Type: application/problem+json` e o corpo formatado segundo a especificação **RFC 7807**:

### Exemplo de Resposta de Erro:
```json
{
  "type": "https://docs.empresa.com/erros/validacao-campos",
  "title": "Erro de Validação de Entrada",
  "status": 422,
  "detail": "Um ou mais campos enviados na requisição são inválidos.",
  "instance": "/api/v1/apontamentos/bancada-42",
  "unit_id": "SEST",
  "invalid_params": [
    {
      "name": "reading_value",
      "reason": "O valor de peso não pode ser negativo."
    },
    {
      "name": "sector_id",
      "reason": "Setor não encontrado ou inativo nesta unidade."
    }
  ]
}
```

### Campos Mandatórios da RFC 7807:
* `type` *(URI)*: Referência para a documentação ou categoria do erro.
* `title` *(string)*: Resumo legível e curto do tipo do problema.
* `status` *(number)*: Código de status HTTP idêntico ao cabeçalho de resposta.
* `detail` *(string)*: Explicação humana e detalhada sobre a ocorrência específica.
* `instance` *(URI)*: Endpoint exato onde o erro ocorreu.
* `unit_id` *(string)*: Identificador da unidade fabril do contexto da requisição.
* `invalid_params` *(array, opcional)*: Lista discriminada de campos inválidos em falhas de validação.

---

## 4. Padrão de Respostas de Sucesso

* **Criação de Registro (`201 Created`):** Deve incluir o cabeçalho `Location: /api/v1/recurso/{id}` e o corpo do recurso criado.
* **Exclusão Lógica (`204 No Content`):** Resposta vazia sem corpo.
* **Paginação por Cursor:** Metadados estruturados contendo `data` (lista de itens) e `cursor` (próximo ponteiro para consulta sequencial).
