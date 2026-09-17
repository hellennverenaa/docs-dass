# Diretriz de Segurança: Autenticação Unificada e Sessões JWT

## 1. Visão Geral
Define o fluxo corporativo de autenticação, autorização setorial e ciclo de vida de tokens de acesso para usuários locais e de outras unidades fabris.

---

## 2. Diagrama do Fluxo de Login (A preencher pelo time)
<!-- Inserir sequenceDiagram do login externo via JWT aqui -->

---

## 3. Origem e Provedor de Identidade
* **Base de Usuários:** [Definir se autentica via banco próprio, LDAP corporativo ou Active Directory]
* **Escopo de Acesso:** Definição dos setores e permissões atribuídas.

---

## 4. Estrutura do Payload do Token JWT
Todo token emitido para nossas aplicações deve conter as seguintes claims obrigatórias:
* `sub`: Identificador único do usuário (UUID).
* `name`: Nome do operador ou gestor.
* `unit_id`: Unidade fabril ativa na sessão.
* `sectors`: Lista de setores autorizados (ex: `["CORTE", "COSTURA"]`).
* `roles`: Níveis de permissão do usuário.

---

## 5. Ciclo de Vida da Sessão e Renovação
* **Tempo de Expiração (Access Token):** [Ex: 15 minutos / 8 horas de turno]
* **Mecanismo de Renovação:** Estratégia de Refresh Token seguro.

---

## 6. Integração com Apache (Camada 2) e Validação nas APIs
* Explicação de como o Apache propaga os cabeçalhos de autorização (`Authorization: Bearer <token>`) e como as APIs em Docker e PM2 validam a assinatura criptográfica antes de processar as requisições.