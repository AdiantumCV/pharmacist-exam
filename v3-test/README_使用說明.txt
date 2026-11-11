海膽藥師中心 v3.0 測試版（2026-11-11）
========================================

本資料夾為完整靜態測試網站，不要直接開啟 index.html（file:// 不支援 fetch 題庫）。

測試版內容：
- 115 年兩次考試三科各 80 題，共 480 題；106 年藥劑學兩次考試共 160 題，合計 640 題。
- 一次只選一科，該科可選單一年份、目前全部年份或自訂年份，並選第一次／第二次／兩次。
- 模擬考、即時練習、原卷模式、智慧錯題本、收藏、考試紀錄、JSON 備份／匯入。
- Firebase Google 登入與 Firestore 寫入設定（需網路、正式 HTTPS GitHub 網域與授權網域）。
- 115 年三科示範解析 20 題，尚待專業審核；不應視為官方詳解。
- 原始試卷圖片部分為整頁截圖，需依題號對照，尚非精準單題裁切。

將網站發佈至 GitHub Pages 測試路徑：
1. 解壓縮，保留內部 index.html、app.js、questions.json、assets/ 的相對位置。
2. 進入 GitHub 儲存庫 AdiantumCV/pharmacist-exam 的 Code 頁。
3. 新增一個資料夾 v3-test/（網頁版可用 Add file → Upload files，將解壓後內容置入 v3-test 目錄；若無法建立資料夾可先上傳 v3-test/README.md 的檔案）。
4. 確認路徑為 v3-test/index.html、v3-test/app.js、v3-test/questions.json、v3-test/assets/*.png。
5. 提交 Commit 後開啟 https://adiantumcv.github.io/pharmacist-exam/v3-test/。
6. 舊版首頁 https://adiantumcv.github.io/pharmacist-exam/ 不變，原有 QR Code 不會指向 v3-test。

建議測試：
1. 訪客：選 1305 → 115 → 第一次 → 10 題；作答／交卷，看分數與解析。
2. 在藥劑學選 106、115 兩年，確認同科跨年抽題。
3. 答錯題目 → 智慧錯題本 → 再答對三次，觀察熟練度。
4. 匯出備份，使用另一瀏覽器匯入。
5. Google 登入，檢查 Firebase Authentication 使用者與 Firestore users/{uid}/state/main 是否生成；用另一台裝置登入同步。
6. 先確保 Firestore 規則發布：使用者只可讀寫 users/{uid} 及其子集合。

重要限制：
- 尚未逐題人工校對，含 115 年需要複核的圖表與公式；請不要當作正式題庫公開推廣。
- Firestore 初步採一個 state/main 文件，適合小規模測試，正式版應改成分筆紀錄／交易處理以防多裝置同時覆寫，以及避免單文件 1 MiB 限制。
- 測驗中關閉頁面會失去該次未交卷的答案；已交卷的紀錄會保留。
- Google 登入會在第一次時詢問是否合併本機訪客紀錄；進階安全與衝突測試尚未完成。
- 這個 ZIP 只是提供原始檔案，沒有自動發布或覆蓋 GitHub 線上網站。
