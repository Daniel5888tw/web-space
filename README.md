# 中鼎文物公司網站

Astro 靜態網站，使用 CSS 與 TypeScript／JavaScript 管理視覺及互動。正式規劃網址為 https://www.heritage-art.tw/；本程式不會自動更動網域。

## 本機開發

使用 Node.js 22.22 或以上版本，建議 Node.js 22 最新修訂版，或 Node.js 24。

```bash
npm ci
npm run dev
```

開啟終端顯示的本機網址。完成修改後執行：

```bash
npm run build
npm run verify
npm run preview
```

## 維護位置

| 內容 | 檔案 |
| --- | --- |
| 公司名稱、電話、信箱、地址 | `src/data/site.ts` |
| 首頁 | `src/pages/index.astro` |
| 典藏資料與來源記載 | `src/data/collection.json` |
| 分類及搜尋 | `src/pages/collection/index.astro` |
| 藏品介紹頁模板 | `src/pages/collection/[slug].astro` |
| 服務、圖鑑、公司介紹、聯絡 | `src/pages/` 對應頁面 |
| 全站樣式、手機排版、動畫 | `src/styles/global.css` |
| 圖片 | `public/images/` |

新增藏品時，在 collection.json 加入一筆資料並使用唯一且穩定的 slug；將 WebP 圖片放到 public/images。更新 scripts/verify.mjs 的預期詳情頁數，並核對實物與圖鑑來源後再發布。

## Cloudflare Pages 連接 GitHub

1. 登入您自己的 Cloudflare 帳號，進入 Workers & Pages，建立 Pages 專案。
2. 選擇 Import an existing Git repository，連接 `Daniel5888tw/web-space`。
3. Framework preset 選 Astro；正式分支 `main`；建置命令 `npm run build`；輸出目錄 `dist`；根目錄維持 `/`。
4. 如需指定環境變數，使用 `NODE_VERSION=22`。靜態網站不需要 Cloudflare API 金鑰或 Astro Cloudflare adapter。
5. 建置成功後取得 Cloudflare 回傳的 pages.dev 網址，先檢查手機導覽、分類搜尋、藏品大圖及 mailto 洽詢。
6. 檢查完成後，才將 `www.heritage-art.tw` 加入 Custom domains，依平台指示設定 DNS。

本次不切換 heritage-art.tw。根網域與 www 的設定方法不同；根網域接到 Pages 通常需將 DNS zone 放在 Cloudflare 管理。網域註冊續費仍可留在原註冊商。先完整備份 DNS；若使用公司信箱，保留 MX、SPF、DKIM、DMARC 與驗證記錄。確認舊網址對應後再加入逐頁 301 轉址，勿猜測舊頁路徑。

## 目前功能與限制

- 6 個主要頁面、33 個典藏圖組詳情頁及 404 頁面。
- 原生分類搜尋、圖片放大、手機選單、減少動態效果偏好。
- 洽詢表單僅組合 mailto，由訪客在郵件程式自行寄出，不會在網站儲存或自動傳送資料。
- 書封、原書年代及題名依提供素材使用，沒有新增鑑定、認證或來源保證。
- Google Drive 原檔、完整盤點 Excel、收藏者個人資料與下載權杖不提交；頁面使用經優化的展示影像。
- 正式網址已在 astro.config.mjs 設定；預覽站 canonical 仍指向規劃正式網址。
- 尚未加入購物車、付款、會員或內容後台。

## 參考文件

- https://docs.astro.build/en/install-and-setup/
- https://developers.cloudflare.com/pages/framework-guides/deploy-an-astro-site/
- https://developers.cloudflare.com/pages/configuration/custom-domains/

## 圖片權利

圖片由網站擁有者提供，並非開放素材；公開儲存庫不代表授權第三人再利用。圖鑑頁面涉及出版、攝影及著作權，正式對外展示前應由公司確認相關使用權。
