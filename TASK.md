# TASK.md: Tarefas de Desenvolvimento do Modern-Docz

Este documento descreve as tarefas de desenvolvimento necessárias para construir o Modern-Docz. As tarefas estão organizadas em fases e ordenadas por dependência.

## Fase 1: Fundação e Protótipo (Primeiro Marco)

*Objetivo: Criar a estrutura base do projeto e ter um protótipo funcional com Astro renderizando um componente React.*

-   [ ] **1.1: Configurar a Estrutura do Monorepo**
    -   [ ] Inicializar um `package.json` na raiz do projeto.
    -   [ ] Configurar `npm workspaces` para gerenciar os pacotes.
    -   [ ] Criar a estrutura de diretórios inicial (ex: `packages/`, `apps/`).

-   [ ] **1.2: Inicializar a Aplicação de Documentação com Astro**
    -   [ ] Criar um novo projeto Astro dentro do monorepo (ex: `apps/docs`).
    -   [ ] Adicionar a integração do Astro com React (`@astrojs/react`).
    -   [ ] Adicionar a integração do Astro com MDX (`@astrojs/mdx`).

-   [ ] **1.3: Configurar o Vite**
    -   [ ] Garantir que o Vite está sendo usado pelo Astro.
    -   [ ] Criar uma configuração base (`vite.config.js`) se for necessário estender o comportamento padrão do Astro.

-   [ ] **1.4: Criar o Protótipo de Renderização**
    -   [ ] Criar um componente React de exemplo (ex: `packages/ui/src/Button.jsx`).
    -   [ ] Criar uma página de documentação de exemplo (`apps/docs/src/pages/button.mdx`).
    -   [ ] Importar e renderizar o componente React dentro do arquivo MDX.
    -   [ ] Validar que o servidor de desenvolvimento do Astro (`astro dev`) renderiza a página e o componente corretamente.

## Fase 2: Suporte a React Native Web

*Objetivo: Habilitar a renderização de componentes React Native Web dentro de um "device frame" simulado.*

-   [ ] **2.1: Configurar o Aliasing para RNW**
    -   [ ] Adicionar as dependências `react-native-web`.
    -   [ ] Modificar a configuração do Vite para adicionar o alias de `react-native` para `react-native-web`.

-   [ ] **2.2: Criar Componente RNW de Exemplo**
    -   [ ] Criar um componente simples usando `View` e `Text` do `react-native` (ex: `packages/ui/src/Card.jsx`).

-   [ ] **2.3: Implementar o "Device Frame"**
    -   [ ] Criar um componente React (`DeviceFrame.jsx`) que renderize seus filhos (`children`) dentro de um container estilizado para parecer um celular.
    -   [ ] Integrar o `DeviceFrame` na aplicação Astro/MDX para envolver os componentes RNW.

-   [ ] **2.4: Validar a Renderização do Componente RNW**
    -   [ ] Criar uma página `card.mdx` e renderizar o componente `Card.jsx` dentro do `DeviceFrame`.
    -   [ ] Verificar se o componente é renderizado corretamente e se os estilos da web funcionam.

## Fase 3: Geração de Documentação de Props

*Objetivo: Extrair e exibir automaticamente as propriedades dos componentes.*

-   [ ] **3.1: Pesquisar Ferramentas Modernas de Extração**
    -   [ ] Investigar alternativas ao `react-docgen` e `react-docgen-typescript` que se integrem bem com o ecossistema Vite/Astro. (Ex: `react-docgen-vite`, `storybookjs/docs-tools`).
    -   [ ] Escolher a ferramenta mais adequada com base na performance e facilidade de integração.

-   [ ] **3.2: Implementar a Extração de Props**
    -   [ ] Criar um plugin ou uma integração para o Astro/Vite que use a ferramenta escolhida para extrair informações de props durante o build.
    -   [ ] Desenvolver um mecanismo para injetar os dados das props (em formato JSON) nas páginas MDX.

-   [ ] **3.3: Criar o Componente `PropsTable`**
    -   [ ] Criar um componente React que receba o JSON das props e renderize uma tabela formatada (Nome, Tipo, Padrão, Descrição).

-   [ ] **3.4: Integrar e Validar**
    -   [ ] Atualizar as páginas `button.mdx` e `card.mdx` para usar o componente `PropsTable`, passando os dados extraídos.
    -   [ ] Validar que a tabela é exibida corretamente com as informações das props dos componentes de exemplo.
