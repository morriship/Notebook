---
description: 'ISBN-13: 9780134494166'
---

# Clean Architecture

Test content

### Ch. 16  Independence 

* **Operation**
  * 架構的設計對 operation 的影響很大, 例: scale up
* **Development**
  * 當一個系統需要分變多個不同的團隊開發時, 必須拆成數個各自獨立的元件再分派給各團隊, 以避免在開發時團隊間~~互相傷害~~多餘的溝通成本
* **Deployment**

  * 一個好的架構應該可在建置完成後立即被佈署, 而不需要依賴一堆雜亂的設置檔  \(這裡具體來說應該是指不該具有高度的環境依賴, 像是在佈署階段要執行一堆 scripts 去做環境建置\)

* **Leaving options open**
  * 反正要達成上面三項超難的, 尤其像在初始階段連需求基本都還不明確,  所以期望的是銘記以上原則並讓架構盡量有彈性



