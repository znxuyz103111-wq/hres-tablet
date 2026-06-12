# 和仁國小　平板載具計畫文件下載專區

純靜態網頁，檔案放在 `files/`，`index.html` 以相對路徑連結，適合直接部署到 GitHub Pages。

## 資料夾結構
```
index.html          ← 下載專區網頁（資料驅動，約 14 KB）
files/              ← 所有可下載文件
  ├─ *.pdf / *.docx
  └─ 和仁國小平板文件_打包.zip   ← 「全部打包下載」用（僅 PDF）
README.md
```

## 部署到 GitHub Pages（帳號 znxuyz）
1. 建立 repo（例如 `tablet-docs`；若想要網址在根目錄，repo 命名為 `znxuyz.github.io`）。
2. 把 `index.html`、`files/`、`README.md` 上傳到 repo 根目錄。
3. Settings → Pages → Source 選「Deploy from a branch」→ 分支 `main`、資料夾 `/ (root)` → Save。
4. 約 1–2 分鐘後即可由 `https://znxuyz.github.io/tablet-docs/` 開啟。

## 如何新增一份文件（「多幾個欄位」）
只要兩步：
1. 把檔案（PDF，必要時加 Word）放進 `files/`。
2. 打開 `index.html`，在 `<script>` 裡的 `const DOCS = [ ... ]` 陣列加一筆：
```js
{
  cat: "表單下載",                       // 分類：導師必備 / 表單下載 / 校務規範 / 教室張貼 / 學生宣導
  icon: "📄",
  title: "文件名稱",
  desc: "一句話說明。",
  pdf: "檔名.pdf",                        // 對應 files/ 內的檔名
  word: "檔名.docx",                     // 可省略（沒有 Word 版就刪掉這行）
  online: "https://forms.gle/xxxx",      // 可省略（有線上表單才加）
  badges: ["iPad 專用"]                  // 可省略（要顯示右上角徽章才加）
}
```
卡片、分類數量、份數統計都會自動更新。若要新增分類，於 `const CATS = { ... }` 加一筆即可。
打包 ZIP 若想同步更新，重新把 `files/` 內的 PDF 壓成 `和仁國小平板文件_打包.zip`。

## 注意
- 「資訊組長工作手冊」含 Surface Go 密碼與廠商私人電話，**請勿**放進公開 repo。
- 「使用手冊」PDF／Word 第 10 頁含 Surface Go 密碼 12345678；若要對外公開，建議先做遮蔽版。
