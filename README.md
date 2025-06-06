# ui5-dev-docs

This repository contains documentation outlining common development rules for Fiori application development,  
intended to ensure consistency among developers.

## Pandoc

### Install

#### macOS/Linux (Homebrew recommended)

```sh
$ brew install pandoc
```

#### Windows

1. Download the installer from the [Pandoc official website](https://pandoc.org/installing.html).
2. After installation, check if the pandoc command is available:

```sh
$ pandoc --version
```

### Basic usage (Markdown → Word)

Output a Word file from the root directory of the repository.

```sh
$ pandoc src/pages/guide-coding-style.md --metadata-file=pandoc/metadata.yaml --resource-path=./src/pages/ --highlight-style=breezeDark --reference-doc=pandoc/reference.docx -o output/UI5_FreeStyle_開発共通ルール.docx
```

## Technical Element References

### MarkDown

-   [MarkdownGuide](https://www.markdownguide.org/)
-   [tree.nathanfriend.com](https://tree.nathanfriend.com/)
-   [Markdown 記法 チートシート - Qiita](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)
-   [Markdown で note や info を使えない理由と対処法](https://roboin.io/article/2024/01/20/note-info-not-work-in-markdown/)
-   [Pandoc official website](https://pandoc.org/)
-   **Visual Studio Code Extensions for MarkDown**
    -   [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
    -   [Text Tables](https://marketplace.visualstudio.com/items?itemName=RomanPeshkov.vscode-text-tables)

### Linter / Formatter / Utility

-   [Prettier](https://prettier.io/)
-   [ESLint](https://eslint.org/)

-   **Visual Studio Code Extensions**
    -   [UI5 Language Assistant](https://marketplace.visualstudio.com/items?itemName=SAPOSS.vscode-ui5-language-assistant)
    -   [Prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
    -   [vscode-ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
    -   [Todo-Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)

### SAPUI5 / JavaScript

-   [SAPUI5 : JavaScript Coding Guidelines](https://help.sap.com/docs/UI_ADD-ON_FOR_SAP_NETWEAVER_20/b4b7cba328bc480d9b373c7da9335537/eded636b85584cd586b1fe231d2b5dac.html)
-   [ECMAScript 6 features](https://github.com/lukehoban/es6features)
-   [JSDoc Guidelines](https://github.com/SAP/openui5/blob/master/docs/guidelines/jsdoc.md)

### IDE

-   [Business Application Studio](https://www.sap.com/japan/products/technology-platform/business-application-studio.html)
-   [Visual Studio Code](https://code.visualstudio.com/)
