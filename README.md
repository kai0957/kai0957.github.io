# OnWorks (`onworks.cc`) 主站部署清單

本專案是專為 GitHub 帳號 `kai0957` 建立的主網域網站，建議上傳至公開倉庫 `kai0957.github.io`。

## 1. 上傳到 GitHub
1. 在 GitHub（`https://github.com/kai0957`）建立名為 `kai0957.github.io` 的 **Public** 倉庫。
2. 將本資料夾內的所有檔案上傳並推送到 `main` 分支。
3. 進到倉庫 **Settings → Pages**：
   - Source 選擇 **Deploy from a branch** → `main` / `/ (root)`。
   - **Custom domain** 填入 `onworks.cc` 並按 **Save**。

## 2. 設定 Cloudflare DNS（onworks.cc）
到 Cloudflare DNS → Records 新增以下紀錄（**全部維持灰色雲朵 DNS only**）：
- 4 筆 `A` 紀錄，Name 填 `@`：
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`
- 1 筆 `CNAME` 紀錄，Name 填 `www`，Target 填 `kai0957.github.io`。
- 各工具子網域各新增 1 筆 `CNAME` 紀錄（例如 Name 填 `tool1`，Target 填 `kai0957.github.io`）。

等待約 5～15 分鐘後，回 GitHub Pages 勾選 **Enforce HTTPS**。

## 3. 連結你既有的工具子網域
子網域可正常開啟後，打開 `index.html`，參考註解範例把你的子網域工具卡片加進首頁 `#tools` 區塊，讓訪客與 Google 爬蟲都能直接從主頁連過去。

## 4. 提交 Search Console 與申請 Google AdSense
1. 先到 Google Search Console 驗證網域 `onworks.cc`（將 TXT 紀錄貼進 Cloudflare），並提交 `https://onworks.cc/sitemap.xml`。
2. 再註冊 Google AdSense 並填入 `https://onworks.cc`：
   - 把 AdSense 提供的 `<script>` 貼到 `index.html` 的 `<head>` 區段。
   - 把你的 Publisher ID 寫進 `ads.txt`（格式：`google.com, pub-你的ID, DIRECT, f08c47fec0942fa0`）。
3. 推送更新並確認瀏覽器可開啟 `https://onworks.cc/ads.txt` 後，回 AdSense 後台按「要求審核」。
