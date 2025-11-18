# Design

Este documento aborda as decisões de design e as questões em aberto relacionadas à modernização do Docz.

## Perguntas e Respostas

### P: Qual é o principal objetivo da modernização?

**R:** O objetivo principal é substituir o Gatsby pelo Astro como a base do Docz. Isso visa melhorar o desempenho, a experiência do desenvolvedor e tornar o projeto mais fácil de manter.

### P: Quais são os principais recursos a serem mantidos?

**R:** A principal funcionalidade a ser preservada é a capacidade de gerar documentação automaticamente a partir de arquivos MDX e a extração de props de componentes React (incluindo PropTypes e TypeScript). A integração com o React Native Web também é um recurso importante a ser adicionado.

### P: Como a arquitetura do projeto mudará?

**R:** A arquitetura será migrada de um sistema baseado em temas do Gatsby para uma arquitetura baseada em integrações do Astro. O `docz-core` provavelmente será o pacote mais afetado, pois lida com a lógica de bundling e análise de código.

### P: Quais são os desafios esperados?

**R:** O maior desafio será garantir a compatibilidade com o ecossistema MDX existente e migrar a extração de props de componentes (atualmente usando `react-docgen` e `react-docgen-typescript`) para funcionar com o Vite, o bundler subjacente do Astro. Além disso, a integração do React Native Web exigirá uma configuração personalizada do Vite.
