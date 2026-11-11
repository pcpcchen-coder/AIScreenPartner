# AIScreenPartner

將市售磁吸無線自拍小螢幕夾在主螢幕旁，由自行開發的 APP 顯示 AI 用量、數字、文字與工作狀態。

## 目前方向（2026-11-11）

- 使用者指定沿用附件那類「自拍無線投屏小螢幕」。
- APP 負責資料取得與畫面繪製，小螢幕負責接收投屏畫面。
- 已確認 APP 執行端：**Mac mini / macOS**。Mac 晶片型號與 macOS 版本尚未確認，不影響目前將 AirPlay 列為優先查證方向。
- 硬體不必能安裝 APP、開網頁或刷機；重點是能接收執行端傳來的儀表板畫面。
- ESP32 方案保留為備選，取消先前的優先推薦。
- 目前完成需求與候選調查，尚未採購、實機驗證或實作 APP。

## 運作方式

1. APP 或同主機的資料收集服務取得各 AI 可用的用量與狀態。
2. APP 產生適合約 4 吋螢幕的大字體、數值卡片與簡單圖形。
3. 透過相容的系統投屏功能傳送畫面到自拍小螢幕。
4. 小螢幕接電常駐，固定於主螢幕側邊。

這條路線傳的是影像。一般不能把任意 JSON、文字或藍牙資料直接傳給自拍屏就期待它自行排版；目前沒有確認任何候選提供這種開發介面。APP 也不假設能安裝在螢幕裡。

優先驗證「延伸顯示」：APP 在小螢幕全螢幕呈現，主螢幕繼續正常使用。若硬體僅能鏡像整個主畫面，就不符合此目標，除非另有已驗證的獨立視窗投放方式。不能僅因標示支援手機鏡像就宣稱支援電腦延伸顯示。

## Mac mini 連線與 APP 方案

- 優先使用 macOS 內建 AirPlay 螢幕鏡像功能，目標是將自拍屏用作獨立延伸顯示器。
- 第一次連線由使用者在 macOS 控制中心選擇裝置；成功後在顯示器設定確認延伸模式。實際選單依 macOS 版本與接收器能力而異。
- APP 初步可採 SwiftUI / AppKit，在選定顯示器呈現無邊框儀表板；這是待實作方案。
- APP 可處理偵測顯示器、視窗定位、文字排版、資料更新；自動配對與斷線後無人值守重連尚未驗證，不先承諾。
- 接收器若必須讓 Mac 加入自身熱點，還需驗證同時上網；若能加入既有區域網路，需確認能與 Mac 相互發現。目前沒有確認候選支援哪種模式。
- 無線畫面仍需連續傳送，不能因只顯示少量文字就宣稱不耗串流資源；實際 CPU、網路與穩定性待測。
- USB 用於常駐供電；候選能否邊充邊顯示與關閉休眠仍需確認。

Apple 文件說明 macOS 的延伸、鏡像與 AirPlay 能力；MiraScreen 官網亦泛稱支援 Mac，但兩者都不能證明賣場這款 3.97 吋自拍屏已與本專案的 Mac mini 相容。

## 第一輪候選

### MiraScreen 磁吸無線投影自拍螢幕（3.97 吋、AirPlay）

- 賣場列示 800×480、磁吸、AirPlay 與 Miracast。
- 神腦生活頁面列 NT$1,399，查詢時顯示「補貨中」；不能視為現貨。
- iOPEN Mall / Wooo 3C 頁面列 NT$1,790、預購與預計 14 天出貨；該擷取內容可能較舊，需向賣家重新確認。
- 價格、庫存與交期以賣家即時確認或結帳為準。
- 商品頁主要說明手機使用，尚無這個型號在本專案電腦上的連線證據。
- 精確型號、電腦延伸顯示、邊充邊用、自動休眠與斷線重連仍需確認。
- 狀態：優先查證候選，尚未定案採購。

購買頁：https://online.senao.com.tw/Mart/1392503
備選賣場：https://mall.iopenmall.tw/056151/index.php?action=product_detail&prod_no=P5615113719001
規格參考：https://www.etmall.com.tw/i/7882228

### 附件約 NT$600–863 的白牌自拍屏

價格來自使用者附件，不是已確認的即時報價。附件不足以辨識每款型號與協定版本，不能依外觀直接定案。

選擇條件：

- 約 4 吋，原生解析度以 800×480 或 480×800 為優先。
- 明確列出所需投屏協定，並能證實與指定執行端配對。
- 能以獨立畫面呈現儀表板，不影響主螢幕工作。
- 可接電連續顯示，沒有不可關閉的自動休眠。
- 能調整方向、關閉自拍鏡像翻轉，文字可正常閱讀。
- 斷線恢復與開機配對流程可接受。
- 「4K / 8K」行銷字樣不能代替面板原生解析度。

## APP 初版畫面目標

- 平台名稱、工作中／完成／錯誤。
- 可取得的今日用量、API 費用、額度與重設時間。
- 每頁少量大字卡片，可輪播。
- 顯示資料更新時間與連線狀態。
- 訂閱額度、API 帳單、本地執行紀錄分開；未取得資料顯示「未知」。
- 各 AI 資料來源仍需調查，不能承諾全部平台都有精確剩餘額度。

## 採購前與到貨驗收

1. 已確認 Mac mini；採購前仍須確認精確自拍屏型號與 macOS 相容性。
2. 確認從該主機投放獨立儀表板的可行路徑。
3. 接電連續顯示 8 小時，不因靜止畫面而休眠。
4. 網路中斷再恢復後能重新連線；記錄需不需要人工操作。
5. 主螢幕正常工作，自拍屏只呈現儀表板。
6. 50–70 cm 距離可讀文字，無鏡像翻轉或明顯裁切。
7. 確認尺寸、重量與供電線方向，再設計側掛夾具。

以上為待執行標準，並非已完成測試。

## 參考文件

- Windows 無線投影與延伸模式：https://support.microsoft.com/en-us/windows/hardware/display-graphics/screen-mirroring-and-projecting-to-your-pc-or-wireless-display
- Windows Miracast 支援檢查：https://support.microsoft.com/en-us/windows/hardware/display-graphics/fix-connections-to-wireless-displays-or-docks-in-windows
- Mac 延伸、鏡像與 AirPlay 顯示：https://support.apple.com/guide/mac-help/extend-mirror-mac-desktop-multiple-displays-mchlb5f905a1/27/mac/27
- MiraScreen 候選：https://online.senao.com.tw/Mart/1392503
- 候選規格：https://www.etmall.com.tw/i/7882228
- MiraScreen 一般無線接收器功能（非該自拍屏的相容性證據）：https://mirascreen.com/pages/wireless-display-key-features
- ESP32 備選原廠資料：https://docs.waveshare.com/ESP32-S3-Touch-LCD-4.3B
