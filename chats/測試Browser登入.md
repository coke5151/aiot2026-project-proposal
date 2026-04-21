User：請用 Playwright 測試開啟 Browser，並前往中興大學 CAS 登入頁。

AI：已成功開啟瀏覽器並進入登入頁，頁面正常載入，確認是中興大學 CAS 登入頁。

User：請用我提供的 browser args 重新開 Browser，然後前往同一個頁面。

AI：我建立了對應的瀏覽器啟動設定，並用這些參數重新開啟瀏覽器。

AI：已成功用指定參數開啟新的瀏覽器 session，並再次進入同一個登入頁。

User：請測試中興大學 portal 登入流程的 cookie / redirect 行為，並輸出結構化報告。登入過程由我手動完成。

AI：我準備用同一份瀏覽器啟動設定，先打開登入頁，然後等待你手動輸入帳密與完成驗證。

AI：我建立了輔助蒐集流程，目標是在你登入後整理最終頁面、cookie、redirect 與 Set-Cookie 資訊。

User：中途停止前一次執行，要求再重試一次。

AI：我先檢查目前瀏覽器 session 狀態，發現頁面已經進入登入後的 portal 畫面。

AI：我確認可以讀取目前頁面資訊，但如果要完整捕捉登入送出到成功頁的 redirect / cookie 行為，需要從未登入狀態重新開始。

User：請再重試一次。

AI：我嘗試先登出，確認回到未登入狀態，再重新打開 CAS 登入頁。

AI：我再次啟動 capture，等待你手動完成登入，以便蒐集登入後的 cookie 與 redirect 行為。

User：再次中止執行。

AI：目前已確認瀏覽器可正常開啟、指定啟動參數可用、登入流程可成功進入 portal，但完整的 cookie / redirect 結構化報告尚未成功產出，因為捕捉流程中途被中斷。