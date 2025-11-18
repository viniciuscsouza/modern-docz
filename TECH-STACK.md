# Tech Stack

Este documento descreve a pilha de tecnologia para o Docz modernizado.

## Ferramentas a Adicionar

- **[Astro](https://astro.build/):** O novo framework base para construção do site. Ele substituirá o Gatsby.
- **[Vite](https://vitejs.dev/):** O bundler que vem com o Astro. Precisaremos configurá-lo para a integração com o React Native Web.
- **[React Native Web](https://necolas.github.io/react-native-web/):** Para suportar a documentação de componentes React Native.

## Ferramentas a Manter

- **[Lerna](https://lerna.js.org/):** Continuará sendo usado para gerenciar o monorepo.
- **[React](https://reactjs.org/):** O Docz continuará focado em documentar componentes React.
- **[MDX](https://mdxjs.com/):** O formato principal para escrever a documentação.
- **[react-docgen](https://github.com/reactjs/react-docgen):** Para extrair informações de PropTypes de componentes React.
- **[react-docgen-typescript](https://github.com/styleguidist/react-docgen-typescript):** Para extrair informações de tipos de componentes TypeScript.

## Ferramentas a Remover

- **[Gatsby](https://www.gatsbyjs.org/):** Será completamente substituído pelo Astro.
- **Dependências relacionadas ao Gatsby:** Todos os plugins e pacotes específicos do Gatsby serão removidos.
