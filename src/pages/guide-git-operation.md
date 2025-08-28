# バージョン管理方針

本項ではソースコードのバージョン管理方針、推奨事項について定める。

## 基本方針

- AWS CodeCommit を用いたソースコードのバージョン管理を行う。
- 各種アプリケーションのソースコードは、領域ごとにそれぞれ単一のリポジトリに保存して管理する。（[モノレポ](https://en.wikipedia.org/wiki/Monorepo)）
- main ブランチでのソースコードの変更、main ブランチへの直接的な PUSH は禁止とする。Pull Request (レビュー) を経由してマージすること。
- 作業ブランチは main ブランチから作成すること。ただし、関連課題や他課題との不要な Conflict の発生が見込まれる場合は、develop ブランチに相当する作業ブランチから分岐することを許容する。

## ブランチ運用ルール

### フロー

開発者の効果的な共同作業の推進のため、ブランチ戦略は [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow) をベースとする。

GitHub flow は、“main” と “feature” の2種のブランチで構成された、Git-flow や GitLab flow と比較してシンプルなフロー。  
必要に応じて開発統合を目的とした “develop” ブランチの作成を許可する。  

![deploy](../static/img/git.github_flow.png)

| ブランチ        | 用途                                  | 例        |
| ----------- | ----------------------------------- | -------- |
| main        | リリース用またはプロジェクト最新のソースコードが保存された安定ブランチ | -        |
| develop     | 開発統合ブランチ(任意)                        | -        |
| feature/xxx | 開発用ブランチ                             | feature/login-form |

本アプリケーション開発においては、動作検証やレビューを目的とした開発用ブランチからの開発機へのデプロイを許可する。  
※ 一般的な運用では、 環境へのデプロイは main, develop 等の統合ブランチからのみ行う。

![deploy](../static/img/git.github_flow_deploy.png)

### commit

Commit メッセージにあたっては、[Semantic Commit Messages](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716) を参考に以下のような記述方法の採用を推奨する。 

Format: `<type>: <program id> <subject> #<issue number>` 


| 項目                | 説明                                            |
| ----------------- | --------------------------------------------- |
| `<type>`          | Commit 内容を簡潔に示すための Prefix                     |
| `<program id>`    | 対象のプログラムID                                    |
| `<subject>`       | Commit 内容の表題                                  |
| `#<issue number>` | 課題No. や 日付など。Commit 内容に対し、対象が明確である場合は記述を強く推奨。 |

`<type>` の例   
  - `feat`    : （ユーザー向けの新機能。ビルドスクリプトの新機能ではない）
  - `fix`     : （ユーザー向けのバグ修正。ビルドスクリプトの修正ではない）
  - `docs`    : （ドキュメントの変更）
  - `style`   : （フォーマット修正、セミコロンの抜けなど。プロダクションコードの変更はなし）
  - `refactor`: （プロダクションコードのリファクタリング。例: 変数名の変更）
  - `test`    : （不足しているテストの追加、テストのリファクタリング。プロダクションコードの変更はなし）
  - `chore`   : （Grunt タスクなどの更新。プロダクションコードの変更はなし）


e.g.
```
feat: ZXXR000 update search form #0000
fix: ZXXR000 registration bug fix #0000
```

Description 欄の記述は任意とする。  
また git コマンドを頻繁に実行する場合は、実行ミスの防止を目的として以下のような GUI ツールの使用を推奨する。

- [Fork](https://git-fork.com/)
- [GitHub Desktop](https://desktop.github.com/download/)
- [SourceTree](https://www.sourcetreeapp.com/)

### merge

main ブランチへの merge は Pull Request (レビュー) を経由すること。  
単一のタスクに対する修正が 複数回 main ブランチに merge されることを回避するため、  
main ブランチへの merge は、日本側のレビュー（内部受入）が完了した後に行うことが望ましい。  
日本側レビュー（内部受入）後のお客様受入時に発生した修正事項は、別途作業ブランチを新たに作成してプログラムの修正を行うこと。  
