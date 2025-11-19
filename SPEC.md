# SPEC.md: Especificação do Modern-Docz

## 1. Visão do Produto

O **Modern-Docz** será uma ferramenta de documentação de componentes de UI de próxima geração, reconstruída sobre fundações modernas para oferecer uma experiência de desenvolvimento superior. A visão é migrar o Docz da stack legada (Gatsby) para uma arquitetura mais performática e flexível baseada em **Astro** e **Vite**.

O objetivo principal é criar uma ferramenta extremamente rápida, com live-reloading instantâneo, e que ofereça suporte de primeira classe para a documentação de componentes **React** e **React Native Web**.

## 2. Público-Alvo

-   **Times de Design System:** Equipes que mantêm bibliotecas de componentes e precisam de uma documentação centralizada, fácil de manter e que sirva como a "fonte da verdade".
-   **Desenvolvedores Individuais:** Desenvolvedores que criam e compartilham componentes de UI e precisam de uma maneira rápida e simples de documentá-los e testá-los visualmente.

## 3. Cenários de Uso

### Cenário Principal: Documentando um Novo Componente

1.  **Contexto:** Uma desenvolvedora está trabalhando em um novo componente `Button` para um design system que suporta tanto web quanto mobile (com React Native Web).
2.  **Ação:** Ela cria um novo arquivo `Button.mdx` no diretório de documentação.
3.  **Conteúdo:** Dentro do arquivo, ela escreve uma breve descrição do componente em Markdown e o importa:
    ```mdx
    ---
    name: Button
    route: /button
    ---

    import { Playground } from 'docz';
    import { Button } from './Button';

    # Button

    Este é o nosso componente de botão principal.

    <Playground>
      <Button title="Clique Aqui" />
    </Playground>
    ```
4.  **Resultado Esperado:**
    -   Ao salvar o arquivo, o servidor de desenvolvimento (baseado em Astro) detecta a mudança e atualiza o navegador instantaneamente (Hot Module Replacement).
    -   Uma nova página é criada na rota `/button`.
    -   O componente `Button` é renderizado dentro de um **"frame" que simula um dispositivo móvel**, permitindo a visualização precisa do seu comportamento em um ambiente mobile-first.
    -   Abaixo do `Playground`, uma **tabela de propriedades** (`props`) é gerada automaticamente, extraindo as definições de PropTypes do componente `Button.js` e exibindo o nome da prop, o tipo, o valor padrão e a descrição.

## 4. Requisitos

### Requisitos Funcionais

-   **FR1: Arquitetura baseada em Astro:** O projeto deve usar Astro para orquestrar o build e o roteamento das páginas de documentação.
-   **FR2: Suporte a MDX:** Permitir o uso de componentes React e RNW diretamente em arquivos Markdown (`.mdx`).
-   **FR3: Renderização de Componentes React Native Web:** Componentes identificados como sendo de React Native devem ser renderizados dentro de um "device frame" customizável.
-   **FR4: Aliasing para React Native Web:** A configuração de build (Vite) deve ter um alias para que `import 'react-native'` seja resolvido como `import 'react-native-web'`.
-   **FR5: Extração Automática de Props:** O sistema deve inspecionar os componentes React, extrair suas `props` (seja de PropTypes ou de tipos TypeScript) e exibir uma tabela de documentação. O sistema deve priorizar o uso de ferramentas modernas para essa extração.
-   **FR6: Componente `Playground`:** Deve haver um componente `Playground` que renderize o componente filho em um ambiente interativo (como no Docz original).

### Requisitos Não-Funcionais

-   **NFR1: Experiência de Desenvolvimento Fluida:** O servidor de desenvolvimento local deve ser extremamente rápido, com HMR (Hot Module Replacement) estável e ágil.
-   **NFR2: Estrutura de Monorepo:** O projeto deve ser estruturado como um monorepo, gerenciado com `npm workspaces`, para facilitar a manutenção de pacotes (`core`, `astro-theme`, etc.).
-   **NFR3: Build System com Vite:** Vite deve ser usado como o bundler principal, aproveitando sua velocidade para o desenvolvimento local.

## 5. Critérios de Sucesso

-   **CS1:** O tempo desde a inicialização do servidor de dev até a primeira página interativa é inferior a 5 segundos em um projeto de médio porte.
-   **CS2:** A experiência de HMR é percebida como "instantânea" pelos desenvolvedores.
-   **CS3:** Um desenvolvedor consegue adicionar uma página de documentação para um novo componente React Native Web e vê-la funcionando no navegador em menos de 3 minutos.
-   **CS4:** O build final de produção é otimizado (code-splitting, etc.) e gera um site estático performático.

## 6. Entidades do Domínio

-   **Documentação:** O conjunto de páginas e configurações que descrevem a biblioteca de componentes.
-   **Página (`.mdx`):** Um arquivo que mistura Markdown e componentes JSX para criar uma página de documentação.
-   **Componente:** O elemento de UI (React/RNW) que está sendo documentado.
-   **Propriedade (Prop):** As configurações ou APIs de um componente.
-   **Playground:** Uma área interativa para renderizar e experimentar um componente.
-   **Device Frame:** O container visual que simula um dispositivo móvel para renderizar componentes RNW.
