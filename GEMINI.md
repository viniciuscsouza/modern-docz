# Visão Geral do Projeto

Este projeto é um fork do Docz, uma ferramenta para criar sites de documentação a partir de arquivos MDX. O objetivo principal é modernizar o projeto substituindo o Gatsby pelo Astro, melhorando o desempenho e adicionando suporte para React Native Web.

A arquitetura atual é baseada em Gatsby, com a lógica principal de empacotamento e análise no pacote `docz-core`. A futura arquitetura baseada em Astro exigirá uma integração personalizada para extrair metadados de componentes React (PropTypes e TypeScript) e uma configuração específica do Vite para suportar React Native Web.

Este `GEMINI.md` é um guia para a IA que auxilia no desenvolvimento deste projeto.

## Regras essenciais
- **LEIA** os arquivos `README.md`, `DESIGN.MD`, `TECH-STACK.md` e `PLAN.md` antes de começar. Eles contêm o contexto e o plano de alto nível para a modernização.
- **SIGA** o plano de implementação em `PLAN.md` como a fonte da verdade para as tarefas a serem executadas.
- **REGISTRE** decisões arquiteturais importantes em `/knowledge/adr` (Architecture Decision Records).
- **DOCUMENTE** seu código e decisões, especialmente ao criar novas integrações ou plugins para o Astro/Vite.
- **TESTE** tudo: novo código requer novos testes; bugs exigem testes de regressão. A migração para o Astro exigirá a adaptação ou reescrita dos testes existentes.
- **GARANTA** que os testes sejam determinísticos e independentes.
- **REVISE** o código com atenção e mantenha a simplicidade. O objetivo é criar uma base de código mais limpa e manutenível.
