# 中鼎網站維護

- 專案為 Astro 靜態網站，npm 為套件管理工具，保留 package-lock.json。
- 修改後執行 npm run build 與 npm run verify。
- 網站以繁體中文呈現；公司聯絡資料只在 src/data/site.ts 維護。
- 藏品資料在 src/data/collection.json；圖片在 public/images。保持 slug 穩定，避免舊連結失效。
- 書封僅作出版素材，不列為獨立藏品。多視角、成對及套組資料不得直接作件數宣稱。
- 年代、材質、收藏者及歷史身分須有來源；未經核對的圖像推測不得改成確定事實。
- 本專案使用原生 HTML dialog 與少量 JavaScript；維持鍵盤操作與 reduced-motion 支援。
- 洽詢表單目前使用 mailto，沒有伺服器寄信；不可顯示已寄出或加入偽造送出成功訊息。
- 不提交金鑰、.env、node_modules、dist、私有 Drive 連結、帶權杖的下載網址或原始盤點檔。
- Cloudflare Pages 建置命令 npm run build，輸出 dist。網域與郵件 DNS 的修改須有當次明確指示。
