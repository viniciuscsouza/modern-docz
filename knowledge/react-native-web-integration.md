# Integração do React Native Web com Astro

## Visão Geral

A integração do React Native Web (RNW) em um ambiente como o Astro apresenta desafios específicos, principalmente devido à forma como os pacotes do ecossistema React Native são publicados. A solução para esses desafios reside na configuração do bundler subjacente do Astro, o Vite.

## Desafios Principais

A maioria das bibliotecas React Native é projetada para ser consumida pelo Metro, o bundler padrão do ecossistema React Native. O Metro possui um comportamento específico que difere dos bundlers web tradicionais como Vite ou Webpack:

1.  **Transpilação de `node_modules`**: O Metro transpila o código dentro de `node_modules`, enquanto o Vite, por padrão, não o faz. Muitas bibliotecas RNW são publicadas como código-fonte não transpilado.
2.  **Sintaxe Flow**: Muitos pacotes React Native ainda contêm sintaxe Flow, que precisa ser removida durante o processo de build.
3.  **Resolução de Módulos**: O Metro possui uma lógica de resolução de arquivos específica para plataformas (ex: `.web.js`, `.native.js`), que precisa ser replicada.
4.  **Aliasing**: O pacote `react-native` precisa ser substituído por `react-native-web`.
5.  **Variáveis Globais**: O ambiente React Native espera que certas variáveis globais (como `__DEV__`) estejam definidas.

## Solução Proposta: Vite Plugin

A abordagem mais eficaz para resolver esses problemas é utilizar um plugin do Vite que encapsule todas as configurações necessárias. A pesquisa indicou a existência de plugins como o `vite-plugin-rnw` e o `vite-plugin-react-native-web`, que foram criados exatamente para essa finalidade.

### Passos para a Integração

1.  **Instalar o Plugin**: Adicionar o plugin Vite escolhido (ex: `vite-plugin-rnw`) ao projeto.
2.  **Configurar o Astro**: Modificar o arquivo `astro.config.mjs` para incluir o plugin na configuração do Vite:

    ```javascript
    import { defineConfig } from 'astro/config';
    import { rnw } from 'vite-plugin-rnw'; // Exemplo

    export default defineConfig({
      vite: {
        plugins: [rnw()],
      },
    });
    ```

3.  **Transpilar Módulos Específicos**: Pode ser necessário configurar o plugin para transpilar explicitamente certos pacotes de `node_modules` que não são cobertos por padrão.

Esta abordagem delega a complexidade da configuração do RNW para um plugin dedicado, mantendo a configuração do Astro limpa e focada. Será o caminho a ser seguido na fase de migração do projeto.
