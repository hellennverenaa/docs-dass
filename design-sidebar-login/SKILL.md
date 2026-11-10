---
name: automacao-design-system
description: Implementa ou atualiza login e sidebar no padrão visual oficial do setor de Automação DASS, usando os códigos e assets completos incorporados neste arquivo. Use quando o pedido envolver esse padrão de autenticação ou navegação.
---

# Automação Design System — referência autocontida

Implemente o login e/ou a sidebar oficiais de Automação DASS no projeto atual. Inspecione o projeto, adapte as integrações do destino e valide o resultado. Este arquivo contém a instrução da Skill, a documentação de referência e os componentes originais completos; não consulte o ERP Modelagem. O código original incluído nas seções de templates é a fonte de verdade visual.

## Interface da Skill no Codex

- Nome de exibição: **Automação Design System**
- Descrição curta: **Login e sidebar oficiais da Automação DASS**
- Cor da marca para a interface: `#4d46e0`
- Prompt sugerido: `Use $automacao-design-system para implementar o login e a sidebar oficiais nesta aplicação.`

## Fluxo de implementação

1. Identifique framework, versão, estrutura de rotas, autenticação, layout principal, estilos globais e biblioteca de ícones do projeto.
2. Leia as referências completas deste arquivo: primeiro Design System, depois Login/Sidebar e Dependências.
3. Em Vue 3, copie os blocos integrais `src/views/LoginView.vue` e `src/views/DashboardView.vue` abaixo. Preserve template, CSS scoped e interações. Altere somente identidade textual e ligações de negócio explicitamente personalizáveis.
4. Copie os PNGs incluídos em `assets/` para a pasta pública/de assets do app. Não deixe URL ou caminho absoluto para a instalação da Skill. A máscara do código original espera `../assets/brand-symbol-white.png` quando o SFC está em `src/views/`.
5. Substitua integrações ERP (`../api/axios`, `../api/auth.store`) por adaptadores do próprio projeto. Não copie endpoints, sessão, lista de permissões, usuários, tokens nem regras internas do ERP.
6. Personalize nome/subtítulo e configuração dos menus, rotas, grupos, permissões, usuário, autenticação e ações do produto, mantendo todos os estilos, medidas, logo, estados e comportamento responsivo.
7. Integre com router e layout atuais sem duplicar shell ou criar rotas conflitantes. Confira login, sidebar expandida/recolhida, rota ativa, logout, busca se usada e drawer móvel. Execute tipo/build disponíveis e corrija erros.
8. Informe arquivos alterados, integrações realizadas, validações e dependências que o projeto precisa fornecer.

### Fora de Vue

Adapte a mecânica do framework, mas use as regras, valores e organização literal documentados abaixo. Preserve hierarquia, ordem, dimensões, cores, gradientes, sombras, espaçamentos, tipografia, ícones, estados, animações, responsividade e interações. Não crie uma tela apenas “inspirada” no padrão. Caso uma biblioteca equivalente seja necessária, mantenha peso visual e tamanho dos ícones Lucide e informe essa dependência.

## Regras obrigatórias

### Identidade e logo

- Logo oficial do setor Automação DASS é obrigatório no cabeçalho do Login e no tile superior da Sidebar.
- `assets/brand-symbol-white.png` é o arquivo/máscara usado no CSS original. `assets/logo-automacao.png` é a variante RGBA com transparência extraída da mesma marca. Preservar resolução, proporções, transparência e cores. Não recriar, recolorir, esticar ou trocar por marca/ícone do produto.
- O nome da aplicação e subtítulo podem variar. Preserve sua posição e estilos; não deixe ERP Modelagem como marca textual em outro produto.

### Login

Preserve plano pontilhado, centralização, card, largura, logo, hierarquia da marca, título e descrição, campos, alertas, botão, gradiente, espaçamentos, tipografia, rodapé, breakpoints e estados. Personalize nome, subtítulo e textos explicitamente configuráveis. Conecte autenticação ao app mantendo carregamento e erros no mesmo padrão visual.

### Sidebar

Preserve largura, altura, background, cabeçalho/logo, botão recolher, estilos, espaçamentos, categorias, links, estados ativos/hover, transições, perfil e Sair no rodapé, drawer móvel e comportamento responsivo. Personalize nome, menus, rotas, grupos, ícones, permissões, usuário e ações específicas sem alterar a identidade visual.

A busca e ação principal são opcionais conforme o produto. Se a busca existir, mantenha local, tamanho, tema escuro e interação originais. Se for removida, não redesenhe os outros itens. O perfil do usuário e Sair permanecem no rodapé.

## Design System de referência

# Design System — setor de Automação

Fonte de verdade para as propriedades extraídas dos SFCs atuais. Este arquivo descreve o sistema existente; não substitui os componentes-fonte nem cria um design alternativo.

## Classificação

- **FIXA:** valor/estrutura que deve ser preservado ao replicar o design.
- **PERSONALIZÁVEL:** dado ou conteúdo que pode mudar para integrar outra aplicação sem redesenhar os componentes.

## Logo e marca

| Propriedade | Classificação | Regra |
| --- | --- | --- |
| Símbolo Automação DASS | FIXA | Usar o arquivo oficial `../assets/brand-symbol-white.png`; não redesenhar, recolorir ou trocar por ícone |
| Representação | FIXA | Login e sidebar usam máscara branca; o retângulo do asset de máscara não deve aparecer |
| Arquivo RGBA alternativo | FIXA | `assets/logo-automacao.png` mantém a variante com transparência extraída de `docs/LogoAutomacao.png` |
| Posição | FIXA | Login: logo à esquerda do lockup; sidebar: centralizado no tile azul |
| Nome/título da aplicação | PERSONALIZÁVEL | Substituir “ERP Modelagem” na marca textual pelo nome do produto |
| Subtítulo | PERSONALIZÁVEL | Texto do produto pode mudar, mantendo a linha e hierarquia tipográfica |

## Paleta observada

| Nome/uso | Classificação | Valor original |
| --- | --- | --- |
| Fundo de login | FIXA | `#f8fafc` |
| Pontos do fundo de login | FIXA | `#cbd5e1` a 45% de opacidade |
| Cartão de login | FIXA | `#ffffff` |
| Texto primário de login | FIXA | `#0f172a` |
| Texto secundário | FIXA | `#64748b` |
| Rótulo de campo | FIXA | `#374151` |
| Ícone/placeholder | FIXA | `#94a3b8` |
| Campo de login | FIXA | fundo `#f8fafc`; borda `#e2e8f0` |
| Foco e CTA login | FIXA | `#1e40af` |
| Erro | FIXA | fundo `#fef2f2`; borda `#fecaca`; texto `#b91c1c` |
| Fundo sidebar | FIXA | `#0d162d` |
| Superfície secundária sidebar | FIXA | `#111c30` |
| Texto primário sidebar | FIXA | `#e2e8f0` |
| Texto inativo/ícone | FIXA | `#94a3b8` |
| Título de categoria | FIXA | `#71829e` |
| Índigo principal | FIXA | `#4d46e0` |
| Índigo claro do tile | FIXA | `#6962ef` |
| CTA hover | FIXA | `#5b54eb` |
| CTA ativo | FIXA | `#3933b9` |
| Item ativo | FIXA | texto `#e0e7ff`; fundo `rgba(77,70,224,.22)`; borda `rgba(129,124,255,.14)` |
| Item hover | FIXA | texto `#e2e8f0`; fundo `rgba(255,255,255,.055)` |
| Divisores sidebar | FIXA | `rgba(148,163,184,.14)`; grupos usam `.1` |
| Área geral | FIXA | `#f1f5f9`; dashboard gerencial `#f8fafc` |

Os literais hexadecimais encontrados nos dois SFCs são: `#000000`, `#0d162d`, `#0f172a`, `#111c30`, `#1e3a8a`, `#1e40af`, `#334155`, `#374151`, `#3933b9`, `#4d46e0`, `#5b54eb`, `#5f58eb`, `#64748b`, `#6962ef`, `#71829e`, `#817cff`, `#8293ad`, `#8b9ab5`, `#8ea0bb`, `#91a1ba`, `#94a3b8`, `#9fb0c9`, `#aaa6ff`, `#b91c1c`, `#b9c5d7`, `#cbd5e1`, `#dbe4f0`, `#e0e7ff`, `#e2e8f0`, `#eff6ff`, `#f1f5f9`, `#f8fafc`, `#fecaca`, `#fef2f2`, `#fff` e `#ffffff`. `#000000` aparece em regras-base do SFC da sidebar; os seletores finais `.sidebar ...` sobrescrevem as cores dos componentes que formam o tema escuro.

Os literais RGBA adicionais encontrados são: `rgba(0,0,0,.05)`, `rgba(0,0,0,.08)`, `rgba(127,29,29,.18)`, `rgba(129,124,255,.14)`, `rgba(129,124,255,.35)`, `rgba(129,124,255,.58)`, `rgba(148,163,184,.1)`, `rgba(148,163,184,.12)`, `rgba(148,163,184,.13)`, `rgba(148,163,184,.14)`, `rgba(148,163,184,.16)`, `rgba(148,163,184,.18)`, `rgba(148,163,184,.2)`, `rgba(148,163,184,.28)`, `rgba(148,163,184,.32)`, `rgba(15,23,42,.035)`, `rgba(162,158,255,.28)`, `rgba(2,6,23,.34)`, `rgba(2,6,23,.35)`, `rgba(2,6,23,.38)`, `rgba(2,6,23,.42)`, `rgba(2,6,23,.56)`, `rgba(2,6,23,.58)`, `rgba(226,232,240,.8)`, `rgba(248,113,113,.23)`, `rgba(255,255,255,.045)`, `rgba(255,255,255,.055)`, `rgba(255,255,255,.08)`, `rgba(255,255,255,.1)`, `rgba(255,255,255,.7)`, `rgba(255,255,255,.96)`, `rgba(30,64,175,.12)`, `rgba(30,64,175,.3)`, `rgba(30,64,175,.35)`, `rgba(59,130,246,.1)`, `rgba(77,70,224,.06)`, `rgba(77,70,224,.08)`, `rgba(77,70,224,.11)`, `rgba(77,70,224,.12)`, `rgba(77,70,224,.2)`, `rgba(77,70,224,.22)`, `rgba(77,70,224,.25)`, `rgba(77,70,224,.3)` e `rgba(77,70,224,.5)`. Os SFCs permanecem a fonte literal para preservar espaçamento e cascade originais.

## Tipografia

`src/index.css` importa Geist, Nunito e Inter com pesos 300–900. Não existe declaração de `font-family` em `:root` ou `body` nesse arquivo. Os controles do login usam `inherit`; o documento Tailwind não estende `fontFamily`. Assim, fontes efetivamente renderizadas dependem da pilha herdada do navegador/shell.

| Elemento | Classificação | Valor |
| --- | --- | --- |
| Nome da marca no login | FIXA em estilo; texto PERSONALIZÁVEL | `1.1rem`, peso 700, line-height 1.2, tracking `-.025em` |
| Subtítulo da marca | FIXA em estilo; texto PERSONALIZÁVEL | `.625rem`, peso 600, tracking `.06em`, uppercase |
| Título de login | FIXA | `1.1rem`, peso 700, tracking `-.03em` |
| Descrição de login | FIXA em estilo | `.8rem`, line-height 1.5 |
| Rótulos login | FIXA | `.7rem`, peso 700, tracking `.05em`, uppercase |
| Campo login | FIXA | `.875rem`, peso 500 |
| Botão login | FIXA | `.875rem`, peso 700, tracking `.01em` |
| Título marca sidebar | FIXA em estilo; texto PERSONALIZÁVEL | `.94rem`, peso 800, tracking `-.02em`, line-height 1.15 |
| Subtítulo sidebar | FIXA em estilo; texto PERSONALIZÁVEL | `.65rem`, peso 600, tracking `.075em`, uppercase |
| Título de categoria | FIXA | `.62rem`, peso 800, tracking `.11em`, uppercase |
| Item de menu | FIXA | `.84rem`, peso 550 |

## Dimensões e espaçamento

| Elemento | Classificação | Base |
| --- | --- | --- |
| Login: largura máxima do grupo | FIXA | `24rem`, com breakpoints registrados no `seção Referência de Login desta Skill` |
| Login: cartão | FIXA | `94%` do grupo, raio `1.25rem` |
| Login: interior | FIXA | padding `1.5rem`, gap `1.25rem` |
| Login: tile logo | FIXA | `2.5rem`; símbolo `1.65rem` |
| Login: inputs | FIXA | padding `.65rem .75rem .65rem 2.5rem`; sem altura explícita |
| Login: botão | FIXA | padding `.75rem 1.25rem`; largura total |
| Sidebar: largura | FIXA | `17.5rem` expandida, `4.5rem` recolhida (há ajustes 1920/2560px) |
| Sidebar: tile logo | FIXA | `2rem`; recolhida `1.8rem`; símbolo `1.4rem` |
| Sidebar: cabeçalho | FIXA | mínimo `4.75rem`; padding `.75rem .8rem .75rem 1rem` |
| Sidebar: item | FIXA | mínimo `2.8rem`; padding `.62rem .75rem`; raio `.62rem` |
| Sidebar: ícone | FIXA | `19px`; ícones toggle `18px` |
| Sidebar: avatar | FIXA | círculo `2rem`; chip mínimo `3.35rem` |

## Bordas, sombras e gradientes

| Elemento | Classificação | Valor |
| --- | --- | --- |
| Tile login | FIXA | gradiente `135deg, #0f172a 0%, #1e40af 100%`; raio `.75rem`; sombra `0 4px 16px rgba(30,64,175,.3)` |
| Tile sidebar | FIXA | gradiente `135deg, #6962ef, #4d46e0`; raio `.55rem`; sombra `0 3px 12px rgba(77,70,224,.3)` |
| Botão login | FIXA | `linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #1e40af 100%)` |
| Botão CTA sidebar | FIXA | fundo `#4d46e0`; hover `#5b54eb`; ativo `#3933b9` |
| Cartão login | FIXA | 3 camadas: `0 1px 3px rgba(0,0,0,.05)`, `0 8px 32px rgba(0,0,0,.08)`, inset branco `0 0 0 1px rgba(255,255,255,.7)` |
| Campo login | FIXA | raio `.625rem`; foco: borda `#1e40af`, halo `0 0 0 3px rgba(30,64,175,.12)` |
| Item ativo | FIXA | borda `rgba(129,124,255,.14)`; indicador lateral `3px`, `#817cff` |

## Estados, ícones e animações

- **FIXA:** ícones de login e navegação vêm de `@lucide/vue`; manter dimensões por contexto: login `16px` em campos, `18px` em ação/loader; sidebar `19px`, busca `17px`, toggle `18px`.
- **FIXA:** campo em foco muda fundo a branco e ativa halo azul; disabled reduz opacidade.
- **FIXA:** botão login tem hover com `translateY(-1px)`, sombra azul e opacity `.92`; active usa `scale(.98)`.
- **FIXA:** spinner login: `.8s linear infinite`; transição do alerta `.2s`; ícone do campo muda cor em `.15s`.
- **FIXA:** sidebar anima largura em `.24s cubic-bezier(.32,.72,0,1)`; rótulos usam `fade-slide` `.15s` com deslocamento X `-6px`.
- **FIXA:** suporta `prefers-reduced-motion: reduce` reduzindo transições para `.01ms`.
- **PERSONALIZÁVEL:** associação de ícones aos links, sem trocar a biblioteca sem revisar dimensões e peso visual.

## Layout responsivo e navegação

- Login breakpoints: 1280, 1536, 1920 e 2560px; valores exatos no `seção Referência de Login desta Skill`.
- Sidebar: drawer em `max-width: 767px`, largura `min(20rem,86vw)`, backdrop, topbar branca, Escape e bloqueio/restauração do scroll do body.
- Desktop: expandida por padrão; pode recolher. Em 1920px e 2560px, largura cresce conforme especificado.
- **PERSONALIZÁVEL:** nome da aplicação, labels de menu, rotas, grupos e permissões.
- **FIXA:** item ativo, busca opcional, avatar/perfil e botão Sair mantêm hierarquia, estados e posição.
- Busca é funcional no código original. Se não fizer sentido numa aplicação de destino, sua ausência é uma escolha de produto; se mantida, preservar o tema escuro, localização e interação do componente.

## Dependências e implementação

Ver `seção Dependências e desacoplamento desta Skill`. As fontes dos componentes ficam em `src/views/LoginView.vue no bloco de código completo desta Skill` e `src/views/DashboardView.vue no bloco de código completo desta Skill`; os blocos scoped de estilo estão incluídos nessas fontes sem alteração.


## Referência de Login

# Login — referência extraída

Este documento registra a tela existente no ERP Modelagem, sem propor uma alternativa. O arquivo completo — estrutura, interação e todos os estilos scoped — está em `LoginView.vue`.

## Código original e contexto

- Fonte extraída: `erp-modelagem/frontend/src/views/LoginView.vue`.
- Componente copiado integralmente: `LoginView.vue` (519 linhas no momento da extração).
- Logo/máscara usada pelo componente: `brand-symbol-white.png`, referenciada pelo CSS original como `../assets/brand-symbol-white.png`.
- Estilos globais disponíveis: `index.css`.
- Inicialização Vue e roteador não são incluídos; os contratos de integração estão em `seção Dependências e desacoplamento desta Skill`.
- Dependências e contratos não incluídos: `seção Dependências e desacoplamento desta Skill`.

O SFC preserva literalmente o `<script setup lang="ts">`, template e `<style scoped>`. Não há CSS separado para esta tela no projeto original.

## Estrutura funcional

Ordem dos elementos: plano de fundo pontilhado; cartão; marca horizontal com logo, nome e subtítulo; título e descrição do acesso; alerta condicional; campos de usuário e senha com ícones; botão Entrar; rodapé institucional.

O formulário usa `@submit.prevent`, `novalidate` e valida usuário/senha vazios após `trim()`. Durante a chamada, desabilita os controles, informa `aria-busy` e mostra spinner. Envia `POST /auth/login`; em sucesso, espera `data.token`, grava sessão por `authStore.login` quando `data.usuario` existe e navega para a rota nomeada `dashboard`. Mensagens tratam status 401, 429, 5xx e falhas restantes.

## Medidas e estilo extraídos

| Propriedade | Valor no código |
| --- | --- |
| Área da tela | `min-height: 100dvh`; conteúdo centralizado em ambos os eixos |
| Padding da tela | `1.5rem` |
| Fundo | `#f8fafc` |
| Grade | `radial-gradient(circle, #cbd5e1 1px, transparent 1px)`, repetição `24px`, opacidade `0.45` |
| Largura base do grupo | `100%`, `max-width: 24rem` |
| Cartão | largura `94%`; branco; borda `1px solid rgba(226, 232, 240, 0.8)`; raio `1.25rem` |
| Sombra do cartão | `0 1px 3px rgba(0,0,0,.05)`, `0 8px 32px rgba(0,0,0,.08)`, `0 0 0 1px rgba(255,255,255,.7) inset` |
| Interior do cartão | padding `1.5rem`; gap `1.25rem` |
| Marca base | quadrado `2.5rem`; raio `.75rem`; `linear-gradient(135deg, #0f172a 0%, #1e40af 100%)`; sombra `0 4px 16px rgba(30,64,175,.3)` |
| Logo/máscara base | `1.65rem × 1.65rem`; branco; máscara central `235% auto` |
| Cabeçalho da marca | linha horizontal; gap `.5rem`; logo à esquerda e textos alinhados à esquerda |
| Nome | `1.1rem`, peso 700, `#0f172a`, tracking `-0.025em`, line-height `1.2` |
| Subtítulo | `.625rem`, peso 600, `#64748b`, tracking `.06em`, uppercase |
| Título de acesso | `1.1rem`, peso 700, `#0f172a`, tracking `-0.03em` |
| Descrição | `.8rem`, `#64748b`, line-height `1.5` |
| Rótulos | `.7rem`, peso 700, `#374151`, tracking `.05em`, uppercase |
| Campo | largura total; padding `.65rem .75rem .65rem 2.5rem`; `.875rem`; fundo `#f8fafc`; borda `1.5px solid #e2e8f0`; raio `.625rem` |
| Ícone do campo | `16px`, posição absoluta à esquerda `.875rem`, `#94a3b8`; foco `#1e40af` |
| Botão | largura total; padding `.75rem 1.25rem`; `.875rem`, peso 700; raio `.625rem`; gradiente `#0f172a → #1e3a8a → #1e40af` |
| Ícone do botão/spinner | `18px`; spinner gira em `.8s linear infinite` |
| Rodapé | `.625rem`, peso 600, `#94a3b8`, tracking `.05em` |

### Breakpoints definidos no SFC

| Breakpoint | Mudanças reais |
| --- | --- |
| Base | grupo `24rem`; logo `2.5rem`; símbolo `1.65rem`; interior do cartão `1.5rem` |
| `min-width: 1280px` | grupo `29rem` |
| `min-width: 1536px` | grupo `34rem`; logo/símbolo `3.4rem`/`2.2rem`; nome `1.5rem`; subtítulo `.7rem`; interior `2.25rem`; gap `1.6rem`; campo `1rem` com padding ampliado; botão `1rem` |
| `min-width: 1920px` | grupo `41rem`; gap do layout `2rem` |
| `min-width: 2560px` | grupo `52rem`; logo/símbolo `4.6rem`/`3rem`; interior `3rem`; tipografia e padding de campos/botão ampliados; footer `.875rem` |

Não existe breakpoint móvel específico no LoginView; o estilo base atende telas menores e o formulário pode crescer verticalmente.

## Tipografia

Os controles declaram `font-family: inherit`. `index.css` importa Geist, Nunito e Inter do Google Fonts, mas não define um `font-family` global nem escolhe explicitamente uma dessas famílias. A renderização final herda a pilha de fontes do documento/Tailwind. Para reprodução fiel, incluir o `index.css` extraído e conferir a fonte herdada no shell de destino.

## FIXO e personalizável

**Fixo:** estrutura e ordem; logo Automação; dimensões, cores, máscara, gradientes, estados dos campos e botão, alertas, acessibilidade, breakpoints e rodapé institucional.

**Personalizável:** nome da aplicação, subtítulo, textos de instrução/placeholders se necessário, endpoint/contrato de autenticação e navegação de sucesso. A integração deve ser trocada sem alterar a estrutura ou as regras visuais do SFC.

## Elementos obrigatórios

Logo Automação, nome da aplicação, subtítulo, título de acesso, usuário, senha, botão Entrar e rodapé institucional.

## Segredos

O arquivo extraído contém somente placeholders de formulário (por exemplo `JOAO.SILVA`) e código genérico. Nenhuma senha, token, cookie ou credencial real foi copiada. A integração original de API/sessão foi deliberadamente excluída do pacote; veja `seção Dependências e desacoplamento desta Skill`.


## Referência de Sidebar

# Sidebar — referência extraída

Este documento acompanha o componente original `DashboardView.vue`, copiado integralmente (template, lógica e estilos scoped). O componente também compõe a área de conteúdo via `RouterView`; a extração mantém isso como no ERP.

## Código original e contexto

- Fonte: `erp-modelagem/frontend/src/views/DashboardView.vue`.
- SFC completo copiado: `DashboardView.vue` (1252 linhas no momento da extração).
- Máscara do logo: `brand-symbol-white.png`.
- Estilos globais disponíveis: `index.css`. Inicialização e roteador ficam a cargo do projeto destino.
- Dependências e contratos da sessão: `seção Dependências e desacoplamento desta Skill`.

## Estrutura visual

Coluna lateral sticky à esquerda com fundo escuro. De cima para baixo: marca e botão recolher; ação principal condicional; busca; categorias e itens; rodapé com usuário e Sair. O conteúdo selecionado é renderizado no `RouterView` à direita.

## Medidas e cores exatas do CSS

| Propriedade | Valor extraído |
| --- | --- |
| Altura | `100dvh` |
| Largura desktop base | expandida `17.5rem`; recolhida `4.5rem` |
| `min-width: 1920px` | expandida `18.5rem`; recolhida `5rem` |
| `min-width: 2560px` | expandida `21rem`; recolhida `5.25rem` |
| Breakpoint mobile | `max-width: 767px` |
| Largura drawer | `min(20rem, 86vw)` |
| Fundo | `#0d162d` |
| Superfície secundária | `#111c30` |
| Texto principal | `#e2e8f0` |
| Texto inativo | `#94a3b8` |
| Título das seções | `#71829e` |
| Índigo | `#4d46e0` |
| Logo tile | `linear-gradient(135deg, #6962ef, #4d46e0)`; tile `2rem × 2rem`, raio `.55rem`, sombra `0 3px 12px rgba(77,70,224,.3)` |
| Símbolo no tile | `1.4rem × 1.4rem`, máscara `brand-symbol-white.png`, escala `235% auto` |
| Raio da sidebar | `0 1rem 1rem 0` |
| Cabeçalho | mínimo `4.75rem`; padding `.75rem .8rem .75rem 1rem`; linha inferior |
| Cabeçalho recolhido | mínimo `6rem`; logo `1.8rem`; toggle `1.8rem × 1.65rem` |
| Chevron toggle | `18px`; toggle expandido `2rem × 2rem` |
| CTA | mínimo `2.8rem`; raio `.65rem`; fundo `#4d46e0`; hover `#5b54eb`; ativo `#3933b9`; texto branco |
| Pesquisa | controle `2.65rem` alto; raio `.65rem`; fundo escuro `rgba(2,6,23,.42)`; foco `.58` alpha; texto `#e2e8f0`; placeholder `#71829e` |
| Busca compacta | botão `2.8rem × 2.6rem`; popover `18rem`; superfície `#111c30` |
| Área de navegação | gap `.45rem`; padding `.55rem .55rem .75rem`; rolagem vertical |
| Título de categoria | `.62rem`, peso 800, tracking `.11em`, uppercase; `#71829e` |
| Separador de grupo | borda `rgba(148,163,184,.1)`; margem superior `.35rem`; padding superior `.55rem` |
| Item | mínimo `2.8rem`; ícone `19px`; gap `.75rem`; padding `.62rem .75rem`; raio `.62rem`; fonte `.84rem` |
| Item hover | texto `#e2e8f0`; fundo `rgba(255,255,255,.055)` |
| Item ativo | texto `#e0e7ff`; fundo `rgba(77,70,224,.22)`; borda `rgba(129,124,255,.14)`; indicador `#817cff` |
| Rodapé | flex fixo inferior; padding `.7rem .6rem .65rem`; borda superior |
| Chip usuário | mínimo `3.35rem`; avatar `2rem`; superfície `rgba(255,255,255,.045)` |
| Botão Sair | mínimo `2.65rem`; fonte `.8rem`; raio `.62rem`; hover vermelho translúcido |
| Área principal | padding `1.75rem`; `2.5rem` a partir de 1920px; `3rem` a partir de 2560px |

O CSS completo — incluindo regras auxiliares e cores de foco — permanece no final do arquivo SFC copiado. A versão mobile recolhe o conteúdo principal em drawer, apresenta topbar clara e backdrop `rgba(2,6,23,.56)`.

## Grupos e comportamento

Os grupos atuais são `Acesso rápido`, `Modelagem`, `Produção` e `Administração`. Os itens são definidos em `navItems` com `to`, `label`, componente de ícone e permissão. A visibilidade respeita `authStore.hasPermission`; RBAC também permite a exceção `isAdminAutomacao`. A busca opcional remove acentos e ignora caixa, filtra rótulos e grupos vazios, mostra “Nenhuma tela encontrada” e limpa ao navegar. No modo recolhido, abre popover e foca o input.

A rota ativa usa igualdade ou prefixo de caminho, adiciona `aria-current="page"` e chevron. `RouterLink` executa a navegação. `RouterView` apresenta a página correspondente.

O rodapé mostra inicial, nome e perfil do usuário, seguido de Sair. O logout chama o store e navega à rota `login`.

## Transições e responsividade

- Largura da sidebar: `.24s cubic-bezier(.32,.72,0,1)`; transform e sombra também têm transições.
- Rótulos e marca: transição `fade-slide` com opacity/transform em `.15s` e deslocamento `-6px`.
- Mobile: drawer fixo até `767px`, `min(20rem,86vw)`, fecha por botão, backdrop, navegação ou Escape. O body perde scroll enquanto aberto; elementos fechados recebem `inert`/`aria-hidden`.
- Preferência de movimento reduzido: transições para `.01ms`; rolagem suave removida.
- Breakpoints de conteúdo: sidebar expande gradualmente em `1920px` e `2560px`; topbar aparece em mobile.

## Elementos fixos e configuráveis

**Fixo:** logo Automação, estrutura da coluna, cores, dimensões, estados, comportamentos de recolhimento/mobile, tema da busca, avatar/perfil no rodapé e saída.

**Personalizável:** nome do produto, `navItems`, ícones, rotas, permissões, nomes/itens dos grupos, dados do usuário, presença e conteúdo do CTA. A mudança de menu não deve alterar o CSS estrutural.

## Dependências de integração

`authStore` precisa fornecer `user`, `isAdminAutomacao`, `hasPermission()` e `logout()`. O `vue-router` precisa fornecer as rotas nomeadas e paths usados no array `navItems`. O conteúdo da área central é responsabilidade das rotas da aplicação de destino. Não copie credenciais nem a allowlist de contas administrativas do store original; veja `seção Dependências e desacoplamento desta Skill`.


## Dependências e desacoplamento

# Dependências e contratos de integração

Esta lista deriva de `erp-modelagem/frontend/package.json` e dos imports dos dois SFCs. O pacote da Skill inclui os dois SFCs e o CSS global relevante, sem copiar o manifest/lockfile do ERP.

## Bibliotecas diretas usadas pelos componentes

| Dependência | Versão declarada | Uso |
| --- | --- | --- |
| `vue` | `^3.5.39` | SFC, Composition API, `Transition`, refs e lifecycle |
| `vue-router` | `^4.6.4` | `useRouter`, `useRoute`, `RouterLink`, `RouterView`, navegação nomeada |
| `@lucide/vue` | `^1.24.0` | Ícones `LogIn`, `User`, `Lock`, `AlertCircle`, `Loader2`, sidebar, busca e navegação |
| `axios` | `^1.18.1` | Usado indiretamente via `src/api/axios.ts` na tela de login |

## Tooling e estilos globais

| Dependência | Versão declarada | Uso |
| --- | --- | --- |
| `vite` | `^8.1.1` | Dev server e build |
| `@vitejs/plugin-vue` | `^6.0.7` | Compilação de SFC |
| `typescript` | `~6.0.2` | Script setup tipado e config |
| `vue-tsc` | `^3.3.5` | Verificação Vue/TypeScript no build |
| `tailwindcss` | `^3.4.19` | Utilitários da aplicação envolvente |
| `postcss` | `^8.5.19` | Pipeline CSS |
| `autoprefixer` | `^10.5.3` | Prefixos de CSS |

O arquivo global incluído em `bloco de src/index.css incluído nesta Skill` carrega Geist, Nunito e Inter de `fonts.googleapis.com`; as famílias são importadas, mas estes SFCs não as selecionam explicitamente com `font-family`. O manifest, roteador, App e demais configuração do ERP não são incluídos: configure o projeto destino com as versões compatíveis listadas acima.

## Imports específicos da aplicação que não foram incluídos

Os componentes originais importam `../api/axios` e `../api/auth.store`. Esses módulos contêm a integração real de API, armazenamento/renovação de sessão, nomes de armazenamento e lógica de autorização da aplicação. O store tem uma allowlist de identificadores de conta. Para cumprir a regra de não copiar dado sensível, tais implementações **não** foram adicionadas ao pacote.

Interfaces exigidas pelo login:

- `api.post('/auth/login', { usuario, senha })` com retorno `{ data: { token, usuario } }`.
- `authStore.login(token, usuario)` para persistir a sessão.
- `router.push({ name: 'dashboard' })` para concluir o login.

Interfaces exigidas pela sidebar:

- `authStore.user.value` com `nomeCompleto`, `usuario`, `perfilNome` e permissões.
- `authStore.hasPermission(permission)`, `authStore.isAdminAutomacao.value` e `authStore.logout()`.
- Vue Router configurado com os nomes/paths consumidos por `navItems`; as views das rotas pertencem ao produto destino.

Configure o router no projeto destino com as rotas locais de login, dashboard e páginas do produto. Nenhum router do ERP é incluído na Skill.

## Como desacoplar sem redesenhar

Preservar os SFCs e substituir somente a camada de integração externa: adaptar o caminho/cliente API do login, implementar a interface de sessão acima, mapear permissões e ligar cada `navItems.to` a rotas existentes. Não copiar allowlists de usuários ou estado de sessão do ERP. O código visual, os estilos scoped e o comportamento local de formulário/sidebar permanecem no componente original.

## Itens que não são dependências inclusas

- Backend `/auth/login`, `/auth/me`, `/auth/logout` e refresh de token.
- Dados de usuário, permissões e menus reais.
- Views de dashboard referenciadas no router e componentes de negócio das rotas.
- Serviço de identidade/Portal Unix ou configuração de ambiente.
- Fontes baixadas localmente: as fontes atuais dependem do Google Fonts em runtime; sem rede, o navegador usa fallback.

Nenhuma senha, token, cookie, valor de `.env` ou credencial real foi copiada. O projeto de referência guarda dados de autenticação fora deste pacote.


## Exemplo de integração Vue 3

# Exemplo de integração Vue 3

Este exemplo mostra onde ligar os SFCs originais; não substitui os componentes nem define a autenticação de um produto.

## Arquivos de destino

Em uma aplicação Vue típica, os SFCs ficam em `src/views/LoginView.vue` e `src/views/DashboardView.vue`; a máscara oficial fica em `src/assets/brand-symbol-white.png`; os adaptadores do produto podem ficar em `src/api/axios.ts` e `src/api/auth.store.ts`. Copie os SFCs completos dos blocos nomeados abaixo, preservando `<template>` e `<style scoped>`. Colocar a máscara em `src/assets/` mantém válido o caminho CSS original `../assets/brand-symbol-white.png`.

## Personalização da marca e navegação

No LoginView, troque somente os textos da marca (nome e subtítulo) pelos dados do produto, mantendo classes e elementos. No DashboardView, configure os grupos e os itens de navegação para as rotas reais, escolhendo ícones da `@lucide/vue`. Preserve classes, estrutura e handlers visuais existentes.

## Contratos que cada aplicação fornece

O login original espera um cliente com `post(path, body)`, cujo retorno disponibilize `data.token` e, opcionalmente, `data.usuario`. A aplicação decide como autenticar, persistir a sessão e para qual rota navegar. No `src/views/LoginView.vue`, ligue o envio do formulário ao endpoint, à sessão e à rota reais do destino; não implemente backend fictício nem mantenha `/auth/login` do ERP por padrão.

A sidebar consulta `authStore.user.value`, `authStore.isAdminAutomacao.value`, `authStore.hasPermission(permission)` e `authStore.logout()`. Adapte esses pontos à sessão do produto e remova condições de permissão que não existam no destino sem remover os estados visuais dos itens. Configure `vue-router` com as rotas do produto. O conteúdo à direita é renderizado pelo `RouterView` original.

## Dependências Vue

Os SFCs usam Vue 3, Vue Router 4 e `@lucide/vue`. Login usa também o cliente Axios da aplicação. Consulte `seção Dependências e desacoplamento desta Skill` para as versões identificadas e dependências externas.


## Arquivos completos para o projeto de destino

Os blocos seguintes são os SFCs originais, integralmente copiados. Seus estilos estão nos blocos `<style scoped>` dentro de cada arquivo. Os únicos ajustes permitidos são integrações e conteúdos declarados personalizáveis nesta Skill.

### Destination file: `src/views/LoginView.vue`

```vue
<script setup lang="ts">
import { ref, reactive } from 'vue'
import { useRouter } from 'vue-router'
import { LogIn, User, Lock, AlertCircle, Loader2 } from '@lucide/vue'
import api from '../api/axios'
import { authStore } from '../api/auth.store'

const router = useRouter()

const form = reactive({ usuario: '', senha: '' })
const loading = ref(false)
const errorMsg = ref('')

async function handleLogin() {
  if (!form.usuario.trim() || !form.senha.trim()) {
    errorMsg.value = 'Preencha o usuario e a senha para continuar.'
    return
  }

  loading.value = true
  errorMsg.value = ''

  try {
    const { data } = await api.post('/auth/login', {
      usuario: form.usuario,
      senha: form.senha,
    })

    const token = data.token
    if (!token) throw new Error('Token nao retornado pelo servidor.')

    if (data.usuario) {
      authStore.login(token, data.usuario)
    }

    router.push({ name: 'dashboard' })
  } catch (err: any) {
    const status = err?.response?.status
    if (status === 401) {
      errorMsg.value = 'Credenciais invalidas. Verifique seu usuario e senha.'
    } else if (status === 429) {
      errorMsg.value = 'Muitas tentativas de acesso. Aguarde alguns minutos.'
    } else if (status >= 500) {
      errorMsg.value = 'Servico indisponivel. Tente novamente mais tarde.'
    } else {
      errorMsg.value = 'Nao foi possivel conectar ao servidor de autenticacao.'
    }
  } finally {
    loading.value = false
  }
}
</script>

<template>
  <div class="login-root">
    <!-- Subtle dot-grid background -->
    <div class="bg-grid" aria-hidden="true"></div>

    <main class="login-main">
      <!-- Card -->
      <div class="login-card" role="main">
        <div class="card-inner">
          <header class="brand-header">
            <div class="brand-logo" aria-hidden="true">
              <div class="logo-mark"></div>
            </div>
            <div class="brand-text">
              <h1 class="brand-name">ERP Modelagem</h1>
              <p class="brand-subtitle">Sistema de Rastreamento de Producao</p>
            </div>
          </header>

          <div class="card-heading">
            <h2 class="card-title">Acesso ao Sistema</h2>
            <p class="card-desc">Insira suas credenciais do PORTAL UNIX</p>
          </div>

          <!-- Error -->
          <Transition name="error-fade">
            <div v-if="errorMsg" class="error-banner" role="alert" aria-live="assertive">
              <AlertCircle :size="18" class="error-icon" aria-hidden="true" />
              <span class="error-text">{{ errorMsg }}</span>
            </div>
          </Transition>

          <!-- Form -->
          <form @submit.prevent="handleLogin" class="login-form" novalidate>
            <div class="field-group">
              <label for="usuario" class="field-label">Usuario</label>
              <div class="input-wrapper">
                <User :size="16" class="input-icon" aria-hidden="true" />
                <input
                  id="usuario"
                  v-model="form.usuario"
                  type="text"
                  autocomplete="username"
                  spellcheck="false"
                  autocapitalize="off"
                  placeholder="Ex: JOAO.SILVA"
                  class="field-input"
                  :disabled="loading"
                  required
                />
              </div>
            </div>

            <div class="field-group">
              <label for="senha" class="field-label">Senha</label>
              <div class="input-wrapper">
                <Lock :size="16" class="input-icon" aria-hidden="true" />
                <input
                  id="senha"
                  v-model="form.senha"
                  type="password"
                  autocomplete="current-password"
                  placeholder="Sua senha de rede"
                  class="field-input"
                  :disabled="loading"
                  required
                />
              </div>
            </div>

            <button
              type="submit"
              class="btn-submit"
              :disabled="loading"
              :aria-busy="loading"
            >
              <Loader2 v-if="loading" :size="18" class="btn-spinner" aria-hidden="true" />
              <LogIn v-else :size="18" aria-hidden="true" />
              <span>{{ loading ? 'Autenticando...' : 'Entrar' }}</span>
            </button>
          </form>
        </div>
      </div>

      <!-- Footer -->
      <footer class="login-footer">
        <span>© 2026 Grupo DASS • Desenvolvido por DASS SEST</span>
      </footer>
    </main>
  </div>
</template>

<style scoped>
/* ==============================
   ROOT & BACKGROUND
============================== */
.login-root {
  min-height: 100dvh;
  background-color: #f8fafc;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  position: relative;
  overflow: hidden;
}

.bg-grid {
  position: fixed;
  inset: 0;
  background-image: radial-gradient(circle, #cbd5e1 1px, transparent 1px);
  background-size: 24px 24px;
  opacity: 0.45;
  pointer-events: none;
  z-index: 0;
}

/* ==============================
   MAIN LAYOUT — scales from mobile to 4K TVs
============================== */
.login-main {
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 24rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

@media (min-width: 1280px) { .login-main { max-width: 29rem; } }
@media (min-width: 1536px) { .login-main { max-width: 34rem; } }
@media (min-width: 1920px) { .login-main { max-width: 41rem; gap: 2rem; } }
@media (min-width: 2560px) { .login-main { max-width: 52rem; gap: 2.5rem; } }

/* ==============================
   BRAND HEADER
============================== */
.brand-header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  text-align: left;
}

.brand-text {
  text-align: left;
}

.brand-logo {
  width: 2.5rem;
  height: 2.5rem;
  background: linear-gradient(135deg, #0f172a 0%, #1e40af 100%);
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 16px rgba(30, 64, 175, 0.3);
  flex-shrink: 0;
}

.logo-mark {
  width: 1.65rem;
  height: 1.65rem;
  background: #ffffff;
  -webkit-mask: url('../assets/brand-symbol-white.png') center / 235% auto no-repeat;
  mask: url('../assets/brand-symbol-white.png') center / 235% auto no-repeat;
  mask-mode: luminance;
}

.brand-name {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0f172a;
  letter-spacing: -0.025em;
  line-height: 1.2;
  margin: 0;
}

.brand-subtitle {
  font-size: 0.625rem;
  font-weight: 600;
  color: #64748b;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin: 0.125rem 0 0;
}

@media (min-width: 1536px) {
  .brand-logo { width: 3.4rem; height: 3.4rem; border-radius: 0.9rem; }
  .logo-mark { width: 2.2rem; height: 2.2rem; }
  .brand-name { font-size: 1.5rem; }
  .brand-subtitle { font-size: 0.7rem; }
}
@media (min-width: 2560px) {
  .brand-logo { width: 4.6rem; height: 4.6rem; border-radius: 1rem; }
  .logo-mark { width: 3rem; height: 3rem; }
  .brand-name { font-size: 2.1rem; }
  .brand-subtitle { font-size: 0.95rem; }
}

/* ==============================
   LOGIN CARD
============================== */
.login-card {
  width: 94%;
  background: #ffffff;
  border: 1px solid rgba(226, 232, 240, 0.8);
  border-radius: 1.25rem;
  box-shadow:
    0 1px 3px rgba(0, 0, 0, 0.05),
    0 8px 32px rgba(0, 0, 0, 0.08),
    0 0 0 1px rgba(255, 255, 255, 0.7) inset;
}

.card-inner {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

@media (min-width: 1536px) { .card-inner { padding: 2.25rem; gap: 1.6rem; } }
@media (min-width: 2560px) { .card-inner { padding: 3rem; gap: 2rem; } }

/* ==============================
   CARD HEADING
============================== */
.card-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0f172a;
  letter-spacing: -0.03em;
  margin: 0 0 0.25rem;
}

.card-desc {
  font-size: 0.8rem;
  color: #64748b;
  margin: 0;
  line-height: 1.5;
}

@media (min-width: 1536px) { .card-title { font-size: 1.4rem; } .card-desc { font-size: 0.95rem; } }
@media (min-width: 2560px) { .card-title { font-size: 1.8rem; } .card-desc { font-size: 1.25rem; } }

/* ==============================
   ERROR BANNER
============================== */
.error-banner {
  display: flex;
  align-items: flex-start;
  gap: 0.625rem;
  padding: 0.875rem 1rem;
  background: #fef2f2;
  border: 1px solid #fecaca;
  border-radius: 0.75rem;
  color: #b91c1c;
}

.error-icon { flex-shrink: 0; margin-top: 1px; }

.error-text {
  font-size: 0.875rem;
  font-weight: 500;
  line-height: 1.45;
}

@media (min-width: 2560px) {
  .error-text { font-size: 1.25rem; }
}

.error-fade-enter-active,
.error-fade-leave-active { transition: opacity 0.2s ease, transform 0.2s ease; }
.error-fade-enter-from,
.error-fade-leave-to { opacity: 0; transform: translateY(-6px); }

/* ==============================
   FORM
============================== */
.login-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

/* ==============================
   FIELD
============================== */
.field-group {
  display: flex;
  flex-direction: column;
  gap: 0.375rem;
}

.field-label {
  font-size: 0.7rem;
  font-weight: 700;
  color: #374151;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

@media (min-width: 1536px) { .field-label { font-size: 0.85rem; } }
@media (min-width: 2560px) { .field-label { font-size: 1.1rem; } }

.input-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.input-icon {
  position: absolute;
  left: 0.875rem;
  color: #94a3b8;
  pointer-events: none;
  flex-shrink: 0;
  transition: color 0.15s ease;
}

.input-wrapper:focus-within .input-icon { color: #1e40af; }

.field-input {
  width: 100%;
  padding: 0.65rem 0.75rem 0.65rem 2.5rem;
  font-size: 0.875rem;
  font-family: inherit;
  font-weight: 500;
  color: #0f172a;
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 0.625rem;
  outline: none;
  -webkit-appearance: none;
  appearance: none;
  transition:
    border-color 0.15s ease,
    box-shadow 0.15s ease,
    background 0.15s ease;
}

.field-input::placeholder { color: #94a3b8; font-weight: 400; }

.field-input:focus {
  border-color: #1e40af;
  background: #ffffff;
  box-shadow: 0 0 0 3px rgba(30, 64, 175, 0.12);
}

.field-input:disabled {
  opacity: 0.55;
  cursor: not-allowed;
  background: #f1f5f9;
}

@media (min-width: 1536px) {
  .field-input {
    font-size: 1rem;
    padding: 0.85rem 1rem 0.85rem 3rem;
    border-radius: 0.7rem;
  }
  .input-icon { left: 1.125rem; }
}
@media (min-width: 2560px) {
  .field-input {
    font-size: 1.3rem;
    padding: 1.1rem 1.1rem 1.1rem 3.6rem;
    border-radius: 0.85rem;
  }
  .input-icon { left: 1.375rem; }
}

/* ==============================
   SUBMIT BUTTON
============================== */
.btn-submit {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.625rem;
  width: 100%;
  padding: 0.75rem 1.25rem;
  font-size: 0.875rem;
  font-weight: 700;
  font-family: inherit;
  letter-spacing: 0.01em;
  color: #ffffff;
  background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #1e40af 100%);
  border: none;
  border-radius: 0.625rem;
  cursor: pointer;
  margin-top: 0.5rem;
  will-change: transform;
  transition:
    opacity 0.15s ease,
    box-shadow 0.2s ease,
    transform 0.1s cubic-bezier(0.32, 0.72, 0, 1);
}

.btn-submit:hover:not(:disabled) {
  opacity: 0.92;
  box-shadow: 0 8px 24px rgba(30, 64, 175, 0.35);
  transform: translateY(-1px);
}

.btn-submit:active:not(:disabled) {
  transform: scale(0.98) translateY(0px);
  box-shadow: none;
}

.btn-submit:focus-visible {
  outline: 3px solid #1e40af;
  outline-offset: 2px;
}

.btn-submit:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.btn-spinner {
  animation: spin 0.8s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

@media (min-width: 1536px) {
  .btn-submit {
    font-size: 1rem;
    padding: 0.95rem 1.5rem;
    border-radius: 0.7rem;
  }
}
@media (min-width: 2560px) {
  .btn-submit {
    font-size: 1.3rem;
    padding: 1.2rem 2rem;
    border-radius: 0.85rem;
    gap: 0.65rem;
  }
}

/* ==============================
   FOOTER
============================== */
.login-footer {
  display: flex;
  align-items: center;
  gap: 0.625rem;
  font-size: 0.625rem;
  font-weight: 600;
  color: #94a3b8;
  letter-spacing: 0.05em;
  text-transform: none;
}

.footer-sep { color: #cbd5e1; }

@media (min-width: 2560px) {
  .login-footer { font-size: 0.875rem; gap: 0.8rem; }
}
</style>

```

### Destination file: `src/views/DashboardView.vue`

```vue
<script setup lang="ts">
import { computed, nextTick, onBeforeUnmount, onMounted, ref, watch } from 'vue'
import { useRouter, useRoute, RouterLink, RouterView } from 'vue-router'
import { authStore } from '../api/auth.store'
import {
  LayoutDashboard,
  ShieldCheck,
  LogOut,
  Menu,
  ChevronLeft,
  ChevronRight,
  ListOrdered,
  Barcode,
  ClipboardList,
  Layers,
  PlusCircle,
  MonitorPlay,
  Activity,
  Search,
  X
} from '@lucide/vue'

const router = useRouter()
const route = useRoute()
const user = computed(() => authStore.user.value)

const desktopSidebarExpanded = ref(true)
const mobileViewport = ref(false)
const mobileDrawerOpen = ref(false)
const searchQuery = ref('')
const compactSearchOpen = ref(false)
const compactSearchInput = ref<HTMLInputElement | null>(null)
const sidebarExpanded = computed(() => mobileViewport.value || desktopSidebarExpanded.value)
const userDisplayName = computed(() => user.value?.nomeCompleto || user.value?.usuario || 'Usuário')
const userInitial = computed(() => userDisplayName.value.trim().charAt(0).toLocaleUpperCase('pt-BR') || 'U')

const navItems = [
  { to: '/dashboard/gerencial', label: 'Torre de Controle', icon: LayoutDashboard, permission: 'TELA_TORRE_CONTROLE' },
  { to: '/dashboard/rastreamento', label: 'TV Rastreamento', icon: MonitorPlay, permission: 'TELA_RASTREAMENTO' },
  { to: '/dashboard/modelos', label: 'Catálogo de Modelos', icon: Layers, permission: 'TELA_CATALOGO_MODELOS' },
  { to: '/dashboard/catalogo-pecas', label: 'Catálogo de Peças', icon: Layers, permission: 'TELA_CATALOGO_PECAS' },
  { to: '/dashboard/rotas', label: 'Construtor de Rota', icon: ListOrdered, permission: 'TELA_CONSTRUTOR_ROTA' },
  { to: '/dashboard/ordens', label: 'Gestão de Ordens', icon: ClipboardList, permission: 'TELA_GESTAO_ORDENS' },
  { to: '/dashboard/bipagem', label: 'Bipagem Operacional', icon: Barcode, permission: 'TELA_BIPAGEM' },
  { to: '/dashboard/inspecao', label: 'Inspeção de Qualidade', icon: ShieldCheck, permission: 'TELA_INSPECAO_QUALIDADE' },
  { to: '/dashboard/rbac', label: 'Permissões RBAC', icon: ShieldCheck, permission: 'TELA_GESTAO_RBAC' },
  { to: '/dashboard/historico', label: 'Histórico de Movimentações', icon: Activity, permission: 'TELA_HISTORICO_MOVIMENTACOES' },
]

const navSections = [
  { id: 'overview', label: 'Acesso rápido', items: [navItems[0], navItems[1]] },
  { id: 'modelagem', label: 'Modelagem', items: [navItems[2], navItems[3], navItems[4]] },
  { id: 'producao', label: 'Produção', items: [navItems[5], navItems[6], navItems[7]] },
  { id: 'administracao', label: 'Administração', items: [navItems[8], navItems[9]] },
]

const visibleNavSections = computed(() => {
  const query = normalizeSearchText(searchQuery.value.trim())

  return navSections
    .map(section => ({
      ...section,
      items: section.items.filter(item => {
        const allowed = item.to === '/dashboard/rbac'
          ? authStore.isAdminAutomacao.value || authStore.hasPermission(item.permission)
          : authStore.hasPermission(item.permission)

        return allowed && (!query || normalizeSearchText(item.label).includes(query))
      }),
    }))
    .filter(section => section.items.length > 0)
})

const hasNavigationMatches = computed(() => visibleNavSections.value.length > 0)

function normalizeSearchText(value: string): string {
  return value
    .normalize('NFD')
    .replace(/[\u0300-\u036f]/g, '')
    .toLocaleLowerCase('pt-BR')
}

function isNavItemActive(path: string): boolean {
  return route.path === path || route.path.startsWith(path + '/')
}

function logout() {
  authStore.logout()
  router.push({ name: 'login' })
}

function toggleSidebar() {
  if (mobileViewport.value) {
    mobileDrawerOpen.value = false
    return
  }

  desktopSidebarExpanded.value = !desktopSidebarExpanded.value
  compactSearchOpen.value = false
}

async function toggleCompactSearch() {
  compactSearchOpen.value = !compactSearchOpen.value
  if (compactSearchOpen.value) {
    await nextTick()
    compactSearchInput.value?.focus()
  }
}

function clearSearch() {
  searchQuery.value = ''
}

function closeMobileDrawer() {
  mobileDrawerOpen.value = false
}

function handleNavigation() {
  searchQuery.value = ''
  compactSearchOpen.value = false
  closeMobileDrawer()
}

function handleMediaChange() {
  const isMobile = mobileQuery?.matches ?? false
  mobileViewport.value = isMobile
  if (!isMobile) mobileDrawerOpen.value = false
  compactSearchOpen.value = false
}

function handleGlobalKeydown(event: KeyboardEvent) {
  if (event.key !== 'Escape') return
  if (mobileDrawerOpen.value) closeMobileDrawer()
  if (compactSearchOpen.value) compactSearchOpen.value = false
}

let mobileQuery: MediaQueryList | null = null
let previousBodyOverflow = ''

onMounted(() => {
  mobileQuery = window.matchMedia('(max-width: 767px)')
  handleMediaChange()
  mobileQuery.addEventListener('change', handleMediaChange)
  window.addEventListener('keydown', handleGlobalKeydown)
})

watch(() => route.fullPath, () => {
  searchQuery.value = ''
  closeMobileDrawer()
  compactSearchOpen.value = false
})

watch(() => mobileViewport.value && mobileDrawerOpen.value, isOpen => {
  if (isOpen) {
    previousBodyOverflow = document.body.style.overflow
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = previousBodyOverflow
  }
})

onBeforeUnmount(() => {
  mobileQuery?.removeEventListener('change', handleMediaChange)
  window.removeEventListener('keydown', handleGlobalKeydown)
  document.body.style.overflow = previousBodyOverflow
})
</script>

<template>
  <div class="dash-root">
    <aside
      id="main-sidebar"
      :class="[
        'sidebar',
        {
          'sidebar--collapsed': !sidebarExpanded,
          'sidebar--mobile-open': mobileViewport && mobileDrawerOpen,
        },
      ]"
      aria-label="Navegação principal"
      :aria-hidden="mobileViewport && !mobileDrawerOpen ? 'true' : undefined"
      :inert="mobileViewport && !mobileDrawerOpen"
    >
      <div class="sidebar-brand">
        <div class="brand-lockup">
          <div class="brand-mark" aria-hidden="true">
            <div class="brand-symbol"></div>
          </div>
          <Transition name="fade-slide">
            <div v-if="sidebarExpanded" class="brand-info">
              <span class="brand-name">ERP</span>
              <span class="brand-sub">Modelagem</span>
            </div>
          </Transition>
        </div>

        <button
          id="btn-sidebar-toggle"
          class="sidebar-toggle"
          type="button"
          :aria-label="mobileViewport
            ? 'Fechar menu lateral'
            : desktopSidebarExpanded
              ? 'Recolher barra lateral'
              : 'Expandir barra lateral'"
          :aria-controls="'main-sidebar'"
          :aria-expanded="mobileViewport ? mobileDrawerOpen : desktopSidebarExpanded"
          @click="toggleSidebar"
        >
          <ChevronLeft v-if="mobileViewport || desktopSidebarExpanded" :size="18" aria-hidden="true" />
          <ChevronRight v-else :size="18" aria-hidden="true" />
        </button>
      </div>

      <div
        v-if="authStore.hasPermission('TELA_NOVA_ORDEM_TESTE') && (authStore.hasPermission('EDITAR_TELA_NOVA_ORDEM_TESTE') || authStore.hasPermission('CONFIGURAR_MODELO_ORDEM'))"
        class="sidebar-action-wrap"
      >
        <RouterLink
          to="/dashboard/novo-teste"
          class="btn-sidebar-action"
          :class="{ 'btn-sidebar-action--active': route.path === '/dashboard/novo-teste' }"
          :title="!sidebarExpanded ? (authStore.hasPermission('EDITAR_TELA_NOVA_ORDEM_TESTE') ? 'Iniciar Novo Teste' : 'Fila da Modelagem') : undefined"
          @click="handleNavigation"
        >
          <PlusCircle :size="19" class="action-icon" aria-hidden="true" />
          <Transition name="fade-slide">
            <span v-if="sidebarExpanded" class="action-label">{{ authStore.hasPermission('EDITAR_TELA_NOVA_ORDEM_TESTE') ? 'Iniciar Novo Teste' : 'Fila da Modelagem' }}</span>
          </Transition>
        </RouterLink>
      </div>

      <div class="sidebar-search">
        <div v-if="sidebarExpanded" class="search-control">
          <Search :size="17" class="search-icon" aria-hidden="true" />
          <input
            v-model="searchQuery"
            type="search"
            class="search-input"
            placeholder="Buscar tela"
            aria-label="Buscar telas de navegação"
          />
          <button
            v-if="searchQuery"
            class="search-clear"
            type="button"
            aria-label="Limpar busca"
            @click="clearSearch"
          >
            <X :size="15" aria-hidden="true" />
          </button>
        </div>

        <button
          v-else
          class="search-compact"
          type="button"
          title="Buscar telas"
          aria-label="Buscar telas de navegação"
          :aria-expanded="compactSearchOpen"
          @click="toggleCompactSearch"
        >
          <Search :size="18" aria-hidden="true" />
        </button>

        <div
          v-if="!sidebarExpanded && compactSearchOpen"
          class="sidebar-search-popover"
          @keydown.esc.stop="compactSearchOpen = false"
        >
          <div class="search-control">
            <Search :size="17" class="search-icon" aria-hidden="true" />
            <input
              ref="compactSearchInput"
              v-model="searchQuery"
              type="search"
              class="search-input"
              placeholder="Buscar tela"
              aria-label="Buscar telas de navegação"
            />
            <button
              v-if="searchQuery"
              class="search-clear"
              type="button"
              aria-label="Limpar busca"
              @click="clearSearch"
            >
              <X :size="15" aria-hidden="true" />
            </button>
          </div>
        </div>
      </div>

      <nav class="sidebar-nav" aria-label="Telas do ERP">
        <section
          v-for="section in visibleNavSections"
          :key="section.id"
          class="nav-section"
        >
          <h2 v-if="sidebarExpanded" class="nav-section-title">{{ section.label }}</h2>
          <RouterLink
            v-for="item in section.items"
            :key="item.to"
            :to="item.to"
            class="nav-item"
            :class="{ 'nav-item--active': isNavItemActive(item.to) }"
            :title="!sidebarExpanded ? item.label : undefined"
            :aria-current="isNavItemActive(item.to) ? 'page' : undefined"
            @click="handleNavigation"
          >
            <component :is="item.icon" :size="19" class="nav-icon" aria-hidden="true" />
            <Transition name="fade-slide">
              <span v-if="sidebarExpanded" class="nav-label">{{ item.label }}</span>
            </Transition>
            <ChevronRight
              v-if="sidebarExpanded && isNavItemActive(item.to)"
              :size="15"
              class="nav-active-chevron"
              aria-hidden="true"
            />
          </RouterLink>
        </section>
        <p v-if="!hasNavigationMatches" class="nav-empty" aria-live="polite">
          Nenhuma tela encontrada
        </p>
      </nav>

      <div class="sidebar-footer">
        <div
          class="user-chip"
          aria-label="Usuário logado"
          :title="!sidebarExpanded ? userDisplayName + (user?.perfilNome ? ' — ' + user.perfilNome : '') : undefined"
        >
          <div class="user-avatar" aria-hidden="true">{{ userInitial }}</div>
          <div v-if="sidebarExpanded" class="user-info">
            <span class="user-name">{{ userDisplayName }}</span>
            <span v-if="user?.perfilNome" class="user-role">{{ user.perfilNome }}</span>
          </div>
        </div>
        <button
          id="btn-logout"
          class="btn-logout"
          type="button"
          title="Sair do sistema"
          aria-label="Sair do sistema"
          @click="logout"
        >
          <LogOut :size="17" aria-hidden="true" />
          <span v-if="sidebarExpanded">Sair</span>
        </button>
      </div>
    </aside>

    <button
      v-if="mobileViewport && mobileDrawerOpen"
      class="sidebar-backdrop"
      type="button"
      aria-label="Fechar menu lateral"
      @click="closeMobileDrawer"
    ></button>

    <div class="main-wrapper">
      <header v-if="mobileViewport" class="mobile-topbar">
        <button
          class="mobile-menu-toggle"
          type="button"
          aria-label="Abrir menu de navegação"
          aria-controls="main-sidebar"
          :aria-expanded="mobileDrawerOpen"
          @click="mobileDrawerOpen = true"
        >
          <Menu :size="20" aria-hidden="true" />
        </button>
        <div class="mobile-brand-mark" aria-hidden="true">
          <div class="brand-symbol"></div>
        </div>
        <div class="mobile-brand-info">
          <span class="mobile-brand-name">ERP</span>
          <span class="mobile-brand-sub">Modelagem</span>
        </div>
      </header>

      <main
        class="main-content"
        :class="{
          'main-content--dashboard-gerencial': route.path === '/dashboard/gerencial',
          'main-content--rastreamento': route.name === 'rastreamento-ordem',
        }"
        id="main-content"
      >
        <RouterView />
      </main>
    </div>
  </div>
</template>

<style scoped>
.dash-root {
  --sidebar-bg: #0d162d;
  --sidebar-surface: #111c30;
  --sidebar-border: rgba(148, 163, 184, 0.14);
  --sidebar-muted: #94a3b8;
  --sidebar-text: #e2e8f0;
  --sidebar-blue: #4d46e0;
  display: flex;
  min-height: 100dvh;
  background: #f1f5f9;
}

.sidebar {
  position: sticky;
  top: 0;
  z-index: 20;
  display: flex;
  flex: 0 0 auto;
  flex-direction: column;
  width: 17.5rem;
  height: 100dvh;
  color: var(--sidebar-text);
  background: var(--sidebar-bg);
  border-right: 1px solid rgba(2, 6, 23, 0.35);
  border-radius: 0 1rem 1rem 0;
  backdrop-filter: blur(4px);
  transition: width 0.24s cubic-bezier(0.32, 0.72, 0, 1), transform 0.24s ease, box-shadow 0.24s ease;
}

.sidebar--collapsed {
  width: 4.5rem;
}

.sidebar-brand {
  display: flex;
  min-height: 4.75rem;
  flex: 0 0 auto;
  align-items: center;
  justify-content: space-between;
  gap: 0.5rem;
  padding: 0.75rem 0.8rem 0.75rem 1rem;
  border-bottom: 1px solid var(--sidebar-border);
}

.brand-lockup {
  display: flex;
  min-width: 0;
  align-items: center;
  gap: 0.75rem;
}

.brand-mark,
.mobile-brand-mark {
  display: flex;
  width: 2rem;
  height: 2rem;
  flex: 0 0 auto;
  align-items: center;
  justify-content: center;
  border-radius: 0.55rem;
  background: linear-gradient(135deg, #6962ef, #4d46e0);
  box-shadow: 0 3px 12px rgba(77, 70, 224, 0.3);
}

.brand-symbol {
  width: 1.4rem;
  height: 1.4rem;
  background: #fff;
  -webkit-mask: url('../assets/brand-symbol-white.png') center / 235% auto no-repeat;
  mask: url('../assets/brand-symbol-white.png') center / 235% auto no-repeat;
  mask-mode: luminance;
}

.brand-info,
.mobile-brand-info {
  display: flex;
  min-width: 0;
  flex-direction: column;
  overflow: hidden;
  white-space: nowrap;
}

.brand-name,
.mobile-brand-name {
  color: #f8fafc;
  font-size: 0.94rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  line-height: 1.15;
}

.brand-sub,
.mobile-brand-sub {
  color: #94a3b8;
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.075em;
  line-height: 1.35;
  text-transform: uppercase;
}

.sidebar-toggle,
.search-compact,
.mobile-menu-toggle {
  display: inline-flex;
  flex: 0 0 auto;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  background: rgba(255, 255, 255, 0.055);
  border: 1px solid rgba(148, 163, 184, 0.18);
  border-radius: 0.6rem;
  cursor: pointer;
  transition: color 0.16s ease, background 0.16s ease, border-color 0.16s ease;
}

.sidebar-toggle {
  width: 2rem;
  height: 2rem;
}

.sidebar-toggle:hover,
.search-compact:hover,
.mobile-menu-toggle:hover {
  color: #ffffff;
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(148, 163, 184, 0.28);
}

.sidebar-toggle:focus-visible,
.search-compact:focus-visible,
.mobile-menu-toggle:focus-visible,
.btn-sidebar-action:focus-visible,
.nav-item:focus-visible,
.btn-logout:focus-visible,
.search-clear:focus-visible {
  outline: 2px solid #4d46e0;
  outline-offset: 2px;
}

.sidebar--collapsed .sidebar-brand {
  min-height: 6rem;
  flex-direction: column;
  justify-content: center;
  gap: 0.55rem;
  padding: 0.65rem 0.4rem;
}

.sidebar--collapsed .brand-lockup {
  justify-content: center;
}

.sidebar--collapsed .brand-mark {
  width: 1.8rem;
  height: 1.8rem;
}

.sidebar--collapsed .sidebar-toggle {
  width: 1.8rem;
  height: 1.65rem;
}

.sidebar-action-wrap {
  flex: 0 0 auto;
  padding: 0.75rem 0.8rem;
  border-bottom: 1px solid var(--sidebar-border);
}

.btn-sidebar-action {
  display: flex;
  min-height: 2.8rem;
  align-items: center;
  gap: 0.7rem;
  padding: 0.65rem 0.85rem;
  color: #fff;
  background: #4d46e0;
  border: 1px solid rgba(162, 158, 255, 0.28);
  border-radius: 0.65rem;
  box-shadow: 0 5px 14px rgba(77, 70, 224, 0.22);
  font-size: 0.83rem;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.16s ease, transform 0.16s ease, box-shadow 0.16s ease;
}

.btn-sidebar-action:hover {
  background: #5b54eb;
  box-shadow: 0 7px 18px rgba(77, 70, 224, 0.3);
  transform: translateY(-1px);
}

.btn-sidebar-action--active {
  background: #3933b9;
}

.action-icon {
  flex: 0 0 auto;
}

.action-label {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sidebar--collapsed .sidebar-action-wrap {
  padding: 0.65rem 0.45rem;
}

.sidebar--collapsed .btn-sidebar-action {
  justify-content: center;
  padding: 0.65rem 0;
}

.sidebar-search {
  position: relative;
  flex: 0 0 auto;
  padding: 0.75rem 0.8rem 0.35rem;
}

.search-control {
  position: relative;
  display: flex;
  min-width: 0;
  height: 2.65rem;
  align-items: center;
  gap: 0.6rem;
  padding: 0 0.75rem;
  color: #000000;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 0.65rem;
  transition: border-color 0.16s ease, background 0.16s ease, box-shadow 0.16s ease;
}

.search-control:focus-within {
  background: #ffffff;
  border-color: rgba(77, 70, 224, 0.5);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.search-icon {
  display: block;
  flex: 0 0 auto;
  align-self: center;
  margin: 0;
}

.search-input {
  width: 100%;
  min-width: 0;
  padding: 0;
  color: #000000;
  background: transparent;
  border: 0;
  outline: 0;
  font: inherit;
  font-size: 0.8rem;
}

.search-input::placeholder {
  color: #000000;
}

.search-input::-webkit-search-cancel-button {
  display: none;
}

.search-clear {
  display: inline-flex;
  width: 1.5rem;
  height: 1.5rem;
  flex: 0 0 auto;
  align-items: center;
  justify-content: center;
  padding: 0;
  color: #000000;
  background: transparent;
  border: 0;
  border-radius: 0.35rem;
  cursor: pointer;
}

.search-clear:hover {
  color: #000000;
  background: rgba(77, 70, 224, 0.08);
}

.sidebar--collapsed .sidebar-search {
  display: flex;
  justify-content: center;
  padding: 0.6rem 0.4rem 0.45rem;
}

.search-compact {
  width: 2.8rem;
  height: 2.6rem;
}

.sidebar-search-popover {
  position: absolute;
  top: 0.55rem;
  left: calc(100% + 0.6rem);
  z-index: 30;
  width: 18rem;
  padding: 0.65rem;
  color: #000000;
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 0.75rem;
  box-shadow: 0 18px 42px rgba(2, 6, 23, 0.38);
}

.sidebar-nav {
  display: flex;
  min-height: 0;
  flex: 1 1 auto;
  flex-direction: column;
  gap: 0.45rem;
  padding: 0.55rem 0.55rem 0.75rem;
  overflow-x: hidden;
  overflow-y: auto;
  scrollbar-color: rgba(148, 163, 184, 0.32) transparent;
  scrollbar-width: thin;
}

.nav-section {
  display: flex;
  flex: 0 0 auto;
  flex-direction: column;
  gap: 0.18rem;
}

.nav-section + .nav-section {
  margin-top: 0.35rem;
  padding-top: 0.55rem;
  border-top: 1px solid #e2e8f0;
}

.nav-section-title {
  margin: 0;
  padding: 0.1rem 0.75rem 0.42rem;
  overflow: hidden;
  color: #000000;
  font-size: 0.62rem;
  font-weight: 800;
  letter-spacing: 0.11em;
  text-overflow: ellipsis;
  text-transform: uppercase;
  white-space: nowrap;
}

.nav-item {
  position: relative;
  display: flex;
  min-height: 2.8rem;
  align-items: center;
  gap: 0.75rem;
  padding: 0.62rem 0.75rem;
  overflow: hidden;
  color: var(--sidebar-muted);
  border: 1px solid transparent;
  border-radius: 0.62rem;
  font-size: 0.84rem;
  font-weight: 550;
  text-decoration: none;
  transition: color 0.16s ease, background 0.16s ease, border-color 0.16s ease;
}

.nav-item::before {
  position: absolute;
  top: 0.55rem;
  bottom: 0.55rem;
  left: 0;
  width: 3px;
  background: transparent;
  border-radius: 0 4px 4px 0;
  content: '';
  transition: background 0.16s ease;
}

.nav-item:hover {
  color: #000000;
  background: rgba(77, 70, 224, 0.06);
}

.nav-item--active {
  color: #000000;
  background: rgba(77, 70, 224, 0.11);
  border-color: rgba(77, 70, 224, 0.12);
}

.nav-item--active::before {
  background: #4d46e0;
}

.nav-icon {
  flex: 0 0 auto;
  color: #000000;
  transition: color 0.16s ease;
}

.nav-item:hover .nav-icon,
.nav-item--active .nav-icon {
  color: #000000;
}

.nav-label {
  min-width: 0;
  flex: 1 1 auto;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.nav-active-chevron {
  flex: 0 0 auto;
  color: #000000;
}

.sidebar--collapsed .sidebar-nav {
  align-items: center;
  padding-right: 0.45rem;
  padding-left: 0.45rem;
}

.sidebar--collapsed .nav-section {
  width: 100%;
}

.sidebar--collapsed .nav-item {
  justify-content: center;
  padding-right: 0;
  padding-left: 0;
}

.sidebar--collapsed .nav-item::before {
  left: -0.45rem;
}

.sidebar--collapsed .nav-empty {
  display: none;
}

.nav-empty {
  margin: 0.5rem 0.65rem;
  color: #000000;
  font-size: 0.75rem;
  line-height: 1.45;
}

.sidebar-footer {
  display: flex;
  flex: 0 0 auto;
  flex-direction: column;
  gap: 0.5rem;
  padding: 0.7rem 0.6rem 0.65rem;
  border-top: 1px solid var(--sidebar-border);
}

.user-chip {
  display: flex;
  min-width: 0;
  min-height: 3.35rem;
  align-items: center;
  gap: 0.65rem;
  padding: 0.45rem 0.55rem;
  overflow: hidden;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 0.65rem;
}

.user-avatar {
  display: flex;
  width: 2rem;
  height: 2rem;
  flex: 0 0 auto;
  align-items: center;
  justify-content: center;
  color: #eff6ff;
  background: linear-gradient(140deg, #5f58eb, #4d46e0);
  border: 1px solid rgba(77, 70, 224, 0.25);
  border-radius: 50%;
  font-size: 0.75rem;
  font-weight: 800;
}

.user-info {
  display: flex;
  min-width: 0;
  flex-direction: column;
  gap: 0.1rem;
}

.user-name,
.user-role {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.user-name {
  color: #000000;
  font-size: 0.75rem;
  font-weight: 700;
  line-height: 1.25;
}

.user-role {
  color: #000000;
  font-size: 0.65rem;
  font-weight: 550;
}

.btn-logout {
  display: flex;
  min-height: 2.65rem;
  align-items: center;
  gap: 0.6rem;
  padding: 0.55rem 0.75rem;
  color: #000000;
  background: transparent;
  border: 1px solid #e2e8f0;
  border-radius: 0.62rem;
  cursor: pointer;
  font: inherit;
  font-size: 0.8rem;
  font-weight: 650;
  text-align: left;
  transition: color 0.16s ease, background 0.16s ease, border-color 0.16s ease;
}

.btn-logout:hover {
  color: #fecaca;
  background: rgba(127, 29, 29, 0.18);
  border-color: rgba(248, 113, 113, 0.23);
}

.sidebar--collapsed .sidebar-footer {
  align-items: center;
  padding-right: 0.4rem;
  padding-left: 0.4rem;
}

.sidebar--collapsed .user-chip {
  justify-content: center;
  width: 100%;
  padding: 0.4rem 0;
}

.sidebar--collapsed .btn-logout {
  justify-content: center;
  width: 100%;
  padding-right: 0;
  padding-left: 0;
}

.main-wrapper {
  display: flex;
  min-width: 0;
  flex: 1 1 auto;
  flex-direction: column;
  height: 100dvh;
  overflow: hidden;
}

.main-content {
  min-width: 0;
  flex: 1 1 auto;
  padding: 1.75rem;
  overflow: auto;
}

.main-content.main-content--dashboard-gerencial {
  padding: 0;
  background: #f8fafc;
}

.main-content.main-content--rastreamento {
  padding: 0;
}

.mobile-topbar {
  display: none;
}

.sidebar-backdrop {
  display: none;
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.15s ease, transform 0.15s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateX(-6px);
}

@media (min-width: 1920px) {
  .sidebar {
    width: 18.5rem;
  }

  .sidebar--collapsed {
    width: 5rem;
  }

  .main-content {
    padding: 2.5rem;
  }
}

@media (min-width: 2560px) {
  .sidebar {
    width: 21rem;
  }

  .sidebar--collapsed {
    width: 5.25rem;
  }

  .nav-item {
    min-height: 3rem;
    font-size: 0.95rem;
  }

  .main-content {
    padding: 3rem;
  }
}

@media (max-width: 767px) {
  .dash-root {
    display: block;
  }

  .sidebar,
  .sidebar--collapsed {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    width: min(20rem, 86vw);
    height: 100dvh;
    transform: translateX(-101%);
    visibility: hidden;
    transition:
      transform 0.24s cubic-bezier(0.32, 0.72, 0, 1),
      visibility 0s linear 0.24s,
      box-shadow 0.24s ease;
  }

  .sidebar--mobile-open {
    transform: translateX(0);
    visibility: visible;
    box-shadow: 18px 0 42px rgba(2, 6, 23, 0.34);
    transition:
      transform 0.24s cubic-bezier(0.32, 0.72, 0, 1),
      visibility 0s,
      box-shadow 0.24s ease;
  }

  .sidebar--collapsed .sidebar-brand,
  .sidebar-brand {
    min-height: 4.75rem;
    flex-direction: row;
    justify-content: space-between;
    gap: 0.5rem;
    padding: 0.75rem 0.8rem 0.75rem 1rem;
  }

  .sidebar--collapsed .brand-lockup,
  .brand-lockup {
    justify-content: flex-start;
  }

  .sidebar--collapsed .brand-mark,
  .brand-mark {
    width: 2rem;
    height: 2rem;
  }

  .sidebar--collapsed .sidebar-toggle,
  .sidebar-toggle {
    width: 2rem;
    height: 2rem;
  }

  .sidebar--collapsed .sidebar-action-wrap,
  .sidebar-action-wrap {
    padding: 0.75rem 0.8rem;
  }

  .sidebar--collapsed .btn-sidebar-action,
  .btn-sidebar-action {
    justify-content: flex-start;
    padding: 0.65rem 0.85rem;
  }

  .sidebar--collapsed .sidebar-search,
  .sidebar-search {
    display: block;
    padding: 0.75rem 0.8rem 0.35rem;
  }

  .sidebar--collapsed .sidebar-nav,
  .sidebar-nav {
    align-items: stretch;
    padding: 0.55rem 0.55rem 0.75rem;
  }

  .sidebar--collapsed .nav-section,
  .nav-section {
    width: auto;
  }

  .sidebar--collapsed .nav-item,
  .nav-item {
    justify-content: flex-start;
    padding: 0.62rem 0.75rem;
  }

  .sidebar--collapsed .nav-item::before,
  .nav-item::before {
    left: 0;
  }

  .sidebar--collapsed .sidebar-footer,
  .sidebar-footer {
    align-items: stretch;
    padding: 0.7rem 0.6rem 0.65rem;
  }

  .sidebar--collapsed .user-chip,
  .user-chip {
    justify-content: flex-start;
    width: auto;
    padding: 0.45rem 0.55rem;
  }

  .sidebar--collapsed .btn-logout,
  .btn-logout {
    justify-content: flex-start;
    width: auto;
    padding: 0.55rem 0.75rem;
  }

  .sidebar-backdrop {
    position: fixed;
    inset: 0;
    z-index: 15;
    display: block;
    padding: 0;
    background: rgba(2, 6, 23, 0.56);
    border: 0;
    backdrop-filter: blur(2px);
  }

  .main-wrapper {
    height: 100dvh;
    min-height: 100dvh;
  }

  .mobile-topbar {
    position: relative;
    z-index: 5;
    display: flex;
    min-height: 3.75rem;
    flex: 0 0 auto;
    align-items: center;
    gap: 0.7rem;
    padding: 0 0.9rem;
    background: rgba(255, 255, 255, 0.96);
    border-bottom: 1px solid #dbe4f0;
    box-shadow: 0 2px 10px rgba(15, 23, 42, 0.035);
  }

  .mobile-menu-toggle {
    width: 2.35rem;
    height: 2.35rem;
    color: #334155;
    background: #f8fafc;
    border-color: #dbe4f0;
  }

  .mobile-brand-mark {
    width: 1.85rem;
    height: 1.85rem;
    border-radius: 0.5rem;
  }

  .mobile-brand-name {
    color: #0f172a;
    font-size: 0.82rem;
  }

  .mobile-brand-sub {
    color: #64748b;
    font-size: 0.58rem;
  }

  .main-content {
    padding: 0.85rem;
  }
}

@media (max-width: 380px) {
  .main-content {
    padding: 0.65rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
/* Dark text theme is paired with the restored dark sidebar for contrast. */
.sidebar .brand-name { color: #f8fafc; }
.sidebar .brand-sub { color: #8b9ab5; }
.sidebar .sidebar-toggle,
.sidebar .search-compact { color: #9fb0c9; background: rgba(255, 255, 255, 0.045); border-color: rgba(148, 163, 184, 0.16); }
.sidebar .sidebar-toggle:hover,
.sidebar .search-compact:hover { color: #fff; background: rgba(77, 70, 224, 0.2); border-color: rgba(129, 124, 255, 0.35); }
.sidebar .search-control { color: #8ea0bb; background: rgba(2, 6, 23, 0.42); border-color: rgba(148, 163, 184, 0.13); }
.sidebar .search-control:focus-within { background: rgba(2, 6, 23, 0.58); border-color: rgba(129, 124, 255, 0.58); }
.sidebar .search-input { color: #e2e8f0; }
.sidebar .search-input::placeholder { color: #71829e; }
.sidebar .search-clear { color: #9fb0c9; }
.sidebar .search-clear:hover { color: #fff; background: rgba(255, 255, 255, 0.08); }
.sidebar .sidebar-search-popover { color: #e2e8f0; background: #111c30; border-color: rgba(148, 163, 184, 0.2); }
.sidebar .nav-section + .nav-section { border-color: rgba(148, 163, 184, 0.1); }
.sidebar .nav-section-title { color: #71829e; }
.sidebar .nav-item { color: #94a3b8; }
.sidebar .nav-item:hover { color: #e2e8f0; background: rgba(255, 255, 255, 0.055); }
.sidebar .nav-item--active { color: #e0e7ff; background: rgba(77, 70, 224, 0.22); border-color: rgba(129, 124, 255, 0.14); }
.sidebar .nav-item--active::before { background: #817cff; }
.sidebar .nav-icon { color: #8293ad; }
.sidebar .nav-item:hover .nav-icon,
.sidebar .nav-item--active .nav-icon,
.sidebar .nav-active-chevron { color: #aaa6ff; }
.sidebar .nav-empty { color: #8ea0bb; }
.sidebar .user-chip { background: rgba(255, 255, 255, 0.045); border-color: rgba(148, 163, 184, 0.13); }
.sidebar .user-name { color: #e2e8f0; }
.sidebar .user-role { color: #91a1ba; }
.sidebar .btn-logout { color: #b9c5d7; background: transparent; border-color: rgba(148, 163, 184, 0.12); }

</style>

```

### Destination file: `src/index.css` (referência global do projeto Vue original)

Inclua somente se o destino não possuir estilos globais equivalentes. O SFC não seleciona uma dessas famílias explicitamente; os controles herdam a fonte do app.

```css
@import url('https://fonts.googleapis.com/css2?family=Geist:wght@300;400;500;600;700;800;900&family=Nunito:wght@300;400;500;600;700;800;900&family=Inter:wght@300;400;500;600;700;800;900&display=swap');

@tailwind base;
@tailwind components;
@tailwind utilities;

```

### Destination file: `postcss.config.js` (se o app usa Tailwind CSS 3)

Mescle no PostCSS existente; não sobrescreva configuração de outro projeto sem verificar seus plugins.

```js
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

### Destination file: `tailwind.config.js` (configuração mínima de referência)

Mantenha os globs compatíveis com a estrutura real do destino e preserve outras extensões já existentes.

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## Assets auxiliares preservados

Os dois logos PNGs permanecem como os únicos arquivos ao lado deste `SKILL.md`: `assets/brand-symbol-white.png` (1536×1024 RGB, 545,499 bytes) e `assets/logo-automacao.png` (1536×1024 RGBA, 982,305 bytes). Codificá-los em Base64 aumentaria o documento em aproximadamente um terço e tornaria mais frágil sua recuperação; mantenha os arquivos originais e copie-os sem conversão.

## Checklist final

- [ ] O logo oficial aparece no login e no topo da sidebar, sem deformação.
- [ ] O nome/subtítulo do produto substituíram os textos ERP, mantendo posição e tipografia.
- [ ] O login manteve card, fundo pontilhado, dimensões, campos, botão, gradiente, rodapé e breakpoints.
- [ ] A sidebar manteve larguras, cabeçalho, recolhimento, categorias, item ativo, perfil, Sair, transições e drawer mobile.
- [ ] A busca foi incluída somente se fizer sentido; quando presente, permanece no local e no tema originais.
- [ ] Rotas, permissões, sessão e autenticação usam o projeto destino; nenhum endpoint, usuário, token ou segredo do ERP foi copiado.
- [ ] Caminhos dos assets são relativos ao app, sem dependência da localização da Skill ou do ERP.
- [ ] Verificação de tipos/build concluída e comportamento checado em desktop/mobile quando disponível.
