---
timezone: UTC+8
---

# Ian Mackenzie

**GitHub ID:** IanMackenzie0909

**Telegram:** @Newt_Scamender

## Self-introduction

AI x Web3 School

## Notes

<!-- Content_START -->
# 2026-05-22
<!-- DAILY_CHECKIN_2026-05-22_START -->
## 1\. Smart Account：錢包變成「可程式化帳戶」

ERC-4337 最核心的改變是：  
使用者不再只能用 **EOA 私鑰帳戶**，而是可以用 **合約錢包 Smart Account**。

代表錢包可以內建：

-   社交恢復
    
-   多簽
    
-   Passkey / 生物辨識
    
-   Session key 臨時授權
    
-   批次交易
    
-   權限控管
    
-   模組化功能擴充
    

Take away：

> **Smart Account 讓錢包從「一把私鑰」變成「可寫邏輯的使用者帳戶」。**

* * *

## 2\. UserOperation + Bundler + EntryPoint：新的交易流程

ERC-4337 不是讓使用者直接送一般交易，而是改成送出：

> **UserOperation = 使用者想讓智能帳戶執行的操作請求**

流程變成：

```
UserOperation
→ Bundler 收集與模擬
→ EntryPoint 統一驗證
→ Smart Account 執行操作
```

其中：

-   **Bundler** 負責收集、模擬、打包 UserOperation。
    
-   **EntryPoint** 是鏈上的統一入口，負責驗證、執行、結算 gas。
    
-   **Smart Account** 則決定這筆操作是否合法。
    

Take away：

> **ERC-4337 把「直接送交易」改成「送 UserOperation，由 Bundler 打包，再交給 EntryPoint 統一處理」。**

* * *

## 3\. Paymaster：讓使用者不一定要自己付 ETH gas

Paymaster 是 ERC-4337 改善使用者體驗的關鍵，讓：

-   使用者沒有 ETH 也能操作
    
-   dApp 幫新手補貼 gas
    
-   使用 ERC-20 token 支付 gas
    
-   特定活動、白名單、訂閱用戶享有 gas sponsor
    

Paymaster 卻也是安全風險最高的部分，因為它本質上是在**替別人付錢**，所以必須有：

-   quota
    
-   deadline
    
-   nonce
    
-   防重放
    
-   rate limit
    
-   deposit / stake
    
-   風控與監控
    

Take away：

> **Paymaster 解決的是「誰來付 gas」的問題，讓 Web3 體驗更接近一般 App。**

### 智能帳戶的目的，是在不改變區塊鏈去中心化帳本本質的前提下，把原本難用、慢感強、需要多次簽名與 gas 操作的 Web3 交易流程，抽象成更接近 Web2 App 的使用體驗。

智能帳戶 (Notion)：[https://rainy-cry-c97.notion.site/3687c68bd87f81e3bf12d2e29a00d03c?source=copy\_link](https://rainy-cry-c97.notion.site/3687c68bd87f81e3bf12d2e29a00d03c?source=copy_link)
<!-- DAILY_CHECKIN_2026-05-22_END -->

# 2026-05-21
<!-- DAILY_CHECKIN_2026-05-21_START -->

# 私鑰的意義：**揭開個人主權的序幕**

## 隨機創建 → 立即擁有

# 區塊鏈網路運行

一筆交易從發起到完成，需經歷完整的生命周期：**Wallet**（簽名）→ **RPC/Node**（傳播）→ **Mempool**（排隊等待）→ **Builder/Validator**（挑選打包）→ **Block**（寫入區塊）→ **Explorer**（公開可查）。

### Web3 關鍵特性

| 特性 | 說明 |
| --- | --- |
| 去中心化 | 錢包創建高度去中心化；交易廣播與 RPC 入口存在中心化風險；節點與客戶端越分散越安全 |
| 無許可 | 任何人都可讀寫網路，寫入只需支付 Gas |
| 抗審查 | 節點全球分布，錢包、前端、RPC 皆可替換 |
| 開放開源 | 客戶端開源，交易記錄公開可查，透明且可審計 |
| 隱私（演進中） | 現為公開帳本加偽匿名，地址可被關聯分析；ZK 等隱私方案仍在持續發展 |

### **Web3 就是用私鑰簽名證明你的身份，用共識網路保證帳本可信，用智能合約讓規則自動執行。**
<!-- DAILY_CHECKIN_2026-05-21_END -->

# 2026-05-20
<!-- DAILY_CHECKIN_2026-05-20_START -->


（先聽我嘮叨會：前兩天一直不知道去哪打卡🥹一直在任務區裡翻找，找了個寂寞🤣。今天終於發現要在哪點到了😭我是不是快被淘汰了🥲）

# 1\. Web3 的本質是「讀、寫、擁有」

**Web1 是讀，Web2 是讀寫，Web3 則多了 Own 的權利，也就是擁有權。**

重點不是都搬到鏈上，是讓使用者透過錢包、「Token」　、「NFT」　、「DAO」　、鏈上身份，自己掌握數位資產與部分網路的權力。

# 2\. Web3 開發是將後端重新拆分

Web3 的前端仍然很像傳統 Web2，但後端一部分會變成：

**_智能合約 + 錢包 + RPC + Indexer + 去中心化儲存 + Oracle_**

也就是說，Web3 開發者不只要會寫網頁，還要理解哪些邏輯該放在鏈上，哪些資料與服務還是要走鏈下。

# 3\. Web3 最大價值是降低對中心平台的依賴，但代價是複雜度與安全風險

**Web3 帶來去中心化、無需許可、原生支付與可驗證規則，但也伴隨：**

-   使用門檻高
    
-   Gas 成本
    
-   智能合約不可隨便修
    
-   私鑰遺失無法救回
    
-   合約漏洞可能直接造成資產損失
    

所以 Web3 不是比較潮的 Web2，而是**一種把所有權、信任與資產邏輯重新設計的架構**。

有興趣的朋友可以看一下我整理的 Notion Page: [Web3 開發概述](https://rainy-cry-c97.notion.site/Web3-3667c68bd87f81969166c839f3cfa0d2)

English version: [Web3 Development Overview](https://rainy-cry-c97.notion.site/Web3-Development-Overview-3667c68bd87f81ee8db5d3369f0f8e24)
<!-- DAILY_CHECKIN_2026-05-20_END -->
<!-- Content_END -->
