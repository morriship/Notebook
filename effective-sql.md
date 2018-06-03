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
* **Item 4: Store Only One Property per Column **
* **Item 5: Understand Why Storing Calculated Data is Usually a Bad Idea **
* **Item 6: Define Foreign Keys to Protect Referential Integrity **
* **Item 7: Be Sure Your Table Relationships Make Sense **
* **Item 8: When 3NF Is Not Enough, Normalize More **
* **Item 9: Use Denormalization for Information Warehouses **
* **Item 10: **
* **Item 11: **
* **Item 12: **
* **Item 13: **
* **Item 14: **
* **Item 15: **
* **Item 16: **
* **Item 17: **
* **Item 18: **
* **Item 19: **
* **Item 20: **
* **Item 21: **
* **Item 22: **
* **Item 23: **
* **Item 24: **
* **Item 25: **
* **Item 26: **
* **Item 27: **
