# Diretriz Corporativa: Design System e Interface Visual

## 1. Visão Geral e Princípios
O Design System corporativo padroniza a linguagem visual de todas as interfaces web e terminais industriais. Ele é construído sobre o **Tailwind CSS**, assegurando consistência estética, alto desempenho de renderização e conformidade com normas de acessibilidade e ergonomia fabril.

---

## 2. Paleta de Cores e Tokens Semânticos

As classes de cores do Tailwind são configuradas com aliases semânticos:

* **Primary (Identidade Corporativa):** Tons de azul institucional (`primary-500` a `primary-700`) para botões de ação principal, cabeçalhos e elementos de destaque.
* **Neutral / Slate (Superfícies e Textos):** Tons de ardósia (`slate-900` para texto de alto contraste, `slate-100` a `slate-50` para fundos).
* **Feedback e Status Operacional:**
  * **Success (Verde):** `emerald-600` (Conformidade, Peça Aprovada, Máquina Ativa).
  * **Warning (Amarelo/Âmbar):** `amber-500` (Atenção, Limite de Tolerância, Manutenção Próxima).
  * **Danger (Vermelho):** `rose-600` (Parada de Máquina, Peça Rejeitada, Erro Crítico).
  * **Info (Azul Claro):** `sky-500` (Instrução Operacional, Leitura de Apoio).

---

## 3. Diretrizes para Terminais de Chão de Fábrica

1. **Áreas de Toque Amplas (Touch Targets):** Em telas touch industriais, botões operacionais devem ter dimensões mínimas de `48px x 48px` (classes `min-h-[48px] px-6 text-lg`).
2. **Alto Contraste Visual:** É proibido o uso de cinzas de baixo contraste em ambientes com iluminação industrial intensa ou reflexos de galpão.
3. **Tipografia Legível:** Família tipográfica `Inter` ou fontes sem serifa legíveis em distâncias superiores a 1 metro.
4. **Modo Noturno / Dark Mode:** Suporte a tema escuro para postos de trabalho operando em turnos noturnos.
