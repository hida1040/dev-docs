# dev-docs

This repository contains documentation outlining common development rules for Fiori FreeStyle application development,  
intended to ensure consistency among developers.

[Go to document](src/index.md).

## Pandoc

Pandoc is a free and open-source document conversion tool that helps convert documents between various formats.  
It mainly supports conversions between file formats such as Markdown, HTML, LaTeX, and Word.

### Install

#### Windows

1. Download the installer from the [Pandoc official website](https://pandoc.org/installing.html).
2. After installation, check if the pandoc command is available:

```sh
$ pandoc --version
```

#### macOS/Linux (Homebrew recommended)

```sh
$ brew install pandoc
```

### Basic usage (Markdown → Word)

Output a Word file from the root directory of the repository.

```sh
$ pandoc src/pages/guide-coding-style.md --metadata-file=pandoc/metadata.yaml --resource-path=./src/pages/ --highlight-style=breezeDark --reference-doc=pandoc/reference.docx -o output/SAPUI5_FreeStyle_開発共通ルール.docx
$ pandoc src/pages/guide-coding-style_en.md --metadata-file=pandoc/metadata.yaml --resource-path=./src/pages/ --highlight-style=breezeDark --reference-doc=pandoc/reference.docx -o output/SAPUI5_Freestyle_Development_Rules_english.docx
$ pandoc src/pages/guide-coding-style_vn.md --metadata-file=pandoc/metadata.yaml --resource-path=./src/pages/ --highlight-style=breezeDark --reference-doc=pandoc/reference.docx -o output/SAPUI5_Freestyle_Development_Rules_vietnamese.docx
```

How to output style references for Word.

```sh
$ pandoc --print-default-data-file reference.docx > reference.docx
```

## Technical Element References

### SAPUI5 / JavaScript

-   [SAPUI5 : JavaScript Coding Guidelines](https://help.sap.com/docs/UI_ADD-ON_FOR_SAP_NETWEAVER_20/b4b7cba328bc480d9b373c7da9335537/eded636b85584cd586b1fe231d2b5dac.html)
-   [ECMAScript 6 features](https://github.com/lukehoban/es6features)
-   [JSDoc Guidelines](https://github.com/SAP/openui5/blob/master/docs/guidelines/jsdoc.md)
-   [UI5 Web Components](https://sap.github.io/ui5-webcomponents/)

#### Linter / Formatter / Utility

-   [Prettier](https://prettier.io/)
-   [ESLint](https://eslint.org/)

##### Visual Studio Code Extensions

-   [UI5 Language Assistant](https://marketplace.visualstudio.com/items?itemName=SAPOSS.vscode-ui5-language-assistant)
-   [Prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
-   [vscode-ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
-   [Todo-Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)

#### Modern JavaScript Framework

-   [React](https://react.dev/)
-   [Vue.js](https://vuejs.org/)
-   [Angular](https://angular.dev/)

#### Unit Testing

-   [QUnit](https://qunitjs.com/)
-   [Jest](https://jestjs.io/)
-   [Vitest](https://vitest.dev/)

### IDE

-   [Business Application Studio](https://www.sap.com/japan/products/technology-platform/business-application-studio.html)
-   [Visual Studio Code](https://code.visualstudio.com/)

### MarkDown

-   [MarkdownGuide](https://www.markdownguide.org/)
-   [tree.nathanfriend.com](https://tree.nathanfriend.com/)
-   [Markdown 記法 チートシート - Qiita](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)
-   [Markdown で note や info を使えない理由と対処法](https://roboin.io/article/2024/01/20/note-info-not-work-in-markdown/)

#### Visual Studio Code Extensions for MarkDown

-   [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
-   [Text Tables](https://marketplace.visualstudio.com/items?itemName=RomanPeshkov.vscode-text-tables)

### Pandoc

-   [Pandoc official website](https://pandoc.org/)
-   [pandoc 使い方まとめ - Qiita](https://qiita.com/kannkyo/items/01d653b08f7479cbd0d3)
