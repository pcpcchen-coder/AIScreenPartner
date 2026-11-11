# 小螢幕購買比較與 USB 資料屏核查

日期：2026-11-11（台灣時間）。僅完成網頁、原廠規格與專案原始碼核查，尚未採購或實機測試。

## 目前建議

使用者希望在 Mac mini 自行開發 APP，只買小螢幕，顯示 AI 用量與文字，不想干擾主螢幕。

**優先評估 USB 資料屏作單台開發樣機**：已找到可控制圖靈／同類硬體的公開通訊實作與 Mac mini 成功案例。它不會被 macOS 當成延伸顯示器，適合定期更新數值。使用者提供的蝦皮商品價格合理，但還未確認精確品牌與硬體版本，不能宣稱該商品已相容。

如果要求一般桌面視窗直接顯示，則使用標準 USB-C / HDMI 螢幕。兩者是不同驅動路線。

## 購買比較

| 路線／產品 | 尺寸／解析度 | 連線 | 查得價格與狀態 | 採購判斷 |
| --- | --- | --- | --- | --- |
| 使用者提供的機殼 USB 監控屏 | 3.5 吋；原生解析度與硬體版本未從賣場文字確認 | 推測是 USB 資料屏，需辨認協定 | 蝦皮 NT$550–630；頁面有黑／白選項與商品數量，台中出貨；具體選項及即時庫存以結帳為準 | 低成本開發樣機候選，不是已驗證免設定商品 |
| Lilliput V4 | 3.97 吋、800×480；102.8×62×12.4mm | 原廠列 USB-C 影像輸入、Mini HDMI，macOS 相容 | DigiKey 台灣單價 NT$3,802＋另列運費 NT$1,438＝NT$5,240，可能另有進口稅費；查詢頁列現貨 95，Lilliput USA 約 1 天出貨 | 小尺寸＋標準 USB-C 的優先款，但單台進口總價高 |
| Waveshare 5inch HDMI LCD (H) V4 / 20109 | 5 吋、800×480；裸模組 | HDMI 影像＋USB 供電／觸控 | 莓亞官網 NT$1,580、頁面列 6 件庫存；露天同店 NT$1,580；iCShop NT$1,729、售完／訂貨提示 | 價格合理的標準 HDMI 備選，須做外殼與固定 |
| Waveshare 7EP-CAPLCD Monitor / 28606 | 7 吋、1280×800；172×106×10mm，鋁合金外殼 | 全功能 USB-C 影像或 HDMI | 莓亞 NT$2,758、補貨預購約 10 天；iCShop NT$3,359、售完／訂貨提示 | 想單線、可接受 7 吋才選；比最初 4～5 吋目標大 |

價格與數量是查詢頁面顯示，不保證付款時仍相同。沒有送出訂單，也未聯絡賣家。

## 可直接開啟的賣場

### 使用者提供的 USB 資料屏

https://shopee.tw/3.5吋電腦機殼螢幕-IPS-USB-C連接-電腦溫度監控-黑-白-i.14551697.27238815352

- 頁面列 NT$550–630、黑／白選項。
- 讀取到的商品說明沒有列出晶片、USB VID/PID、序號、韌體版本或原廠軟體名稱。
- 沒有足夠資料把它確定對應到 Turing、XuanFang、GUITION 等任一硬體。
- 不能因外觀相似就保證套用某個開源驅動。

另找到一個標題標示圖靈的商品（仍未驗證真實硬體）：
https://shopee.tw/圖靈螢幕-圖靈智顯3.5寸電腦機箱副屏-IPS全視角-USB-C副屏-電腦溫度監控螢幕-i.158231072.42810439259
搜尋結果列 NT$880–990、較長備貨 2～8 工作日。不能僅憑標題認定為原廠版或已適配。

### Lilliput V4

- 台灣購買入口、TWD 售價與運費：
  https://www.digikey.tw/zh/products/detail/lilliput-electronics-usa-inc/V4/27513098
- 原廠規格：
  https://www.lilliput.com/v4-product/
- 原廠規格 PDF：
  https://www.lilliput.com/uploads/V4-DM1.pdf
- 其他海外零售頁：
  https://lilliputweb.com/lilliput-v4/
  https://www.markertek.com/product/lil-v4/lilliput-v4-4-inch-vlog-and-selfie-monitor-with-usb-c-and-mini-hdmi-input-and-output

原廠列輸入 USB-C / Mini HDMI、macOS 相容及功耗不超過 2W。USB-C 應接影像來源輸入端，不能把 USB-C OUT 誤當影像輸入。標準配件列 USB-C 線與手機固定座，沒有確認含適用於主螢幕的側夾。

不同原廠資料對重量列示不一致：網站 190g；PDF 淨重 95g、毛重 185g。設計夾具前以實機或供應商確認為準。

原廠明列 macOS 比只有賣場泛稱 AirPlay 更有依據，但本專案仍未實測該 Mac mini 與線材。

### Waveshare 5inch HDMI LCD (H) V4 / 20109

- 莓亞官網：
  https://www.meiyagroup.com.tw/product/樹莓派5吋電容式觸控螢幕800x480-hdmi/
- 莓亞露天：
  https://www.ruten.com.tw/item/22140428782189/
- iCShop：
  https://www.icshop.com.tw/products/388370100011
- 原廠：
  https://www.waveshare.com/product/5inch-hdmi-lcd-h-v4.htm
- 原廠文件：
  https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4

此款不是 USB-C 單線影像螢幕。可用 Mac 的 HDMI，或 USB-C 轉 HDMI；另外供 USB 電力。商品為裸模組，需要保護與固定。附的 USB 線為 USB-A 對 Micro USB，不是 USB-C 顯示線。

依據標準 HDMI 作為顯示備選，不把原廠 Windows 觸控支援敘述套用為 macOS 觸控保證。本案不需要觸控。macOS 原生解析度、EDID、旋轉與睡眠喚醒需到貨驗收。

如 Mac HDMI 已被主螢幕占用，可另購原生影像轉接器，例如 j5create JCA153：
- 原廠：https://tw.j5create.com/products/jca153
- PChome：https://24h.pchome.com.tw/prod/DCAX3N-A9006USB1

轉接器價格未納入 NT$1,580，且不需要為此購買 USB 軟體顯卡或 DisplayLink 裝置。

### Waveshare 7EP-CAPLCD Monitor / 28606

- 莓亞：
  https://www.meiyagroup.com.tw/product/樹莓派7吋電容式觸控螢幕1280x800-ips-鋁合金外殼-hdmi-type-c/
- iCShop：
  https://www.icshop.com.tw/zh-hant/products/388370100002
- 原廠：
  https://www.waveshare.com/7ep-caplcd-monitor.htm
- 原廠文件：
  https://docs.waveshare.net/7EP-CAPLCD_Monitor/

原廠明列全功能 Type-C 顯示訊號、5V Type-C 供電、約 3W。此為以標準顯示協定評估的 Mac 備選，不宣稱原廠已單獨驗證 Mac 或 macOS 觸控。一條線供電與影像的實際穩定性需依主機埠、線材與設備驗收。

## USB 資料屏如何使用

支援的這類螢幕通常以序列／USB 裝置出現，不是 macOS 的一般顯示器。自研 APP 在 Mac 上繪製儀表板，再把像素資料與控制命令傳給螢幕。

因此預期：
- 不占原生外接顯示器名額。
- 不建立可讓滑鼠移入的延伸桌面。
- 不改變主顯示器排列或視窗位置。
- 不需要把 AI 登入憑證送給螢幕；本案只送畫面。
- 程式需常駐，仍消耗少量主機資源，實際用量需測。
- 不能直接拖一般 APP 視窗到它上面，也不能當 HDMI 螢幕。

以上只適用於已確認為這種 USB 資料屏的硬體，不把「USB-C」接頭當成分類證據。

## 有沒有公開開發依據？

有。原始專案：
https://github.com/mathoudebine/turing-smart-screen-python

硬體辨識：
https://github.com/mathoudebine/turing-smart-screen-python/wiki/Hardware-revisions

自訂程式控制介面：
https://github.com/mathoudebine/turing-smart-screen-python/wiki/Control-screen-from-your-own-code

Rev A 驅動：
https://github.com/mathoudebine/turing-smart-screen-python/blob/main/library/lcd/lcd_comm_rev_a.py

它是社群開發的非官方實作，並非原廠 SDK。文件列可自訂圖片、文字、進度條、方向與亮度，足以作本案顯示傳輸設計的研究依據。仍依使用者決定自行開發 APP／用量擷取，不安裝原廠整套監控 APP 或外部 AI 用量服務。

相似外觀有不同協定，文件也列出尚不支援的 Waveshare USB-Monitor、GUITION 等產品；不能混用。

## macOS 已知問題與成功案例

來源：
https://github.com/mathoudebine/turing-smart-screen-python/issues/7

主線 README 仍標示 macOS major bug，issue 仍開啟，不能只引用「支援 macOS」就保證穩定。

但 2026-08-21 有使用者回報 Mac mini M4 + Turing / UsbMonitor 3.5 吋 Rev A 成功，裝置識別為 VID/PID 1a86:5722、序號 USB35INCHIPSV2。其做法是避開 macOS 一般串列路徑，以直接 USB bulk 傳輸，分開送命令與影像並控制傳輸邊界。這是社群使用者的實機回報，不是本專案測試，也不是所有韌體批次的保證。

該回報連到的參考實作：
https://gist.github.com/amarok30/cddaa9a9818d6830a74d9332f501047e

本次未能直接擷取 gist 內容，因此不將它列為已完成程式碼審查的依賴。

## 到貨驗收（待執行）

1. 記錄精確硬體版本、USB VID/PID、產品名、序號與接口。
2. USB 資料屏先辨認協定，再測單色、漸層、中文、數字、計數器與連續多幀，避免純色能亮就誤判成功。
3. Mac 傳輸測試包括直接 USB 與適用的序列路徑；Rev A 著重已知花屏原因，不任意對不明裝置送寫入命令。
4. 文字用 Mac 本地字型先光柵化；顯示端不需原生中文字庫。
5. 先以 5～15 秒更新目標資訊，連續 8 小時無花屏與中斷；此為目標不是實測速度。
6. 拔插、睡眠喚醒、程式退出後能重新初始化，失敗時主螢幕與鍵鼠仍正常。
7. 確認實際閱讀距離，再決定 3.5 吋是否足夠；先放 2～3 個主要數字，其餘輪播。
