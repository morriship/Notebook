---
description: 'ISBN-13: 9780134578897'
---

# Effective SQL

### Ch 1: Data Model Design

* **Item 1: Verify That All Tables Have a Primary Key**
  * 選擇 primary key 時需要考量的幾個條件
    - 必須具有唯一性
    - 不允許被膩值為 null
    - 足夠穩定 (一旦被創建之後即不會再被更改)
    - 盡量簡單 (int 優於 float, 單一欄位優於複數欄位)
  * 複數欄位的 primary key 會造成系統額外開銷, 但依商業邏輯的需求有時這是合理的, 並且比起選用複數欄位, 另外新增一個欄位的開銷可能更大。
* **Item 2: Eliminate Redundant Storage of Data Items**
  * 重複的資料不僅浪費儲存空間, 還會造成資料不一致(inconsistent)
  * 解法: 分割 talbe, 套用 2NF & 3NF
* **Item 3: Get Rid of Repeating Groups**
  * 避免以多個 columns 的形式存取群集類資料 (ex: name1, name2, name3), 需要做一對多或多對多的關聯時應該另外開 table 來解決
  * 銘記以下兩點
    * Columns are expensive.
    * Rows are cheap.
* **Item 4: Store Only One Property per Column**
  * 一個 column 只存一筆資訊, 以地址為例, 不要用 address 一個欄位存下所有地址資訊, 最好明確分存成 country / city / street 等等欄位, 需要使用時再用 CONCAT 組出原先的句子 (用 View 似乎也不錯?)
* **Item 5: Understand Why Storing Calculated Data is Usually a Bad Idea**
  * 與 Trigger 相比, Calculated Column 一般來說較易實現並且具有較高的效能
  * Calculated Column 可被優化程度依以下兩種狀態區別
    1. Deterministic: 依相同 Table 的不同欄位為依據所建立, 可建立 index 以提高查詢的效能
    1. Nondeterministic: 資料源有來自於其他 table, 不能建立 index, 每次查詢都會重新運算
  * 用 View 替代 Calculated Column 在多數情況下算是一個可優先被考量的選擇
* **Item 6: Define Foreign Keys to Protect Referential Integrity**
  * 用 Foreign Keys 建立表單的關聯性以及確保資料完整
  * 用 `ON UPDATE CASCADE`、`ON DELETE CASCADE` 輔助 table 間增刪及修改時的互動
* **Item 7: Be Sure Your Table Relationships Make Sense**
* **Item 8: When 3NF Is Not Enough, Normalize More**
* **Item 9: Use Denormalization for Information Warehouses**

### Ch 2: Programmability and Index Design

* **Item 10: Factor in Nulls When Creating Indexes**
* **Item 11: Carefully Consider Creation of Indexes to Minimize Index and Data Scanning**
* **Item 12: Use Indexes for More than Just Filtering**
* **Item 13: Don't Go Overboard with Triggers**
* **Item 14: Consider Using a Filtered Index to Include or Exclude a Subset of Data**
* **Item 15: Use Declarative Constraints Instead of Programming Checks**
* **Item 16: Know Which SQL Dialect Your Product Uses and Write Accordingly**
* **Item 17: Know When to Use Calculated Results in Indexes**

### Ch 3: When You Can't Change the Design

* **Item 18: Use Views to Simplify What Cannot Be Changed**
* **Item 19: Use ETL to Turn Nonrelational Data into Information**
* **Item 20: Create Summary Tables and Maintain Them**
* **Item 21: Use UNION Statements to "Unpivot" Non-normalized Data**

### Ch 4: Filtering and Finding Data

* **Item 22: Understand Relational Algebra and How It is Implemented in SQL**
* **Item 23: Find Non-matches or Missing Records**
* **Item 24: Know When to Use CASE to Solve a Problem**
* **Item 25: Know Techniques to Solve Multiple-Criteria Problems**
* **Item 26: Divide Your Data If You Need a Perfect Match**
* **Item 27: Know How to Correctly Filter a Range of Dates on a Column Containing Both Date and Time**
* **Item 28: Write Sargable Queries to Ensure That the Engine Will Use Indexes**
* **Item 29: Correctly Filter the "Right" Side of a "Left" Join**
