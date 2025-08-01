# テーブル 設計

本項で記載する内容は、Fiori FreeStyle アプリケーションでの [sap.ui.table.Table](https://sapui5.hana.ondemand.com/sdk/#/api/sap.ui.table.Table) の使用を前提としています。  

## 全体

### 文字揃え
一覧上に設置される Text 表記 および 各種入力形式に応じた各種 Input の 文字揃え を下表のとおり定める。  
※ 下表に指定がないものは原則 Alignment = Left とする。

| Field type        | Alignment | sap.ui.core.TextAlign |
| ---------------- | --------- | --------------------- |
| 文字列           | Left      | `Begin`               |
| 単一文字          | Center    | `Center`              |
| フラグ           | Center    | `Center`              |
| 日付             | Left      | `Begin`               |
| 数値             | Right     | `End`                 |
| 数量             | Right     | `End`                 |
| 金額             | Right     | `End`                 |
| 通貨             | Left      | `Begin`               |
| テーブルヘッダ    | Center    | `Center`              |
| CheckBox         | Center    | `Center`              |
| RadioButton      | Center    | `Center`              |

※ Checkbox, RadioButton は、セル内の Group ごとセンタリングする。  
※ CheckBox などに付随する文字列は左寄せ（Alignment=Left）とする。

**Reference:** [sap.ui.core.TextAlign](https://sapui5.hana.ondemand.com/sdk/#/api/sap.ui.core.TextAlign)

## 機能

### 基本機能

### ヘッダ部の機能
![ヘッダ部機能](../static/img/table.menu.general.png)

| No  | 機能               |
| --- | ---------------- |
| ①   | テーブルタイトル         |
| ②   | 表示件数             |
| ③   | バリアント管理          |
| ④   | ブックマーク（タイルとして保存） |
| ⑤   | 列設定              |
| ⑥   | 表示する行数の指定        |
| ⑦   | Excel ダウンロード     |