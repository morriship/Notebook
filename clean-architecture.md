---
description: 'ISBN-13: 9780134494166'
---

# Clean Architecture

## PART II Programming Prardigms

### Ch 3~6 Paradigms

* **Structured Programming**
* **Object-Oriented Programming**
* **Functional Programming**

## PART III **Design Principles**

### Ch 7~11 SOLID Principles

* **SRP: Single Responsibility Principle**
  * 元件只該因為單一\(唯一的\)理由而被更動
* **OCP: Open-Closed Principle**
  * 讓功能容易被新增, 同時避免既有的組件被修改
* **LSP: Liskov Substitution Principle**
* **ISP: Interface Segregation Principle**
* **DIP: Dependency Inversion Principle**
  * 元件之間的應該依賴抽像化的 policy, 而非直接依賴 \(高耦合\)

## PART IV Component Principle

### Ch. 13 **Component Cohesion**

* **Reuse/Release Equivalence Principle**
* **Common Closure Principle**
* **Common Reuse Principle**

### Ch. 14 **Component Coupling**

* **Acyclic Dependencies Principle**
* **Stable Dependencies Principle**
* **Stable Abstractions Principle**

## PART V Architecture

### Ch. 15 What is Architecture?

### Ch. 16  Independence 

* **Use Cases**
  * 架構必須忠實程現出系統的意圖 詳: Ch.21
* **Operation**
  * 架構的設計對 operation 的影響很大, 例: scale up 的可能性
* **Development**
  * 當一個系統需要分給多個不同的團隊開發時, 必須拆成數個各自獨立的元件再分派下去, 以避免造成開發時團隊間~~互相傷害~~多餘的溝通成本
* **Deployment**
  * 一個好的架構應該可在建置完成後立即被佈署, 而不需要依賴一堆雜亂的設置檔  \(這裡具體來說應該是指不該具有高度的環境依賴, 像是在佈署階段要執行一堆 scripts 去做環境建置\)
* **Leaving options open**

  * 反正要弄出好架構超難的, 尤其像在初始階段連需求基本都還不明確,  所以期望的是銘記以上原則並讓架構盡量有彈性

* **Decoupling**
  * **Decoupling Layer**
    * 對架構各部套用 **SRP** / **CCP**
  * **Decoupling Use Cases**
    * 垂直分割, 減少各 Use Case 之間的耦合
  * **Decoupling Mode**
    * 水平分割, 增加每層 Service 之間的獨立性
* **Independence**
  * **Independent develop-abillity**
    * 當各元件之間具有獨立性時, 開發將能減少 team 之間的溝通頻率
  * **Independent deployability**
    * 架構設計足夠好的專案甚至能對各元件與服務做 hot-swapping
* **Duplication**
  * 工程師經常對相似的程式碼做提煉, 但有時程式碼可能只是恰巧相似而非目的一致, 過一陣子後再來看這段相似的程式碼可能已經出現極大差異
  * **Vertically separating**
    * 將 use cases 之間的程式碼提煉出來會增加耦合, 可能大幅增加日後對單一 case 的修改難度
  * **Horizontally separating**
    * 盡量落實各層之間的獨立性, 避免像是 **因為 DB 資料與前端需求格式相似而直接把從 DB 撈出來的資料送到前端** 之類的狀況發生
* **Decoupling Mode \(again\)**
  * **Source level**
    * 籍由控管元件之間的依賴關係減少修改單一元件後, 其餘元件必須跟著重新編譯的額外開銷.  \#monolithic structure
  * **Deployment level**
    * 利用 jar files、DLLs、shared libraries 減少抽換元件的成本 \(rebuild / redeploy\)
  * **Service level**
    * 透過切分 services 減少各元件之間的依賴性
  * 一個專案在不同時期可能會需要不同層級的解耦模式, 像是 services 的切分會增加人力與運算資源的開銷, 在運算需求不大時做這些是無意義的。 一個好的架構需要盡量保持解耦的可能性, 並且是可 reverse 的.

### Ch. 17 Boundaries Drawing Lines
  
* 所謂的架構設計就是在元件間畫線(boundary)的藝術, 在開發初期僅會有少數的切分, 主要是避免核心的 Business Rule 被其餘決策污染。銘記架構的設計是為了減少元件間的耦合, 盡量避免和 Business Rule 無關的決策, 像是 fremework、database、web servers、utility libraries、dependency injection 等
* **A coule of sad stories**
  * 在某公司曾經有一個專案, 由於架構師在專案初期就決策將 Business Rule 拆成三層服務, 但運算量需求並不大, 造成雖然三個服務都在同一台機器上做運算, 中間卻有著繁雜的溝通流程, 當新增 use case 時需對三層服務都做修改, 無故的浪費了大量的人力和運算資源
  * 另一個更慘的故事是過早採用 SoA 的決策導致開發與測試變的極度困難, 但我懶得寫這段的筆記了所以就這樣吧
* **FitNess**
  * 這裡講述的是作者經歷過的一段故事, 內容聚瞧於前面幾篇講述的印證, 忘記的話還是直接回去翻翻書吧 (p.163)
* **Which lines do you draw, and when do you draw them?**
  * 在重要的元件以及不重要的元件間畫線, 像是 Business Rule 和 GUI 之間, GUI 跟 DB 之間, DB 以及 Business Rules 之間。有些人可能會認為 DB 和 Business Rule 的關係是密不可分的, 但實際上 Business Rule 並不需要知曉和 DB 有關的任何事物儲如 schema、query language, 他們之間是可以透過抽像的 interface 去做溝通的。
  * Interface 應該被包含於 Business Rule, 而 DB Access component 則是在線的另一端, DB Access component 需要明確知道 Business Rule 但反之則否。
* **What about input and output?**
  * 由於許多專案裡與使用者是透過 GUI 與系統互動, 造成有時 GUI 會被當成需要最先被決定的事項之一, 但他們忘了一個重要的原則: The IO is irrelevant.
  * 同上, GUI 需要知道 Business Rule, 但反之則否
* **Plugin Architecture**
  * 跟 Plugin Pattern 的概念相同, 當 Business Rule 被清楚切分後, 任何在線另一端的元件都可被視為 plugin 做替換
* **The Plugin Argument**
  * Plugin 的 boundary 能視為一道防火牆, 確保核心的 Business Rule 不會被污染
  * 由於有明確的 boundary, 線兩邊的修改並不影響到對方, 因此每個元件可依照自己的步調做開發與修改
  * 將 project 套用 SRP 將會清楚了解線應該被畫在哪裡
* **Concolusion**
  * 首先將 project 分割成不同功能的元件, 再將這些元件做歸納為 Business Rule 或 plugin, 最後再將依賴關係建立出來 (plugin 單方面依賴 Business Rule)
  * 這種設計概念同 DIP/SAP, 讓較低階的 detail 依賴較高階的 interface 

### Ch. 18 Boundary Anatomy
* 系統架構的定義為 software components 以及它們之間的 boundaries 的集合
* 註: 本章節使用到的 level 定義在 Ch.19
* **Boundary Crossing**
  * **在執行期間一個 function 呼叫了 boundary 另一端的 function 並帶入了些參數**
  * 適當的管理 dependencies (ISP?) 即為畫出良好的 boundary
* **The Dreaded Monolith**
  * **Monolith** 的一般泛指一個可被執行的完整檔案(可能包含許多靜態連結)
  * 雖然 boundary 在這類專案的成品中是無法被看到的, 但對元件間的獨立開發與整併還是存在著極大的輔助價值
  * 元件間 boundary crossing 的設計為 lower-level component 單向依賴 high-level component 提供的 interface. 
* **Deployment Components**
  * 這階段的 boundary 切分很直覺的就是畫在動態連結的線上
* **Threads**
  * Threads 並不非架構上的 boundary 或 unit, 而是一種執行排程的策略, 可能存在於單一元件或分散於數個元件中
* **Local Processes**
  * Local processes 之間一般靠 sockets、mailboxes、message queues 之類方式溝通
  * Boundary 的畫分跟前述大同小異
* **Services**
  * 畫分的方式同上 `Lower-level services should "plug in" to higher-level services`

### Ch. 19 Policy and Level
* **Level**
* 會因為相同原因(SRP/CCP)被修改的 policies 應該被劃分進相同的 component, 而那些會因為不同理由、在不同時間或為不同層級的 policies 則應該被劃分進不同的 components
  * **Level** 的定義為 `the distance from the inputs and outputs.`, 和 IO 距離越遠的元件 level 越高

### Ch. 20 Business Rules
* Business Rule 就是那些能幫企業賺錢或省錢的程序, 以銀行來說, 借貨的利率就是一個 Business Rule, 而像這種即使不透過電腦也該被實踐的 rules 也被稱為 Critical Business Rule, 它們所使用到的資料則被稱為 Critical Business Data
* **Entities**
  * **Entity** 泛指系統中那些僅包含 Critical Business Rule 以及 Critical Business Data 的物件
* **Use Cases**
  * A use case describes **_application-specific_** business rules as opposed to the Critical Business Rules within the Entities`
  * Use case 只定義流程, 和實作無關

### Ch. 21 Screaming Architecture
* 一個好的架構必須讓使用者只需瀏覽檔案目錄時即可認知道此專案的目的為何, 而不是了解你用了什麼 Framework

### Ch. 22 The Clean Architecture
* 書中列舉了幾個設計思維(但沒解釋): Hexagonal Architecture、DCI、BCE, 並提到其共通點
  * **Independent of frameworks**
  * **Testable**
  * **Independent of the UI**
  * **Independent of the database**
  * **Independent of any external agency**
* **The Dependency Rule**
  * 架構的呈現應該是一個同心圓, 內層元件不該了解外層元件的存在, 也不該被其影響
  * 從內到外分別為
    * **Enterprise Business Rule**: Entities
      * 封裝著最關鍵的商業邏輯, 可能以不同的形式呈現 (object, set of data startures, functions)
    * **Application Business Rule**: Use Cases
      * 包含著 application-specific business rule, 利用與 entities 的交流實現
    * **Interface Adapters**: Controllers、Presenters、Gateways
      * 這層的目的主要是 Frameworks & Drivers 與 Use Cases 之間的橋梁(adapter), 負責將取得的資料轉換至以適合另一方的形式輸出 
    * **Frameworks & Drivers**: UI、Web、DB、Devices、Externam Interfaces
      * 基本上不會放過多的心思在這層 (?)
  * 依照架構的設計可以不只有四層, 但依賴關係始終為由外向內, 越往內層級越高
  * 當出現內層需要依賴外層時可套用 DIP, 在內層定義 interface 並由外層實現, 最終雙方僅需依賴內層定義的 interface
  * 每層之間傳遞的資料格式盡量保持簡單, 不要將 DB 拿回來的 raw data 直接傳遞給內層, 或是將 entities 回傳至外層

### Ch. 23 Presenters and Humble Objects
* **Humble Object pattern**
  * 將元件中不易被測試的部份分離為另一個獨立元件, 藉此讓剩下的部份可以輕易被測試, 被分離出的部份稱做 **Humble Object**
* **Presenters and Views**
  * **Presenter**: 負責將 Use Cases 回傳的資料轉換為適當形式存至 ViewModel 並交由 View 呈現
  * **View**: 由 Presenter 經由 **Humble Object pattern** 分離出的 **Humble object**, 負責資料呈現部份
* **Database Gateways**
  * Use Cases 與 Database 之間會有一層 Database Gateway, 主要是透過 interface 將 DB Query 與 Use Cases 隔離, 以確保 Use Cases 可被測試
* **Data Mappers**
  * 一般來說在架構上講 ORM 是不直覺的, 對使用者來說他們看到的是 data structure 而不是一個包著各種操作行為的 object, 所以用 Data Mapper 會更合適
* **Service Listeners**
  * 在這種狀況下 listeners 會將接收到的資料包裝成一個 data structure, 再交付給其他層做使用
* **Conclusion**
  * 在架構各層的 boundary 一般都會存在著可套用 Humble Object pattern 的元件, 適當的應用這個 pattern 可以增加元件被測試的可能性

### Ch. 24 Partial Boundaries
* 在某些情況下會在元件中預先保留可被完全分割的部份(可被獨立 compile / deploy), 以確保未來切割(如 scale up)時不需要費太多工
  * **Skip The Last Step**
    * 顧名思義, 將元件間做包含 IO 的完整的分割, 只差沒有獨立成兩個元件
    * 此舉跟直接開發兩個獨立元件所需耗費的工程基本上是相同的, 並且會因為時間關係造成部份 dependencies 跨越了 boudary, 而必須再做重新切割
  * **One-Dimensional Boundaries**
    * 讓 client 依賴 Service 提供的 interface
  * **Facades**
    * 由一個 Facade object 提供對 client 的所有接口, 封裝所有與 service 的互動

### Ch. 25 Layers and Boundaries

### Ch. 26 The Main Component

### Ch. 27 Services: Great and Small

### Ch. 28 The Test Boundary

### Ch. 29 Clean Embedded Architecture

## PART VI Details

### Ch. 30 The Databases Is a Detail

### Ch. 31 The Web Is a Detail

### Ch. 32 Frameworks Are Details

### Ch. 33 Case Study: Video Sales

### Ch. 34 The missing Chapter

