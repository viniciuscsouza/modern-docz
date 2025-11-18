# Plano de Implementação

Este documento detalha o plano para modernizar o Docz, migrando de Gatsby para Astro.

## Fases do Projeto

### Fase 1: Configuração e Prova de Conceito

1.  **Inicializar um novo pacote Astro:**
    *   Adicionar um novo pacote dentro do diretório `core` (ou um novo diretório, como `packages`) para o novo site baseado em Astro.
    *   Configurar o Astro com as dependências necessárias, como React e MDX.

2.  **Prova de Conceito de MDX:**
    *   Criar uma página MDX simples que renderize um componente React.
    *   Garantir que o HMR (Hot Module Replacement) do Astro funcione corretamente com componentes React dentro do MDX.

### Fase 2: Extração de Metadados de Componentes

1.  **Integrar `react-docgen` e `react-docgen-typescript`:**
    *   Pesquisar a melhor abordagem para executar `react-docgen` e `react-docgen-typescript` no ambiente do Astro/Vite.
    *   Isso provavelmente envolverá a criação de uma integração personalizada do Astro ou um plugin do Vite.
    *   O objetivo é analisar os componentes React importados nos arquivos MDX e injetar os metadados das props (nome, tipo, descrição, valor padrão) na página.

2.  **Disponibilizar Metadados para Componentes:**
    *   Criar uma maneira de acessar os metadados extraídos dentro do ambiente MDX.
    *   Recriar o componente `<Props>` que exibe a tabela de propriedades de um componente, usando os dados extraídos na etapa anterior.

### Fase 3: Integração com React Native Web

1.  **Configurar o Vite para React Native Web:**
    *   Modificar a configuração do Vite no `astro.config.mjs` para:
        *   Adicionar um alias de `react-native` para `react-native-web`.
        *   Garantir que os módulos do `react-native-web` sejam transpilados corretamente pelo Vite.

2.  **Testar Componentes React Native:**
    *   Criar um exemplo de documentação para um componente React Native para garantir que ele renderize corretamente no navegador.

### Fase 4: Recriar a Experiência do Docz

1.  **Portar/Recriar Componentes do Tema:**
    *   Recriar os componentes essenciais do Docz, como o `<Playground>`, para que funcionem no Astro.
    *   Desenvolver um novo tema padrão usando as melhores práticas do Astro.

2.  **Atualizar a CLI:**
    *   Modificar os comandos existentes da CLI do Docz (`docz dev`, `docz build`) para que eles executem os comandos correspondentes do Astro nos bastidores.

3.  **Migrar Exemplos:**
    *   Atualizar os exemplos existentes no diretório `examples` para usar a nova versão do Docz baseada em Astro.

## Contexto Técnico

A principal mudança técnica é a troca do mecanismo de build. O Gatsby usa um processo de build baseado em GraphQL para coletar dados em tempo de compilação. O Astro, com o Vite, usa uma abordagem mais moderna e rápida, com foco em enviar o mínimo de JavaScript para o cliente.

A parte mais desafiadora será a **extração de metadados**. No Gatsby, isso era feito com plugins que se integravam ao pipeline de dados do GraphQL. No Astro, precisaremos de uma solução que funcione com o pipeline de build do Vite. Uma integração personalizada do Astro que use a API de plugins do Vite parece ser a abordagem mais promissora. Essa integração interceptaria os arquivos MDX, encontraria os componentes React importados, executaria os scripts `docgen` e disponibilizaria os resultados para as páginas.
