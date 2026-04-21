# Flutter Mac 建立無簽名 IPA

## Turn 1

### 👤 User

flutter 要怎麼用 mac 建立無簽名的 .ipa 檔？

### 🤖 Assistant

在 Mac 上使用 Flutter 建立無簽名（Unsigned）的 `.ipa` 檔案，最簡單的方式是先透過 Flutter 指令編譯出無簽名的 `.app` 檔案，然後手動將其打包成 `.ipa` 格式。
以下是完整的步驟與終端機（Terminal）指令：

### 第一步：編譯無簽名的 iOS 應用程式
在你的 Flutter 專案根目錄下，開啟終端機並執行以下指令。`--no-codesign` 參數會告訴 Xcode 在編譯時跳過程式碼簽署階段。

```bash
flutter build ios --release --no-codesign

```
編譯完成後，Flutter 會在 `build/ios/iphoneos/` 目錄下產生一個名為 `Runner.app` 的檔案。

---

### 第二步：手動打包成 .ipa 檔案
`.ipa` 檔案本質上只是一個包含了特定資料夾結構（名為 `Payload`）的壓縮檔。你可以繼續在終端機中執行以下指令來完成打包：
**1. 建立一個名為 Payload 的資料夾：**

```bash
mkdir -p Payload

```
**2. 將剛才編譯好的 Runner.app 複製到 Payload 資料夾中：**

```bash
cp -r build/ios/iphoneos/Runner.app Payload/

```
**3. 將 Payload 資料夾壓縮，並將副檔名指定為 .ipa：**

```bash
zip -r my_app.ipa Payload

```
**4. 刪除暫存的 Payload 資料夾（保持環境整潔）：**

```bash
rm -rf Payload

```
完成上述步驟後，你的專案根目錄下就會多出一個 `my_app.ipa`，這就是你需要的無簽名 `.ipa` 檔。

---

### ⚠️ 重要注意事項

- **無法直接安裝：** 無簽名的 `.ipa` 檔案**無法**直接安裝在一般的 iOS 設備上。iOS 系統會拒絕執行未經 Apple 信任憑證簽署的應用程式。
- **適用情境：** 這種無簽名的 `.ipa` 通常用於以下幾種情況：
  - 提供給越獄（Jailbroken）的設備安裝。
  - 搭配 TrollStore 等工具進行安裝。
  - 準備交由第三方簽名工具（如 AltStore、Sideloadly、iOS App Signer 或企業級簽名服務）進行後續的重新簽名（Re-signing）。

## Turn 2

### 👤 User

所以我可以借圖書館的 iMac build 一個無簽名的 .ipa，帶回家用 AltStore 自己簽名 .ipa 檔安裝到手機上對吧

### 🤖 Assistant

**完全正確！** 你的邏輯非常通，這確實是沒有專屬 Mac 的開發者（或不想花錢買蘋果開發者帳號的人）常常使用的一種「聰明解法」。
你可以將在圖書館 iMac 上編譯好的無簽名 `.ipa` 檔，透過隨身碟或雲端硬碟帶回家，然後用你家裡的電腦（不管是 Windows 還是 Mac）透過 **AltStore** 或 **Sideloadly** 這類工具，輸入你自己的普通 Apple ID 進行免費簽名，最後成功安裝到你的 iPhone 上。
不過，在執行這個完美計畫之前，有幾個**現實面的小提醒**需要稍微留意一下：

### 1. 圖書館 iMac 的環境與權限
這是你計畫中最容易卡關的地方：

- **軟體有沒有安裝？** Flutter 和 Xcode 的體積非常龐大。如果圖書館的 iMac 沒有預先安裝這兩套軟體，你可能會因為沒有「管理員密碼（Admin Password）」而無法自行下載安裝。
- **終端機（Terminal）權限：** 有些公共電腦會鎖定終端機功能，導致你無法下達 `flutter build` 的指令。建議先去圖書館確認一下那台電腦的開放程度。

### 2. 免費 Apple ID 簽名的「七天限制」
使用 AltStore 搭配一般免費的 Apple ID 來簽名，**憑證的有效期限只有 7 天**。

- 這意味著每隔 7 天，你就必須讓手機和安裝了 AltServer 的電腦連上同一個 Wi-Fi，重新刷新（Refresh）一次 App。如果過期了，App 就會閃退打不開，需要重新連接電腦簽名才能繼續使用（資料不會不見，只是暫時打不開）。

### 3. iOS 16 以上需要開啟「開發者模式」
如果你的 iPhone 系統是 iOS 16 或更新版本，在透過 AltStore 安裝完 App 後，第一次點擊 App 時會跳出「未受信任的開發者」或提示需要開發者模式。

- 你需要到手機的 **「設定」>「隱私權與安全性」> 滑到最下方開啟「開發者模式」**，並重新開機後才能順利執行你的 App。

### 4. 數量限制
免費的 Apple ID 帳號，最多只能在設備上同時安裝 **3 個**自己簽名的 App（其中 AltStore 本身就會佔用掉 1 個名額，所以你實際上只能再裝 2 個自己的 App）。

---
**總結來說：**
只要圖書館的電腦環境允許你順利編譯出那個 `Payload` 壓縮而成的無簽名 `.ipa`，你後續「帶回家用 AltStore 自己簽名安裝」的思路是完全可行且 100% 正確的！祝你編譯順利！

## Turn 3

### 👤 User

那需要準備什麼 icon 之類的才能做出能安裝的 ipa 嗎？沒準備好會不會做出 .ipa 檔了但安裝失敗滿其實是壞的檔案？

### 🤖 Assistant

**不用擔心！你「不需要」特地準備 icon，也不會因為沒準備 icon 就做出壞掉或無法安裝的 .ipa 檔。**
當你使用 `flutter create` 建立專案時，Flutter 其實已經默默幫你準備好一套預設的 App 圖示（白底藍色的 Flutter 標誌）以及簡單的啟動畫面（Launch Screen）了。
系統（iOS）和簽名工具（AltStore）真正在乎的是「應用程式的資料結構正不正確」以及「簽名憑證有沒有效」，它們完全不在乎你的 App 圖示長什麼樣子。如果你什麼都不設定直接編譯，你的 App 安裝到手機上後，就會顯示那個預設的 Flutter logo，而且能夠正常執行。

---

### 為了確保你在圖書館不會做白工，這才是你真正要檢查的 3 件事：
既然你擔心帶回家的 `.ipa` 檔會是壞的，以下這幾點才是真正會影響安裝成敗的關鍵（只要這三點沒問題，你的 `.ipa` 就是健康的）：
**1. 編譯過程沒有報錯 (Error)**
只要你在終端機執行 `flutter build ios --release --no-codesign` 時，最後順利跑完並提示成功（沒有出現紅色的 Error 中斷流程），順利產生了 `Runner.app`，那就代表這個檔案在結構上是 100% 沒問題的。
**2. Bundle Identifier (App 的身分證號碼)**
每個 iOS App 都需要一個獨一無二的識別碼。通常 Flutter 預設會幫你設定成 `com.example.你的專案名稱`。

- **重點：** AltStore 在幫你免費簽名時，會註冊這個 Bundle ID。只要你沒有在裡面使用奇怪的符號（只能用英文、數字和句點），用預設的 `com.example.xxx` 帶回家給 AltStore 簽名是完全可以成功安裝的。
**3. 你沒有手動把 Info.plist 搞壞**
iOS App 讀取設定的核心檔案是 `ios/Runner/Info.plist`。只要你沒有自己進去亂刪除裡面的標籤（像是 App 版本號、App 名稱等），維持 Flutter 的預設狀態，打包出來的東西絕對是好的。

---

### 💡 補充小建議：如果你還是想放自己的 Icon 怎麼辦？
如果你不想看到預設的 Flutter logo，強烈建議你**不要**去圖書館開 Xcode 手動慢慢拉圖示（太浪費時間了）。
你可以在家裡先用 **flutter_launcher_icons** 這個方便的套件：

1. 在家裡把你的圖示（一張 1024x1024 的 PNG 圖片即可）放進專案資料夾。
2. 在 `pubspec.yaml` 裡設定好這個套件。
3. 到圖書館時，在跑 `flutter build` 之前，先在終端機執行一行指令（例如 `dart run flutter_launcher_icons`），它就會瞬間幫你把 iOS 需要的所有尺寸圖示自動裁切並替換好。
**結論：**
放寬心！只要你的程式碼沒有 Bug，編譯指令能順利跑完，那個用 `Payload` 資料夾壓縮出來的 `.ipa` 檔帶回家就一定能用 AltStore 簽名並安裝。祝你去圖書館的「編譯任務」一切順利！

---

*Exported from [Voyager](https://github.com/Nagi-ovo/gemini-voyager)*  
*Generated on April 21, 2026 at 11:27 PM*