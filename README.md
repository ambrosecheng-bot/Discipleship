# 與主同行 · 尋寶之旅　Apprentices of Jesus — The Disciple's Map

> 一個單檔、零相依的門徒旅程網站：以「藏寶圖」為首頁，帶領人從**初遇**走到**差遣倍增**，沿途尋見那藏在地裡的至寶。
>
> A single-file, dependency-free website that frames discipleship as a nine-stage treasure map — from a first encounter to becoming a disciple-maker.

「凡你手所當作的事，要盡力去作。」— 傳道書 9:10

**專案位置　Repository:** <https://github.com/ambrosecheng-bot/Discipleship>
**線上網站　Live (GitHub Pages):** <https://ambrosecheng-bot.github.io/Discipleship/>
*（啟用 Pages 後生效，見下方「部署」一節。）*

---

## 簡介　Overview

**與主同行 · 尋寶之旅** 是為在英港人移民（HK immigrants in the UK）而設計的門徒旅程網站。它把跟隨耶穌的歷程，化為一張羊皮紙藏寶圖上的**九站旅程**：每一站提供一項「恩典的管道」，由人親自支取運用，把自己帶到下一個狀態——而這一站的「到」，正是下一站的「從」。

設計守住三條原則：

- **基督是主角，不是更好的自己。** 終點的至寶是天國／基督（太 13:44），不是自我實現。
- **搭橋後離橋。** 旅程的比喻只是進入聖經的橋樑，不取代真實的關係門徒造就。
- **工具服事葡萄樹。** 純展示與導覽，**不含表單、評分或配對**。

整個網站是**一個 HTML 檔**，無建置步驟、無框架，只在執行時透過 CDN 載入 Google Fonts。

---

## 九站一覽　The Nine Stations

| # | 站　Station | 標題　Title | English | 分期　Phase |
|---|------|------|---------|------|
| 1 | 初遇 | 路上相遇 | A Meeting on the Road | 鬆土期 Tilling |
| 2 | 見證 | 看見改變 | Changed Lives | 鬆土期 Tilling |
| 3 | 共鳴 | 與我有關 | Closer to Home | 鬆土期 Tilling |
| 4 | 探問 | 親自查證 | See for Yourself | 鬆土期 Tilling |
| 5 | 同讀 | 結伴同讀 | Reading Together | 入門期 Entering |
| 6 | 初嚐主恩 | 親嚐主恩 | Taste and See | 入門期 Entering |
| 7 | 委身 | 立志跟隨 | Choosing to Follow | 入門期 Entering |
| 8 | 造就 | 基督成形 | Christ Formed in You | 成全與倍增 Forming & Sending |
| 9 | 差遣與倍增 | 差遣倍增 | Sent to Multiply | 成全與倍增 Forming & Sending |

每一站頁面包含：紅蠟印站號、四字標題與英文、一句核心、「**從 → 恩典管道 → 到**」的轉化鏈、經文、為何，以及上一站／回地圖／下一站導航與進度標示。第 1 站另附「細看這一站」雙軌散文（耶穌怎樣做 ‖ 在英港人怎樣走）。

---

## 部署到 GitHub Pages　Deploy

1. 進入本專案 repo：<https://github.com/ambrosecheng-bot/Discipleship>。
2. 把 `disciple-map-site.html` **改名為 `index.html`**，連同 `README.md` 一起放在 repo 根目錄。
3. 前往 **Settings → Pages**，在 **Build and deployment → Source** 選 `Deploy from a branch`，分支選 `main`、資料夾選 `/ (root)`，按 **Save**。
4. 等約 1 分鐘，網站會發佈於 **<https://ambrosecheng-bot.github.io/Discipleship/>**。

> 本機預覽：直接用瀏覽器開啟 `index.html` 即可，無需伺服器。

---

## 檔案結構　Files

```
.
├── index.html        # 主網站（由 disciple-map-site.html 改名而來）
└── README.md
```

主網站之外，本專案開發過程亦產出數個**獨立元件檔**（選用，非部署所需）：

| 檔案 | 用途 |
|------|------|
| `disciple-map-site.html` | ⭐ 完整單檔網站（首頁＋九站，建議用作 `index.html`） |
| `hero-section-disciple-map.html` | 藏寶圖 hero 區塊（獨立版） |
| `discipleship-journey.html` | 深藍章節風的九站旅程頁（獨立版） |

如只部署主網站，可只保留 `index.html`。

---

## 技術說明　Technical Notes

- **單檔、零相依**：所有 HTML／CSS／JS 內嵌於一個檔案；外部僅有 Google Fonts（Cinzel、Noto Serif TC、Noto Sans TC）。
- **手繪地圖**：藏寶圖以 inline SVG 繪製（足跡虛線、九站圖釘、羅盤、羊皮紙做舊濾鏡），縮放清晰、無點陣圖。
- **頁內路由**：以 JavaScript 攔截 `#` 錨點點擊切換頁面，並以 `history.replaceState` 同步網址——可同時在 GitHub Pages 與沙箱式預覽器（如各種 iframe 嵌入）中正常運作，不會觸發整頁重載。
- **響應式**：桌面為「標題疊在地圖上」，手機自動改為「標題在上、地圖在下」堆疊，九站全部可見。
- **無障礙**：里程碑與導覽可鍵盤操作、具 `aria-label`；尊重 `prefers-reduced-motion`。
- **無追蹤、無表單、無第三方腳本。**

---

## 客製化　Customisation

所有內容集中在主檔 `<script>` 中的 `STATIONS` 陣列，修改即更新地圖與九個分頁：

```js
{ n:1, name:"初遇", title:"路上相遇", en:"A Meeting on the Road", phase:"tilling",
  x:130, y:558, lx:0, ly:-32, anchor:"middle",
  one:"門徒之路由關係起步，不由論證起步。",
  from:"從未把福音當作與自己有關的人",
  means:"一位門徒真誠的友誼與生命接觸。",
  to:"知道世上有一條「與主同行」的活法，值得一探",
  ref:"約 1:39、46", verse:"「你來看。」",
  why:"人先信任傳遞者，才聽得進信息。" }
```

- **改文字**：編輯 `title / en / one / from / means / to / ref / verse / why`。
- **改地圖位置**：`x, y` 為里程碑座標（viewBox `1200 × 760`）；`lx, ly, anchor` 為標籤偏移與對齊。
- **加「細看這一站」散文**：參考第 1 站的 `ESSAY_ST1` 寫法，於模板中以 `${s.n===N ? ESSAY_STN : ""}` 注入。
- **改配色／字體**：調整 `:root` 的 CSS 變數（`--paper`、`--ink`、`--ochre`、`--seal`、字體變數等）。

---

## 授權　License

- **程式碼（HTML／CSS／JS 結構）**：採 [MIT License](https://opensource.org/licenses/MIT)，歡迎自由取用與修改。
- **文字、散文與神學內容**：© Ambrose Cheng（鄭君成），**保留版權**。歡迎個人與教會在非商業的門徒造就場景中使用與分享，但請勿在未經授權下作商業用途或修改後再發佈。

> 建議另建一個 `LICENSE` 檔放置 MIT 全文（程式碼部分）。如需，我可另外為你產生。

---

## 致謝與異象　Vision

本專案服事「**一個影響一個**（One Influencing One）」的門徒倍增異象——門徒的終點，是成為另一個人的起點。

*Soli Deo Gloria.*
