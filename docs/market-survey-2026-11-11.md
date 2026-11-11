# 現成 AI 用量顯示產品調查

調查日期：2026-11-11（台灣時間）。

**決策更新：使用者已決定自行開發 Mac APP 與資料擷取，只採購小螢幕。本文保留市場參考；下列 CodexBar 與現成整機建議已不屬於目前實作方向。**

目標：找已能顯示 AI 用量或工作狀態的成品，對照 AIScreenPartner 的 Mac mini + 小螢幕需求。以下是產品官網與原始專案文件調查，尚未購買或實測。售價不含未列示的運費、稅費與轉運；不把網站有購買按鈕視為已驗證台灣交付。

## 判斷

- 有完整成品硬體：codeMeter、Miblo Desk、HSNC AI Meter。
- 有現成軟體：CodexBar，可先在 Mac mini 驗證各帳號能取得的資訊。
- 有現成 APP + 韌體方案：QuotaFrame、AI Monitor；需另買指定 ESP32 硬體並燒錄，不能列為開箱即用的在售成品。
- 如保留使用者指定的自拍投屏螢幕，優先評估 CodexBar 作資料來源，再做約 4 吋的顯示介面。硬體 AirPlay 相容性仍獨立驗證，不因資料來源現成而自動成立。

## 商業成品

| 產品 | 顯示內容 | 硬體與連線 | Mac mini 關係 | 查得價格 | 台灣購買限制 |
| --- | --- | --- | --- | --- | --- |
| codeMeter | Claude Code / Codex 額度百分比、重設倒數與使用節奏；可一個 Claude + 一個 Codex，或兩個 Claude 帳號 | 2 吋、320×240、2.4GHz Wi-Fi、USB-C 或電池款；廠商列每 60 秒更新 | 廠商稱設定後可獨立運作，不需 Mac 持續執行 APP | US$119 起 | 官網有購買入口，指向 Encinitas 3D 結帳；尚未確認台灣運送、即時庫存與到貨成本 |
| Miblo Desk | Claude Code / Codex 用量限制、工作中／待回應／完成；其他多種 coding agents 的工作狀態 | 240×240；外殼 45×35×40mm；2.4GHz Wi-Fi；USB 5V/1A 供電 | Miblo Hub 支援 macOS，需主機端整合 | 巴西幣 R$149.90 | 官網明列目前只寄巴西 |
| HSNC AI Meter | 標準版為 Claude API 呼叫量與費用；客製版可洽其他 AI 指標 | LED 桌面顯示，Wi-Fi，憑證留在裝置（廠商說明） | 不依賴 macOS 顯示端，標準版需 Anthropic Admin API key | 標準 US$99；客製 US$149 | 官網稱 3 週內出貨，列美國運送資訊；台灣直送未確認 |

### codeMeter

產品：https://mydeskmeter.com/codemeter/
方案說明：https://mydeskmeter.com/codemeter/plans/
Claude + Codex：https://mydeskmeter.com/codemeter/claude-and-codex/
製造商：https://encinitas3d.com/

適合：主要關心 Claude Code 與 Codex 訂閱額度，希望不用持續執行 Mac APP。

限制：
- 是桌面小裝置，沒有查到可直接夾在螢幕邊的標準配件。
- 無實測，不將廠商的相容性、更新頻率與免訂閱說明視為已驗證結果。
- 不把訂閱方案限制、更新政策或廠商關於供應商限額規則的敘述當作 AI 供應商官方政策。
- 尚未確認台灣可交付。

### Miblo Desk

產品：https://miblo.ai/en
購買：https://miblo.ai/en/buy
支援與價格：https://miblo.ai/en/about

原廠支援表明確區分：
- Claude Code、Codex：工作狀態與 usage limits。
- Copilot CLI、Gemini CLI、OpenCode 等：工作狀態；不能因支援該工具就宣稱每種工具都有用量數字。
- claude.ai/code 等雲端工作階段不在支援範圍。
- Hub、外掛與 CLI 免費；可選 Miblo+ 遠端控制約 R$9.90/月或 R$99/年，並非基本硬體顯示必須付的訂閱。
- 頁面有明示部分圖片為示意圖，不能全部視為出貨實拍。
- 巴西以外出貨尚未開放，因此不是目前台灣採購首選。

### HSNC AI Meter

產品與購買入口：https://hsnctech.com/ai-meter/

標準版需要 Anthropic Admin API key，定位是 API 呼叫與帳單監控。它不等於 Claude Pro/Max 或 ChatGPT/Codex 訂閱額度顯示器。客製版雖有較廣泛的產品宣稱，仍需先確認指標資料來源與交付範圍，不能直接推定包含所有 AI 訂閱額度。

## 現成 Mac 軟體：CodexBar

產品：https://codexbar.app/
原始碼：https://github.com/steipete/CodexBar
下載：https://github.com/steipete/CodexBar/releases

- 免費、MIT 開源。
- macOS 14+；有 macOS APP 與 CLI。
- 支援 Codex、Claude、Cursor、Gemini、Copilot、OpenRouter 等多個來源，實際欄位依 provider 而異。
- 顯示可取得的 session / weekly / monthly windows、重設倒數、餘額與部分帳單資訊。
- 有本地 Codex / Claude 成本掃描、Usage & Spend 視圖與桌面 widgets。
- 依來源使用既有 CLI 登入、OAuth、API key 或瀏覽器 session；並非完全不需要授權。
- CLI 可供腳本與外部顯示程式呼叫，讓 AIScreenPartner 有機會省去重寫每個平台資料收集器的工作。

注意：
- Codex 配額不是 ChatGPT 所有聊天模型的總用量。
- 本地 token 成本估算、供應商 API 帳單與訂閱費應分開。
- 支援某 provider 不代表能讀出該帳號所有活動或全部精確額度。
- 現成選單與 widgets 不保證直接適配 4 吋自拍屏；小螢幕排版與 AirPlay 連線仍需驗證。
- 尚未在 George 的 Mac mini 安裝或授權任何軟體。

## 已有 APP 與韌體的替代方案

### QuotaFrame：藍牙小螢幕

網站：https://quotaframe.com/
原始碼：https://github.com/eMUQI/QuotaFrame

- Claude / Codex 百分比與重設倒數。
- 電腦端 Bridge 持續執行，透過藍牙同步到指定 ESP32 螢幕。
- 網站列 macOS 14+、Apple Silicon、需藍牙，資料來源是 CodexBar CLI。
- 需購買支援的精確硬體並燒錄韌體；不是自拍屏，也沒有在本次調查確認整機購買價格。
- 網站示範畫面明列為演示資料，不是設備實拍。
- 適合進一步評估「無線傳資料」且不必從零寫 APP 的路線；不取代使用者目前的自拍屏偏好。

### AI Monitor（tobymarks/esp32-ai-monitor）：USB 桌面顯示

原始碼：https://github.com/tobymarks/esp32-ai-monitor
下載：https://github.com/tobymarks/esp32-ai-monitor/releases

專案文件列示：
- 現成 Mac companion APP（macOS 14+，Apple Silicon / Intel）。
- 使用 CodexBar CLI，經 USB serial 傳資料給螢幕。
- 支援 ESP32-2432S028 / ESP32-2432S028R（2.8 吋 320×240）與 Guition ESP32-S3-4848S040（4 吋 480×480）。
- 有多個 provider 頁面、用量百分比、倒數、觸控切換、方向與亮度設定。
- 需另購硬體與燒錄；顯示資料走 USB，不是 Wi-Fi/AirPlay。
- 某些 plugin / session 功能標示開發中，不能當成已完成穩定版承諾。
- 這是現成的開源軟硬體方案，不是在本次調查中確認的整機商業商品。

## 對 AIScreenPartner 的建議

1. 先以 CodexBar 驗證 Mac mini 上實際使用的帳號能取得哪些指標，不必先買螢幕。
2. 仍選自拍屏時，可評估做輕量的獨立顯示視窗，優先沿用 CodexBar CLI，而不是重寫每家資料收集器。
3. 如果改求開箱即用成品，先向 codeMeter 確認台灣運送與帳號相容性。
4. 如果可接受燒錄指定硬體，QuotaFrame 或 AI Monitor 值得先試，可能省下多數開發。
5. 尚未改動既定硬體選擇、安裝 APP、連結帳號或購買商品。

## 尚待驗證

- 成品台灣運送、運費、稅與售後。
- George 實際使用的 AI 平台、帳號方案與授權來源。
- 本地登入權限、資料範圍及 provider 長期維護狀態。
- 硬體固定、持續供電、斷線恢復與更新行為。
- 小螢幕顯示的是實際額度、使用估算，還是 API 帳單。
