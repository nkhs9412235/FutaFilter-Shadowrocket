# FutaFilter-Shadowrocket
FutaFilter optimized for Shadowrocket on iOS
# FutaFilter Shadowrocket 2026

FutaFilter 的 Shadowrocket 專用 Module。

本專案以 FutaFilter 原始 Surge 規則為基礎，針對 Shadowrocket 進行語法整理、相容性修正與 MITM 範圍整理。

## ✨ Features

* LINE 廣告封鎖
* Dcard 廣告／追蹤相關請求封鎖
* 漫畫人／漫畫社廣告 API 封鎖
* 4Gamers 廣告請求封鎖
* PTT 相關追蹤請求封鎖
* Pixnet 彈窗相關請求封鎖
* Poke Genie 必要網域直連
* 常見廣告／追蹤服務封鎖
* 支援 Shadowrocket Module
* MITM 使用 `%APPEND%`，避免覆蓋其他 Module
* 盡可能縮小 MITM hostname 範圍
* 不包含 VIP 解鎖或其他付費功能破解

---

## 📌 Current Version

**Version:** 2026.08.09

**Base:** FutaFilter `v20231207.01`

**Target:** Shadowrocket on iOS

**File:**

`FutaFilter-Shadowrocket.sgmodule`

---

## 📥 Installation

### Method 1 — Remote Module

在 Shadowrocket：

```text
首頁
→ 模組
→ 右上角 +
→ 輸入 Module URL
→ 下載
→ 啟用
```

Module URL：

```text
https://raw.githubusercontent.com/你的GitHub帳號/FutaFilter-Shadowrocket/main/FutaFilter-Shadowrocket.sgmodule
```

請把：

```text
你的GitHub帳號
```

替換成自己的 GitHub 使用者名稱。

---

## 🔐 HTTPS MITM

本 Module 包含 URL-REGEX 規則。

部分規則需要 Shadowrocket HTTPS 解密才能完整工作。

如果只使用：

* DOMAIN
* DOMAIN-SUFFIX
* DOMAIN-KEYWORD

則不需要 MITM。

如果需要 LINE、Dcard、漫畫人等 URL-REGEX 規則完整運作，請在 Shadowrocket 啟用 HTTPS 解密。

### Shadowrocket

```text
配置
→ 點目前使用的配置旁邊的 ⓘ
→ HTTPS 解密
→ 生成新的 CA 證書
→ 安裝證書
```

然後到 iOS：

```text
設定
→ 一般
→ 關於本機
→ 證書信任設定
→ 開啟 Shadowrocket Root CA
```

請只對自己信任的 Module 啟用 MITM。

---

## 🧩 Rule Categories

### LINE

主要處理：

* 廣告 API
* 廣告媒體
* 廣告資料
* LINE News
* OA 相關請求

### Dcard

處理：

* `bilanx.dcard.tw`

### 漫畫人 / 漫畫社

處理：

* 廣告 API
* Promotion API
* 廣告相關網域
* `applog.uc.cn`

### 其他

包含：

* 4Gamers
* PTT
* Pixnet
* Poke Genie
* LINE TV
* Bugsnag
* vpon
* 常見廣告／追蹤服務

---

## ⚠️ 誤殺與相容性

本專案採取「寧可少封，也不要大量誤殺」的策略。

因此不會單純把大型廣告清單全部合併進來。

大型廣告清單雖然可以增加封鎖數量，但也可能：

* 造成 App 功能異常
* 阻擋正常 API
* 造成登入問題
* 造成圖片或影片無法載入
* 增加 MITM 範圍
* 增加規則維護成本

如果發現某個 App 功能異常，建議先停用本 Module 進行測試。

---

## 🔄 Version History

### 2026.08.09

* 建立 Shadowrocket 專用版本
* 保留 FutaFilter 原始規則
* 修正漫畫人／漫畫社 `DOMAIN-SUFFIX` 語法
* 整理 MITM hostname
* 使用 `%APPEND%`
* 整理規則分類
* 避免加入未驗證的第三方廣告網域
* 以 Shadowrocket Module 為主要使用方式

### 2023.12.07.01

Original FutaFilter release.

---

## 📚 Rule Sources

本專案主要基於：

* FutaFilter
* Shadowrocket Module / Surge Module 格式
* 公開廣告封鎖規則研究
* Shadowrocket 社群維護中的規則專案

參考專案：

* FutaFilter
* blackmatrix7/ios_rule_script
* uxudjs/Shadowrocket
* Johnshall/Shadowrocket-ADBlock-Rules-Forever
* LingJingMaster/Shadowrocket-Rules

第三方專案的規則與授權仍歸原作者所有。

---

## 🛠️ Maintenance Policy

本專案不追求規則數量。

新增規則前，優先確認：

1. 是否確實與廣告或追蹤有關
2. 是否可能影響正常功能
3. 是否可以使用 DOMAIN / DOMAIN-SUFFIX 取代 MITM
4. URL-REGEX 是否真的需要 HTTPS 解密
5. 是否已經存在相同規則
6. 是否有可靠的公開來源可以交叉驗證

不因「看起來像廣告網域」就直接加入。

---

## 📮 Issue

如果發現：

* 廣告沒有被阻擋
* App 功能異常
* 網站無法正常載入
* 規則誤殺
* 新的廣告 API

可以建立 GitHub Issue。

建議提供：

```text
App / Website:
iOS Version:
Shadowrocket Version:

問題描述：

相關網域：

相關 URL：

是否開啟 MITM：
Yes / No
```

請不要公開：

* 個人帳號
* 密碼
* Token
* Cookie
* VPN 訂閱網址
* 私人 IP

---

## 📄 License

本專案主要為個人研究與 Shadowrocket 規則整理用途。

第三方規則、網域資料及原始專案之著作權與授權仍歸各原作者所有。

使用本專案前，請自行確認相關規則的授權條款。

---

## ⭐ Disclaimer

本專案不保證所有 App、網站及未來版本均可正常運作。

App 更新後可能改變 API、網域或請求格式，因此規則可能需要更新。

請自行判斷是否適合你的使用環境。
