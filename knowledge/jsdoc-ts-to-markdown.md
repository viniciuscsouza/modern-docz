# Conversão de JSDoc/TypeScript para Markdown

## Visão Geral

Uma das funcionalidades mais importantes do Docz é a capacidade de analisar o código-fonte (JSDoc e TypeScript) e gerar tabelas de propriedades (props) em Markdown. Esse processo é realizado principalmente pelas bibliotecas `react-docgen` e `react-docgen-typescript`.

## Processo de Análise

1.  **Detecção de Componentes**: O `docz-core` percorre os arquivos do projeto em busca de componentes React.
2.  **Extração de Metadados**: Para cada componente encontrado, o `docz-core` utiliza:
    *   **`react-docgen`**: Para componentes JavaScript que usam `propTypes`.
    *   **`react-docgen-typescript`**: Para componentes TypeScript que usam interfaces ou tipos.
3.  **Geração de AST**: Essas bibliotecas analisam o código-fonte e geram uma Árvore de Sintaxe Abstrata (AST), da qual extraem informações sobre as propriedades (nome, tipo, valor padrão, descrição, etc.).
4.  **Formatação para Markdown**: Os metadados extraídos são então formatados em uma tabela Markdown, que é inserida na página de documentação correspondente.

## Exemplo de Fluxo

-   **Entrada**: Um componente React com JSDoc ou tipos TypeScript.
-   **Saída**: Uma tabela Markdown com as propriedades do componente.

Esse processo automatizado simplifica a criação de documentação técnica e garante que ela esteja sempre sincronizada com o código-fonte.
