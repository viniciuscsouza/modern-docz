# Arquitetura Docz

## Visão Geral

Docz é um monorepo gerenciado pelo Lerna, projetado para documentar projetos de forma simples e eficiente. A arquitetura atual é baseada no Gatsby, com a lógica principal dividida em vários pacotes localizados no diretório `core`.

## Estrutura do Monorepo

A estrutura do monorepo é organizada da seguinte forma:

- **`core/`**: Contém os pacotes principais que compõem a funcionalidade do Docz.
- **`examples/`**: Inclui exemplos de uso do Docz.
- **`other-packages/`**: Abriga outros pacotes que não fazem parte do núcleo.

## Pacotes Principais (`core/`)

- **`docz`**: O pacote principal que os usuários instalam. Ele integra todos os outros pacotes e expõe a CLI do Docz.
- **`docz-core`**: Contém a lógica central de análise, processamento de arquivos e geração da documentação.
- **`gatsby-theme-docz`**: O tema do Gatsby que renderiza a interface do Docz.
- **`rehype-docz`** e **`remark-docz`**: Plugins para o ecossistema Remark/Rehype, usados para processar o conteúdo Markdown.

## Fluxo de Dados

1.  O usuário executa o comando `docz dev` ou `docz build`.
2.  A CLI do `docz` inicia o processo, utilizando o `docz-core` para encontrar e analisar os arquivos de código-fonte.
3.  O `docz-core` utiliza o `react-docgen` e o `react-docgen-typescript` para extrair a documentação dos componentes React.
4.  O conteúdo extraído é então processado pelos plugins `remark-docz` e `rehype-docz`.
5.  Finalmente, o `gatsby-theme-docz` renderiza o site de documentação com base nos dados processados.
