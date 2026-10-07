# 基金資料段落提取與查詢工具 V39.0

無 CDN、可離線使用的純前端版本。PDF.js、Mammoth、SheetJS 均已放在 `assets/vendor/`，執行時不需向外部 CDN 下載程式庫。

## GitHub Pages 部署

1. 將 ZIP 解壓縮。
2. 把解壓縮後的內容完整上傳至儲存庫根目錄。
3. 在 GitHub 開啟 `Settings` → `Pages`。
4. 將 Source 設定為 `GitHub Actions`。
5. 等待 Actions 完成後開啟網站。

詳細檢查請參閱 `GITHUB_PAGES_CHECKLIST.md`。

## 本機離線使用

建議在專案目錄啟動簡易靜態伺服器：

```bash
python -m http.server 8000
```

再開啟：

```text
http://localhost:8000
```

直接雙擊 `index.html` 時，部分瀏覽器會限制 Web Worker，因此 PDF 功能可能受到影響。

## 第三方程式庫

- PDF.js 2.11.338
- Mammoth 1.5.1
- SheetJS Community Edition 0.18.5

請依各專案授權條款使用及保留必要授權資訊。

## 整合功能分頁

- 基金資料庫：匯入、預覽、階層式查詢及匯出。
- 收支數字提取與彙總：由 DOCX 提取作業基金或政事基金收支數字並加總。
- 作業基金分析說明產生器：自動識別三種 PDF 綜計表並產生分析說明。

三個功能以同一首頁的不同分頁呈現，切換分頁時保留各分頁目前資料。

## V39.0 全面優化
- 彙總工具加入點選/拖曳、重複排除、品質分數、勾稽、逐筆刪除、Excel/JSON 匯出。
- 分析說明產生器加入前 3 頁辨識、多頁解析、檔案移除、進度、重設、複製與下載、解析 Excel、待補項目與基本勾稽。
