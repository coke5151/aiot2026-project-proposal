# Request：

[$openspec-propose](../.codex/skills/openspec-propose/SKILL.md) 請幫我設計 GUI 畫面，要包含登入登出、行事曆、每週課表、掃 QR Code 點名等功能

# Response：

我會使用 `openspec-propose` 技能來產生這次 GUI 功能的 OpenSpec 提案，先讀取技能流程與專案現有規格結構，再建立 proposal/design/tasks/spec delta。

OpenSpec CLI 可用，專案目前只有基礎 `openspec` 目錄。我會建立一個 `design-gui-screens` 變更，涵蓋登入登出、行事曆、課表與 QR Code 點名的畫面設計。

提案階段只需要定義「為什麼」與能力邊界。我會先把 GUI 分成四個新能力規格：身份驗證、行事曆、每週課表、QR Code 點名，後續 design/tasks 會依這些能力展開。

目前 `proposal` 已完成，`design` 與 `specs` 已解除封鎖。我會補上可實作的畫面架構決策，並為每個 GUI 能力建立可測試的需求情境。

我已確認專案定位是 Flutter 的 NCHU AllPass 行動 App，所以規格會以行動端 App 畫面與流程為核心，而不是桌面網站。接下來會建立五份 spec 與一份 design 文件。

`design` 與五份 `spec` 都已完成，現在只剩實作任務清單。任務會按 Flutter GUI 開發順序切分，方便之後直接進入 `/opsx:apply`。

已建立 OpenSpec 變更：`design-gui-screens`

位置：[openspec/changes/design-gui-screens](C:/Users/User/Documents/Repos/aiot2026-project-proposal/openspec/changes/design-gui-screens)

已完成的 artifacts：

- [proposal.md](C:/Users/User/Documents/Repos/aiot2026-project-proposal/openspec/changes/design-gui-screens/proposal.md)：定義 GUI 設計目的與功能範圍
- [design.md](C:/Users/User/Documents/Repos/aiot2026-project-proposal/openspec/changes/design-gui-screens/design.md)：定義 Flutter App 的登入狀態、導覽架構、行事曆、課表與 QR 點名流程設計
- `specs/`：新增 5 個能力規格
  - `gui-authentication`
  - `gui-calendar`
  - `gui-weekly-schedule`
  - `gui-qr-attendance`
  - `gui-navigation`
- [tasks.md](C:/Users/User/Documents/Repos/aiot2026-project-proposal/openspec/changes/design-gui-screens/tasks.md)：切分後續 Flutter GUI 實作任務

驗證結果：`openspec status --change design-gui-screens` 顯示 `4/4 artifacts complete`，已 ready for implementation。

接下來可以執行 `/opsx:apply`，或直接請我開始實作 GUI。