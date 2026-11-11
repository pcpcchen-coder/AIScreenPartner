# MiraScreen 開發介面與 Mac mini 相容性核查

日期：2026-11-11（台灣時間）。

## 結論

**目前不能確認賣場的 MiraScreen 3.97 吋磁吸自拍屏能接通 George 的 Mac mini 並提供獨立儀表板畫面。暫不建議以已相容為前提採購。**

目前只完成公開文件核查，沒有取得這款實機，也沒有該型號在目標 Mac 上的測試紀錄。這個結論是「缺少驗證」，不是「已證明不相容」。

## 證據與界線

| 問題 | 查得內容 | 判定 |
| --- | --- | --- |
| 是否有官方公開 SDK？ | 檢索官方網站、下載、支援頁，未找到可取得的顯示 SDK、開發 API 文件或範例 | 未找到；不能據此斷言廠商完全沒有商務 SDK |
| 能直接送文字或 JSON 讓它顯示嗎？ | 未找到這款硬體的 HTTP / WebSocket / BLE 顯示資料介面或協定 | 不可作為已具備功能設計 |
| 一般 MiraScreen 接收器支援 Mac 嗎？ | 官網 MacBook Air 教學列「Connect your Mac to MiraScreen's WiFi」「Turn on AirPlay」 | 有一般 Mac 投屏教學，但沒有證明這款自拍屏 |
| 3.97 吋自拍屏呢？ | 賣場列 AirPlay / Miracast、800×480，使用平台主要列 iOS / Android | 沒有該型號的 Mac 延伸顯示證據 |
| 能確認精確型號／韌體嗎？ | 已查頁面不足以把此自拍屏對應至原廠接收方案與特定韌體 | 尚未確認 |
| 能邊充邊顯示、長時間常亮嗎？ | 沒有取得這款型號的明確手冊或測試紀錄 | 尚未確認 |
| APP 能否自動配對、斷線重連？ | 沒有取得此產品的公開控制介面與測試紀錄 | 不承諾 |

EZMira / EZCastLite 是成品投屏 APP，不等於可供本專案呼叫的公開 SDK。其他公司的 AirPlay SDK 或自行實作的 AirPlay 接收程式，也不能當作此自拍屏的開發介面。

官網一般接收器、HDMI dongle 與賣場同名自拍屏之間，尚未建立精確型號與韌體的對應。不能僅依名稱推定是同一套硬體或接收實作。

## 我們的 APP 是否一定需要 MiraScreen SDK？

**如果 macOS 能把硬體接成可獨立使用的延伸顯示器，就不需要 MiraScreen SDK。**

實作分兩層：

1. **連線層**：由 macOS AirPlay 與接收器完成裝置發現、配對、傳輸與建立顯示輸出；目前這款硬體還沒有通過驗證。
2. **顯示層**：自研 APP 使用 AppKit 的 NSScreen 取得已存在的顯示器資訊，並把自己的儀表板視窗放到選定螢幕上。

NSScreen 是取得可用顯示器資訊的 Apple API，並不能用來證明 AirPlay 配對成功、替裝置補上缺少的協定，或保證自動重連。

如果裝置只能接收手機畫面，或只能鏡像整個主畫面且沒有可驗證的獨立視窗投放途徑，就不能照上述方案滿足「主螢幕正常工作、小螢幕獨立顯示資訊」的需求。

## 接通驗證必須取得的證據

以下是待執行的條件，目前全部沒有實機結果。

1. **硬體身分**：精確產品型號、韌體版本、包裝或背標照片。
2. **環境**：測試 Mac 型號、macOS 版本、網路接法。
3. **發現與配對**：macOS 控制中心的螢幕鏡像列表可找到它，並成功顯示畫面。
4. **獨立輸出**：顯示器設定可用延伸模式；或有實測可用的獨立視窗投放方式。需要主螢幕和自拍屏同時呈現不同畫面的證據。
5. **自研 APP 顯示**：將測試視窗送到該輸出，正確顯示中文、大數字、時間與持續變動的計數器，無自拍鏡像翻轉與裁切。
6. **持續上網**：Mac 投屏時仍可連網取得所需 AI 資料。
7. **供電與常駐**：接電顯示 8 小時，記錄睡眠、斷線與發熱等狀況。
8. **恢復**：斷電、斷網、Mac 睡眠喚醒後，分別記錄重新連線步驟與能否自動恢復。

賣家若提供測試，也應是相同型號與可辨識的 Mac 環境；手機投屏影片不足以取代以上驗證。

## 專案決策

- MiraScreen 3.97 吋從「優先候選」改列「未通過相容性驗證，暫不建議採購」。
- 使用者仍採自行開發 APP、只買顯示硬體的方向。
- 尚未安裝任何廠商 APP、傳送帳號憑證、購買商品或聯絡外部廠商。
- 下一個能改變此判定的證據是精確型號的 Mac 連線／延伸顯示測試，而不是更多泛稱 AirPlay 支援的廣告。

## 公開來源

- MiraScreen MacBook Air 教學：https://mirascreen.com/pages/macbook-air
- MiraScreen 下載頁：https://mirascreen.com/pages/download
- MiraScreen 使用者手冊入口：https://mirascreen.com/blogs/support
- MiraScreen 產品列表（核查時沒有列出產品）：https://mirascreen.com/collections/wireless-display
- 3.97 吋自拍屏商品規格：https://www.etmall.com.tw/i/7882228
- Apple NSScreen：https://developer.apple.com/documentation/appkit/nsscreen
- Apple NSScreen Markdown 文件：https://developer.apple.com/documentation/appkit/nsscreen.md
- Apple 多顯示器說明：https://support.apple.com/guide/mac-help/extend-mirror-mac-desktop-multiple-displays-mchlb5f905a1/27/mac/27
