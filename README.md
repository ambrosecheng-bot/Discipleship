# 與主同行 · Apprentices of Jesus

> **大使命門徒協作平台** — A discipleship platform for the Hong Kong immigrant community in the UK

[![GitHub Pages](https://img.shields.io/badge/Hosted%20on-GitHub%20Pages-181717?logo=github)](https://ambrosecheng-bot.github.io/Apprentics-Jesus/)
[![Language](https://img.shields.io/badge/Languages-繁中%20%7C%20简中%20%7C%20EN-C17D2A)](https://ambrosecheng-bot.github.io/Apprentics-Jesus/)
[![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey)](LICENSE)
[![Founding Church](https://img.shields.io/badge/Founding%20Church-SCCC%20Southampton-2A4A5C)](https://www.cocm.org.uk)

---

## 簡介 Overview

「與主同行」是一個為**英國香港 BNO 移民基督徒**而建的免費開放門訓平台。

核心理念是 **一個影響一個（One Influencing One）**——每一位跟隨耶穌的門徒，都可以成為下一個人的同行者。平台以修咸頓（Southampton）為起點，服務漢普郡、英國，乃至普天之下的華人門徒。

This is a free, open discipleship platform built for **Hong Kong BNO immigrants in the UK**, grounded in the Great Commission and the philosophy of **One Influencing One** — every disciple can become a discipler. Based in Southampton, serving Hampshire, the UK, and the global Chinese diaspora.

---

## 主要功能 Features

### 🚪 訪客入口系統 Visitor Journey System
- **四類訪客識別**：探索者 · 尋道者 · 新門徒 · 同行者
- 每類訪客對應個性化路徑，無需宗教背景即可進入
- 手風琴式九站旅程展開，漸進引導

### 🗺️ 九站門徒旅程 Nine-Station Discipleship Journey
| 站次 | 名稱 |
|------|------|
| S1 | 在黑暗中遇見光 |
| S2 | 來，跟從我 |
| S3 | 捨，才能得 |
| S4 | 在路上學習 |
| S5 | 幽谷中的功課 |
| S6 | 從內而外的翻轉 |
| S7 | 愛的群落 |
| S8 | 帶著使命出發 |
| S9 | 終點即起點 |

### 📖 聖經知識庫 Bible Knowledge Base
- 全文搜索支援
- 章節導覽
- 適合個人查考及小組研習

### 🤝 門訓資源庫 Discipleship Resource Library
- 文章 · 影片 · 書籍 · 工具 · 外部連結
- 四類受眾標籤篩選：初信者 · 受訓門徒 · 門訓者 · 教會領袖
- 持續更新

### 🌐 三語切換 Trilingual Support
- 繁體中文（預設）
- 簡體中文
- English

---

## 技術架構 Technical Architecture

```
與主同行/
│
├── index.html          # 完整單頁應用（All-in-one SPA）
│   ├── <style>         # 內嵌 CSS（CSS variables, responsive grid）
│   ├── <body>          # 頁面結構
│   │   ├── nav         # 黏性導覽列 + 三語切換
│   │   ├── .hero       # Hero Banner（Ken Burns 動效）
│   │   ├── .hero-doors # 四扇訪客入口門
│   │   ├── .hero-panel # 九站旅程手風琴面板
│   │   ├── .testimonials-section  # 見証語錄
│   │   ├── .community-section     # 社群邀請
│   │   ├── .journey-section       # 門徒旅程詳覽
│   │   ├── .cta-banner            # 底部行動橫幅
│   │   └── footer
│   └── <script>        # 內嵌 JS（i18n, 資源渲染, 旅程邏輯）
│
└── README.md
```

**技術選擇 Tech Stack**

| 項目 | 選擇 | 原因 |
|------|------|------|
| 架構 | 單一 HTML 檔案 | 零依賴部署，任何靜態主機均可運行 |
| 字型 | Noto Serif TC / Noto Sans TC / IM Fell English | 支援繁簡中文及英文 |
| 圖示 | Tabler Icons（CDN） | 輕量開源圖示庫 |
| 動效 | Pure CSS（Ken Burns, transitions） | 無 JavaScript 動效依賴 |
| 主機 | GitHub Pages | 免費、可靠、版本控制整合 |
| i18n | 內建 JS 物件（`data-i18n` 屬性） | 無需外部 i18n 框架 |

---

## 快速部署 Quick Deploy

### 方法一：Fork 此儲存庫（推薦）

```bash
# 1. Fork 此 repo 至你的 GitHub 帳號
# 2. 進入 Settings → Pages → Source: Deploy from branch → main → / (root)
# 3. 儲存後約 60 秒，網站即上線
```

### 方法二：本地克隆

```bash
git clone https://github.com/ambrosecheng-bot/Apprentics-Jesus.git
cd Apprentics-Jesus

# 直接用瀏覽器開啟（無需本地伺服器）
open index.html

# 或使用 VS Code Live Server / Python 本地伺服器
python3 -m http.server 8080
# 然後訪問 http://localhost:8080
```

### 方法三：自訂部署至其他靜態主機

本項目為純靜態單頁應用，可部署至任何靜態主機：

- **Netlify**：拖放 `index.html` 至 Netlify Drop
- **Vercel**：`vercel --prod`
- **Cloudflare Pages**：連接 GitHub repo，自動部署

---

## 本地化指引 Localisation Guide

如需為你所在地區的華人社群建立自己的版本，請修改以下部分：

### 1. 地理定位（Hero Eyebrow）
```html
<!-- index.html 第 ~1901 行 -->
<p class="hero-eyebrow" data-i18n="eyebrow">修咸頓 · 漢普郡 · 英國 · 普天之下</p>
```
將「修咸頓 · 漢普郡 · 英國」替換為你所在城市及地區。

### 2. 聚會資訊（Meeting Info Bar）
搜尋 `meeting-bar`，更新聚會時間、地點及聯絡方式。

### 3. CTA 連結
搜尋 `javascript:void(0)`，替換為你的實際 WhatsApp 連結、Google Form 或聯絡郵件：
```html
<!-- 替換前 -->
<a href="javascript:void(0)" class="hero-primary-cta">來見見我們 →</a>

<!-- 替換後（WhatsApp 示例） -->
<a href="https://wa.me/447700000000" class="hero-primary-cta" target="_blank">來見見我們 →</a>
```

### 4. 三語文字內容
所有翻譯文字集中於 `<script>` 區塊的 `i18n` 物件內，結構如下：
```javascript
const i18n = {
  zh_hant: { eyebrow: "修咸頓 · ...", h1: "在異鄉，你不需要一個人扛", ... },
  zh_hans: { eyebrow: "修咸顿 · ...", h1: "在异乡，你不需要一个人扛", ... },
  en:      { eyebrow: "Southampton · ...", h1: "In a foreign land, you don't have to carry it alone", ... }
};
```

---

## 貢獻指引 Contributing

歡迎以下形式的貢獻：

- **內容貢獻**：補充門訓資源（文章、書籍、工具推薦）→ 提交 Issue 或 PR，修改 `resourcesData` 陣列
- **翻譯改善**：修正或補充三語翻譯 → 修改 `i18n` 物件
- **Bug 回報**：在 Issues 頁面描述問題及重現步驟
- **功能建議**：在 Discussions 分享你的想法

### PR 規範

```
類型: 簡短描述（繁體中文或英文均可）

例：
content: 新增《門徒的代價》書籍至資源庫
fix: 修復手機版導覽列顯示問題
i18n: 更新英文版 Hero 副標題
```

---

## 發起教會 Founding Church

本平台由 **Southampton Chinese Christian Church（SCCC，修咸頓中國基督教會）** 發起，附屬於 **海外華人基督教使命（COCM）** 旗下。

SCCC 是本平台的創始夥伴，但平台的異象和資源服務全球所有華人門訓社群，不限於任何單一教會。

> The platform was initiated by SCCC but is open to the global Chinese discipleship community. Any church or ministry is welcome to fork, adapt, and deploy their own version.

---

## 授權 License

本項目內容採用 [Creative Commons BY-NC 4.0](LICENSE) 授權：

- ✅ 可自由分享及改編
- ✅ 須署名原作者
- ❌ 不可用於商業用途

聖經引文版權歸各版本出版機構所有。

---

## 聯絡 Contact

- **平台網址**：[ambrosecheng-bot.github.io/Apprentics-Jesus](https://ambrosecheng-bot.github.io/Apprentics-Jesus/)
- **發起教會**：[SCCC · Southampton Chinese Christian Church](https://www.cocm.org.uk)
- **Issues / PR**：歡迎直接在本 repo 提交

---

<p align="center">
  <em>一個影響一個 · One Influencing One</em><br>
  <small>提摩太後書 2:2 · 2 Timothy 2:2</small>
</p>
