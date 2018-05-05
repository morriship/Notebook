---
description: 'ISBN-13: 9780134494166'
---

# Clean Architecture

### 

### Programming Prardigms

* **Structured Programming**
* **Object-Oriented Programming**
* **Functional Programming**

### **Design Principles**

* **SRP: Singple Responsibility Principle**
  * 元件只該因為一個\(唯一的\)理由而被更動
* **OCP: Open-Closed Principle**
  * 讓功能容易被新增, 同時避免既有的組件被修改
* **LSP: Liskov Substitution Principle**
* **ISP: Interface Segregation Principle**
* **DIP: Dependency Inversion Principle**
  * 元件之間的應該依賴抽像化的 policy, 而不該是直接依賴 \(高耦合\)

### Component Principle

* **Component Cohesion**
  * **Reuse/Release Equivalence Principle**
  * **Common Closure Principle**
  * **Common Reuse Principle**
* **Component Coupling**
  * **Acyclic Dependencies Principle**
  * **Stable Dependencies Principle**
  * **Stable Abstractions Principle**

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
    * 減少各 Use Case 之間的耦合
  * **Decoupling Mode**
    * 增加每層 Service 之間的獨立性
* **Independence**
  * **Independent develop-abillity**
    * 當各元件之間具有獨立性時, 開發將能減少 team 之間的溝通頻率
  * **Independent deployability**
    * 架構設計足夠好的 project 甚至能對各元件與服務做 hot-swapping



