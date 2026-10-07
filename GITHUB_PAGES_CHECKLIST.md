# GitHub Pages 部署檢查清單

## 一、上傳前

- [ ] 儲存庫根目錄存在 `index.html`
- [ ] 根目錄存在空白檔案 `.nojekyll`
- [ ] `assets/vendor/` 內有以下 4 個檔案：
  - [ ] `pdf.min.js`
  - [ ] `pdf.worker.min.js`
  - [ ] `mammoth.browser.min.js`
  - [ ] `xlsx.full.min.js`
- [ ] `assets/vendor/cmaps/` 與 `assets/vendor/standard_fonts/` 兩個資料夾完整上傳
- [ ] 保留 `.github/workflows/pages.yml`
- [ ] 不要只上傳 `index.html`，否則 PDF、DOCX、Excel 功能會失效
- [ ] 不要把未公開或敏感 JSON 放進公開儲存庫

## 二、GitHub 設定

- [ ] 預設分支名稱為 `main`
- [ ] 進入 `Settings` → `Pages`
- [ ] `Build and deployment` → `Source` 選擇 `GitHub Actions`
- [ ] 到 `Actions` 頁面確認 `Deploy static site to Pages` 顯示綠色勾勾
- [ ] 到 `Settings` → `Pages` 點選 `Visit site`

## 三、部署後功能檢查

- [ ] 首頁可以正常開啟，沒有 404
- [ ] 三個主分頁均可開啟：基金資料庫、收支數字提取與彙總、作業基金分析說明產生器
- [ ] 瀏覽器開發者工具 Console 沒有紅色錯誤
- [ ] Network 中 4 個 `assets/vendor/*.js` 都是 HTTP 200
- [ ] 匯入測試 JSON 可顯示基金筆數及年度
- [ ] 第一筆基金可以預覽
- [ ] 年度、基金、大標題、中標題、小標題篩選正常
- [ ] 關鍵字搜尋及反白正常
- [ ] JSON 匯出正常
- [ ] Excel 匯出正常
- [ ] 基金資料庫分頁的 DOCX 匯入正常
- [ ] 收支數字提取與彙總分頁可選基金類型並拖曳多個 DOCX
- [ ] 作業基金分析說明產生器可識別收支餘絀表、餘絀撥補表及現金流量表
- [ ] 文字型 PDF 匯入正常
- [ ] 掃描型 PDF 會提示先進行 OCR
- [ ] 重新整理頁面後仍能載入首頁
- [ ] 手機版頁面沒有橫向溢出主介面

## 四、離線測試

- [ ] 先完整下載或解壓縮整個專案
- [ ] 中斷網路後，以本機靜態伺服器開啟
- [ ] 不建議直接雙擊 `index.html` 測試 PDF Worker
- [ ] 可在專案資料夾執行 `python -m http.server 8000`
- [ ] 開啟 `http://localhost:8000`
- [ ] 在斷網狀態完成 JSON、PDF、DOCX 匯入及 Excel 匯出

## 五、常見錯誤

### 首頁 404

確認 `index.html` 位於部署來源最上層，而不是多包一層資料夾。

### PDF.js 本機程式庫載入失敗

確認 `assets/vendor/pdf.min.js` 與 `assets/vendor/pdf.worker.min.js` 已上傳，大小不是 0 KB，檔名大小寫完全相同。

### DOCX 無法匯入

確認 `assets/vendor/mammoth.browser.min.js` 已上傳；舊式 `.doc` 不支援，請先另存成 `.docx`。

### Excel 無法匯出

確認 `assets/vendor/xlsx.full.min.js` 已上傳。

### GitHub Actions 部署失敗

確認 Pages 的來源設定為 `GitHub Actions`，工作流程具有 `pages: write` 與 `id-token: write` 權限。

## V39.0 新增測試
- [ ] 彙總工具可排除相同檔案重複匯入
- [ ] 未識別金額顯示「未識別」而不是 0
- [ ] 單筆刪除後合計會重算
- [ ] 彙總 Excel 及 JSON 可下載
- [ ] 分析產生器可解析多頁 PDF
- [ ] 三種 PDF 可逐一移除及全部重設
- [ ] 純文字複製、TXT、HTML、解析 Excel 可用
- [ ] 勾稽及待補項目分頁可顯示結果
