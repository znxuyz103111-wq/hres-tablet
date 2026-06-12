# 和仁國小　平板載具計畫文件下載專區 — 維護說明

這是一個純靜態網頁。`index.html` 用相對路徑連結 `files/` 資料夾裡的文件，
適合直接放到 GitHub Pages。本文件包含：部署、新增文件、重建打包 ZIP、修改/刪除、注意事項。

---

## 0. 資料夾結構
```
index.html                         ← 下載專區網頁（約 15 KB）
files/                             ← 所有可下載文件都放這裡（*.pdf / *.docx）
lib/jszip.min.js                   ←「全部打包下載」用的程式庫（一起上傳、勿刪）
README.md                          ← 本說明
```
重點：`index.html` 一定要在 repo 最上層；`files` 資料夾名稱不要改，
否則網頁上的下載連結會失效。

---

## 1. 第一次部署到 GitHub Pages（電腦／瀏覽器）

1. 解壓本壓縮檔，得到 `index.html`、`files`、`README.md`。
2. 開 github.com 登入帳號 → 右上「+」→ New repository。
3. 取名（例如 `tablet-docs`），**務必選 Public（公開）** → Create repository。
   - 若想網址在根目錄（znxuyz.github.io），repo 就命名為 `znxuyz.github.io`。
4. 空 repo 頁 → Add file → Upload files → 把 `index.html`、`files` 資料夾、`lib` 資料夾、
   `README.md` 一起拖進去 → Commit changes。
5. 上方 Settings → 左欄 Pages → Build and deployment：
   Source 選「Deploy from a branch」→ Branch 選「main」、資料夾「/(root)」→ Save。
6. 等 1～2 分鐘，重新整理該頁，最上方會出現網址
   （如 https://znxuyz.github.io/tablet-docs/），打開即完成。

若「Deploy from a branch」是灰色點不動 → repo 不是 Public。
到 Settings → General → 最下 Danger Zone 改為 Public。

---

## 2. 新增一份文件（兩步）

### 步驟一：把檔案放進 files/
- 進 repo → 點進 `files` 資料夾 → Add file → Upload files →
  拖入新的 PDF（要的話連 Word 一起）→ Commit changes。
- 檔名建議用底線、不要有空格（中文可以）。

### 步驟二：在 index.html 加一行讓卡片出現
- 回 repo 首頁 → 點 `index.html` → 右上鉛筆圖示（Edit）。
- 找到 `const DOCS = [`，每一行就是一份文件。複製任一行貼成新的一行，改成你的文件：
```js
{"cat":"表單下載","icon":"📄","title":"文件標題","desc":"一句話說明。","pdf":"你的檔名.pdf","word":"你的檔名.docx","size":"100 KB"},
```
- `pdf` /`word` 要與 files/ 內檔名**完全一致**。
- 沒有 Word 版 → 刪掉 `,"word":"..."`；沒有線上表單 → 不要加 `online`；
  不需徽章 → 不要加 `badges`（要的話寫 `"badges":["iPad 專用"]`）。
- `cat` 只能填：校務規範 / 導師必備 / 表單下載 / 學生宣導 / 其他。
- 該行結尾要有逗號。
- Commit changes，等 1～2 分鐘卡片就會出現，份數統計自動更新。

> 想新增整個分類：編輯 `index.html` 的 `const CATS = {...}`，照現有格式加一筆。

---

## 3.「全部打包下載」ZIP（自動，不用維護）

打包功能已改為**自動**：使用者按下「全部打包下載（ZIP）」時，網頁會即時抓取
目前清單中的所有 PDF、在瀏覽器內壓成一個 ZIP 下載。
所以你**新增文件後不必做任何事**，新檔會自動被納入打包。

唯一要注意：`lib/jszip.min.js` 是打包用的程式庫，請確保它一起上傳、不要刪除或改名。

## 4. 修改或刪除文件

- **換檔（內容更新）**：進 files/ → 上傳同名新檔覆蓋即可（網頁不用改）。
- **刪文件**：① 在 files/ 把該檔刪掉（點檔案 → 右上垃圾桶 → Commit）；
  ② 編輯 index.html，把 DOCS 裡對應那一行刪掉 → Commit。
- 改完都等 1～2 分鐘讓 Pages 重新部署。

---

## 5. 注意事項（重要）

- **「資訊組長工作手冊」請勿放進這個公開 repo**：內含 Surface Go 密碼與廠商私人電話。
- **「使用手冊」PDF／Word 第 10 頁含 Surface Go 密碼 12345678**：
  目前分檔後一樣可被公開下載；若要正式對外公開，建議先做遮蔽版再放上來。
- GitHub Pages 為公開網站；放上去的任何檔案任何人都能下載，上傳前請再確認內容。
