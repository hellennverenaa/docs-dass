# ADR 0003: Padrão de Gateway de Borda (Traefik) e Segregação de Tráfego

* **Status:** Aceita
* **Data:** 2026-09-08
* **Decisores:** Comitê de Arquitetura e Engenharia de Software

---

## 1. Contexto e Declaração do Problema
Com a expansão de múltiplos serviços conteinerizados em Docker e aplicações locais em PM2, a infraestrutura precisava de uma camada de borda desacoplada (*Ingress*) capaz de gerenciar certificados SSL de forma centralizada, realizar roteamento baseado em caminhos e segregar os acessos de Front-End (Vue 3 / assets estáticos) das rotas de API Back-End.

---

## 2. Opções Avaliadas
* **Opção A (Exposição Direta de Portas do Docker/Node):** Inseguro e complexo de administrar em produção.
* **Opção B (Apache HTTP Server Monolítico na Borda):** Funcional para proxy reverso, mas com gerenciamento manual e rígido de certificados e descoberta dinâmica de containers.
* **Opção C (Arquitetura em Duas Camadas: Traefik na Borda + Apache Interno com JWT):** O Traefik assume a terminação HTTPS e roteamento de borda com auto-descoberta, repassando o tráfego para o Apache gerenciar a autenticação JWT e distribuição local.

---

## 3. Decisão
Adotar o **Traefik** como Gateway de Borda (Camada 1) para terminação SSL (porta 443) e segregação de tráfego, operando em conjunto com o Apache HTTP Server (Camada 2).

---

## 4. Consequências e Impactos

### Positivas:
* Ponto de entrada único e seguro para todas as filiais e fábricas.
* Renovação automática de certificados SSL e roteamento dinâmico de serviços.
* Camada de aplicação e banco completamente blindadas contra acessos externos diretos.

### Negativas / Trade-offs Mitigados:
* Adição de um salto de rede leve na borda, compensado pela agilidade operacional e segurança corporativa.
