# 和仁國小　平板載具計畫文件下載專區 — 維護說明

純靜態網頁。`index.html` 以相對路徑連結 `files/` 內的文件，適合直接放到 GitHub Pages。

## 0. 資料夾結構
```
index.html        ← 下載專區網頁
files/            ← 所有可下載文件（*.pdf / *.docx）
README.md         ← 本說明
```
重點：`index.html` 要在 repo 最上層；`files` 資料夾名稱不要改，否則下載連結會失效。

## 1. 第一次部署到 GitHub Pages（電腦／瀏覽器）
1. 解壓本壓縮檔，得到 `index.html`、`files`、`README.md`。
2. github.com 登入 → 右上「+」→ New repository。
3. 取名（例如 tablet-docs），務必選 **Public** → Create repository。
   （想讓網址在根目錄就把 repo 命名為 `znxuyz.github.io`。）
4. 空 repo → Add file → Upload files → 把 `index.html`、`files` 資料夾、`README.md`
   一起拖進去 → Commit changes。
5. Settings → Pages → Source 選「Deploy from a branch」→ Branch「main」、資料夾「/(root)」→ Save。
6. 等 1～2 分鐘，重新整理該頁取得網址（如 https://znxuyz.github.io/tablet-docs/）。

若「Deploy from a branch」灰色點不動 → repo 不是 Public（Settings → General → 最下改 Public）。

## 2. 新增一份文件（兩步）
### 步驟一：把檔案放進 files/
進 repo → 點進 `files` → Add file → Upload files → 拖入新 PDF（要的話連 Word）→ Commit。
（檔名建議用底線、不要空格；中文可以。）

### 步驟二：在 index.html 加一行
回首頁 → 點 `index.html` → 右上鉛筆（Edit）→ 找到 `const DOCS = [`，
複製任一行貼成新一行改成你的文件：
```js
{"cat":"表單下載","icon":"📄","title":"文件標題","desc":"一句話說明。","pdf":"你的檔名.pdf","word":"你的檔名.docx","size":"100 KB"},
```
- `pdf` /`word` 要與 files/ 內檔名**完全一致**。
- 沒有 Word 版 → 刪 `,"word":"..."`；沒有線上表單 → 不寫 `online`；不需徽章 → 不寫 `badges`。
- `cat` 只能填：校務規範 / 導師必備 / 表單下載 / 學生宣導 / 其他。
- 該行結尾要有逗號。Commit 後等 1～2 分鐘卡片就會出現，份數自動更新。

> 新增分類：編輯 `const CATS = {...}` 照現有格式加一筆即可。

## 3. 修改或刪除文件
- 換檔：files/ 上傳同名新檔覆蓋（網頁不用改）。
- 刪除：① files/ 刪該檔；② index.html 把 DOCS 對應那行刪掉。兩者都做。

## 4. 注意事項
- 「資訊組長工作手冊」請勿放進這個公開 repo（含密碼與廠商私人電話）。
- 「使用手冊」PDF／Word 第 10 頁含 Surface Go 密碼 12345678；要正式對外公開前建議先做遮蔽版。
- GitHub Pages 為公開網站，上傳的任何檔案任何人都能下載，上傳前請再確認內容。
