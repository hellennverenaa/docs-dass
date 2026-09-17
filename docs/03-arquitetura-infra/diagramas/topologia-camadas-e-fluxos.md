# Diretriz de Infraestrutura: Topologia em 4 Camadas

## 1. Visão Geral
A infraestrutura de servidores e aplicações corporativas adota uma arquitetura em 4 camadas desacopladas. Essa estrutura garante segurança na borda, controle centralizado de autenticação, convivência flexível entre containers Docker e processos PM2, e persistência relacional unificada.

---

## 2. Camada 1: Borda e Roteamento (Gateways)
* **Gateway Front-End:** Responsável por responder requisições de páginas web, SPAs e assets visuais das ferramentas industriais.
* **Gateway Back-End:** Responsável pelo direcionamento de chamadas transacionais de APIs REST e integrações externas.
* **Comunicação Segura:** Todas as unidades conectam-se via DNS corporativo sob protocolo HTTPS (porta 443). Nenhuma porta de aplicação é exposta para a rede externa sem passar pelos gateways.

---

## 3. Camada 2: Servidor Web (Apache) e Autenticação (JWT)
* **Apache HTTP Server:** Opera como Proxy Reverso principal e gerenciador de conexões seguras. Distribui as requisições para os runtimes de aplicação (Docker e PM2).
* **Mecanismo de Auth JWT:** Responsável pela emissão, validação e verificação de integridade dos tokens criptográficos de sessão.
* **Repasse de Contexto:** Toda requisição autenticada repassada aos back-ends deve carregar os dados de identidade do usuário, sua unidade de origem e suas permissões setoriais via cabeçalhos seguros ou payload assinado.

---

## 4. Camada 3: Execução de Aplicações (Docker e PM2)
A organização adota um modelo híbrido de computação na camada intermediária:
* **Ambiente Docker:** Utilizado para novos microserviços, aplicações isoladas e componentes padronizados em containers, garantindo reprodutibilidade de ambiente.
* **Ambiente PM2:** Utilizado para aplicações e workers Node.js no sistema operacional, operando com balanceamento de instâncias via cluster e reinicialização automática em caso de falha.
* **Comunicação Segura:** As portas de escuta das aplicações em PM2 e Docker devem escutar estritamente em interfaces locais internas, sendo inacessíveis sem o roteamento do Apache.

---

## 5. Camada 4: Persistência Relacional (SQL)
* Banco de dados relacional centralizado (PostgreSQL) com suporte a particionamento lógico por `unit_id`.
* Aplicação das diretrizes corporativas de Row-Level Security (RLS), chaves primárias em UUIDv7 e índices com rastreamento temporal.