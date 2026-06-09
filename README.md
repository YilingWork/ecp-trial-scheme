# 試辦方案專家審議平台——部署與維護說明

這個資料夾是一個**可直接上線的網站**，只有三個檔案：

| 檔案 | 用途 |
|---|---|
| `index.html` | 網站主體（含全部內容、折疊、密碼閘） |
| `robots.txt` | 擋 Google／Bing 等搜尋引擎收錄 |
| `README.md` | 本說明（不會顯示在網站上） |

---

## 一、第一次上線（GitHub Pages）

> 全程在 GitHub 網頁操作，不需用指令。

1. 登入 GitHub → 右上「＋」→ **New repository**。
2. Repository name 填 `ecp-trial-scheme`（或你喜歡的名字）；可見性選 **Public**（免費 Pages 的條件，內容靠密碼＋noindex 保護）；按 **Create repository**。
3. 進入新 repo → **Add file → Upload files** → 把本資料夾的 `index.html` 與 `robots.txt` **拖進去** → **Commit changes**。
4. repo 上方 **Settings → Pages** → Source 選「**Deploy from a branch**」→ Branch 選 **main**、資料夾 **/(root)** → **Save**。
5. 等 1–2 分鐘，重新整理該頁，會出現網址：
   `https://<你的帳號>.github.io/ecp-trial-scheme/`
6. 開網址測試 → 輸入密碼 **ECP2026** → 應能看到內容。
7. 把網址私下貼給專家委員（建議連同密碼，但分開兩封訊息傳）。

---

## 二、每場會議後更新（你的日常流程）

1. 跟 AI 說：「**把第 X 場決議更新上網頁**」＋決議內容。
2. AI 會改好 `index.html`（該章狀態改 ✅ 已定案、填入決議區塊、更新紀錄加一列）。
3. 你到 GitHub repo → 點 `index.html` → 右上鉛筆 ✏️ **Edit** →（或直接 Upload files 覆蓋）→ 貼上新內容 → **Commit**。
4. 約 1 分鐘後網站自動更新。專家看「更新紀錄」就知道何時改了什麼。

> 最省事做法：每次都請 AI 給你**整份新的 index.html**，你用 Upload files 直接覆蓋舊檔即可。

---

## 三、更換密碼

預設密碼是 `ECP2026`。要改成自己的密碼：

1. 請 AI：「把網頁密碼改成 `你的新密碼`」，AI 會算出新的 SHA-256 並換掉 `index.html` 裡的 `HASH`。
2. 或自己算：把新密碼用 SHA-256 雜湊（可用線上工具），取代 `index.html` 中這一行的字串：
   `const HASH = "....";`

⚠️ **密碼保護是「弱保護」**：能擋一般路人與搜尋引擎，但懂技術者檢視原始碼可能繞過。它的定位是「避免意外曝光」，**不適合機密等級內容**。若需真正權限控管，改用 Cloudflare Access（免費、email 登入）。

---

## 四、本機預覽

直接用瀏覽器打開 `index.html`（雙擊即可）就能預覽，不必上線。
