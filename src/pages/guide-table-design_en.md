# Table Design

The content described in this section assumes the use of [sap.ui.table.Table](https://sapui5.hana.ondemand.com/sdk/#/api/sap.ui.table.Table) in Fiori FreeStyle applications.

## List Output Section

The following specifications are defined as common specifications for the list output section in each area.  
If any items in this section are not explicitly described in the design documents, development should be based on the content described in this document.

### Text Alignment

The alignment of Text elements and various Input types in the table is defined in the table below.  
※ For Field types not listed in the table, the default alignment is Left.

| Field type        | Alignment | sap.ui.core.TextAlign |
| ---------------- | --------- | --------------------- |
| String           | Left      | `Begin`               |
| Single Character | Center    | `Center`              |
| Flag             | Center    | `Center`              |
| Date             | Left      | `Begin`               |
| Number           | Right     | `End`                 |
| Quantity         | Right     | `End`                 |
| Amount           | Right     | `End`                 |
| Currency         | Left      | `Begin`               |
| Table Header     | Center    | `Center`              |
| CheckBox         | Center    | `Center`              |
| RadioButton      | Center    | `Center`              |

※ CheckBox and RadioButton should be centered per group within the cell.  
※ Text associated with CheckBox or similar controls should be left-aligned (Alignment = Left).

**Reference:** [sap.ui.core.TextAlign](https://sapui5.hana.ondemand.com/sdk/#/api/sap.ui.core.TextAlign)

### "No" Column

A "No" column showing row numbers is placed on the left side of the list output section.  
The numbers in the No column are assigned starting from the first row for each record based on the data source extracted by the Fiori application and the pre-specified sort order.

### Checkbox Automation

In tables with checkboxes for record selection, if the value of an Input changes, the corresponding row should be checked automatically.  
The event handler `liveChange` should be used to detect changes.  
However, the use of `change` is permitted only when necessary due to internal logic constraints.

If there are requirements that differ from the above, the requirements for each screen should take precedence.  
The items below are defined as common display specifications.

## Header Section

The following are defined as common specifications for header section functions in each area.  
If the content in this section is not explicitly described in the design documents, development should be based on the content described here.

### Text Alignment

The alignment of column titles in the header section should generally be Center (Alignment = Center).

### Functions

The functions placed at the top of the table header vary depending on the area.

#### SD, FI

In the Sales (SD) and Accounting (FI) areas, the following functions are implemented as common features for each area.  
Additionally, functions defined for each add-on screen (such as change or add buttons) are also included.

![Header Functions - SD, FI](../static/img/table.menu.general.png)

| No  | Function                         |
| --- | -------------------------------- |
| ①   | Variant Management               |
| ②   | Row count selection              |
| ③   | Excel download                   |
| ④   | Bookmark (saved as a tile)      |

Functions such as Variant Management and Bookmarks are controlled by the event logic under `webapp/handler/ControlHandler`.

#### PPPS, MM

In the Production (PPPS) and Purchasing (MM) areas, additional functions and display items are included, and customized UIs are applied to identical functions.  
The following functions are implemented as common features for each area.  
Additionally, functions defined for each add-on screen (such as change or add buttons) are also included.

![Header Functions - PPPS, MM](../static/img/table.menu.custom.png)

| No  | Function                         |
| --- | -------------------------------- |
| ①   | Detail title                     |
| ②   | Number of displayed items        |
| ③   | Variant Management               |
| ④   | Bookmark (saved as a tile)      |
| ⑤   | Column settings                  |
| ⑥   | Row count selection              |
| ⑦   | Excel download                   |

Functions such as Variant Management and Bookmarks are controlled by the event logic under `webapp/handler/ControlHandler`.
