# 深圳 Maker 學習之旅

今天開始（2015.2.2）為期一週的 Maker 學習之旅。Mokoversity 八位農場計畫的夥伴們，到深圳知名的 Maker Space：Seeed Studio，進行學習之旅。

這次的旅程主題是：學習 ARM mbed 物聯網作業系統。因為大家覺得四軸飛行器是個有趣的玩具，所以決定以 ARM mbed 以及 LPC1768 開發板，共同「手作」一台土製飛行器。

使用 ARM mbed 製作四軸飛行器，應該是 ARM mbed 

## 領料

確立好主題後，大家就開始討論飛行器的規格，並且列出可能需要的零件。

![從 Seeed Studio 倉庫領取的材料](https://scontent-b-sjc.xx.fbcdn.net/hphotos-xap1/v/t1.0-9/10446647_384280548419836_8997656722491301359_n.jpg?oh=2b5015fd3cdd7960991be5ab89352350&oe=55579122)

在 Seeed Studio 工程師的幫助下，很快就拿到第一批零件。然後開始帶著「不知道會不會成功」的愉快心情，開始 Happy Making。

## 無線充電模組

這次提出的規格中，用到了一個很特別的模組：Wireless Charing Module。大家希望賦與飛行器，「自動回家充電」的能力。

![Wireless Charing Module](https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/10931390_384280568419834_6574277745703459333_n.jpg?oh=cc117c2a2b1feb2babdb2f0e715f978b&oe=556D1FDB&__gda__=1432920931_4e18517a01f41b896c99078f8cca7fde)

## Building Blocks

團隊開會討論飛行器專案時，提到 Building Blocks 會是一個極短專案（七天）的成功關鍵；簡單說明 Building Blocks 的觀念後，大家開始分頭打造自已的 Block。

Building Blocks 可以做為一個極輕量級的軟體專案管理方法，它的重點在於：每天都要有「成功的 Blocks 整合」進度。

ARM mbed 最主要的核心精神，就是 Sensor Device 封裝成 REST API 的觀念。所以這個專案最重要的 Block 就是：REST Device 的建構。

![開始展開 Building Blocks](https://fbcdn-sphotos-b-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-9/10846095_384280718419819_7489546409479898578_n.jpg?oh=e5c7aed8f15f6da6be602ad15ef4be1f&oe=55673F42&__gda__=1431963595_49195ca38cb3bdfce52058ee675ff72c)

## WiFi & Blue Tooth

飛行器的控制使用 BLE 4.0；WiFi 則是在開發階段，用來推送 Sensor Data 至 WebSocket Server。我們的專案，使用 LPC1768 開發板，開發板是 ARM Cortext-M3 MCU，以及一些主要的控制腳位，所以需要接線外接 Sensor。

使用 Seeed Studio 設計與生產的 mbed Shield 板，就可以很方便地外接需要的 Sensor。所以，我們又申請了 WiFi Shield 與 Blue Tooth Shield。

![](https://fbcdn-sphotos-f-a.akamaihd.net/hphotos-ak-prn1/v/t1.0-9/10646712_384280678419823_2718231352411837997_n.jpg?oh=4c3d9b23387b509fbfaf88ccbbfed85f&oe=5553C2C8&__gda__=1430830963_6e533fa3ef4b9fcff5e85bd27bb21995)

沒有使用 Shield 板的話，就要用麵包板與導線外接。

![](https://camo.githubusercontent.com/de78ac16ddc9583509e7754e7158a9e8faca0eef/687474703a2f2f692e696d6775722e636f6d2f496f6d354b4d452e6a7067)

## 陀螺儀

陀螺儀（Single Axis Analog Gyro 與 Grove - 3-Axis Digital Gyro）的部份，獨立成一個 Block。這個 Block 的製作一個 REST API，將 Sensor Data 推送至 WebSocket。

![](https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-9/10426561_384280598419831_8663669645142068366_n.jpg?oh=916d0f655a69d4cfa5a56852c09d4f8d&oe=5559F61A&__gda__=1431632787_b48f1be7cfc806dac32760052f2b1536)

![](https://dchtm6r471mui.cloudfront.net/hackpad.com_Ncb0ktNHpUZ_p.320451_1423112309163_%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202015-02-05%20%E4%B8%8B%E5%8D%8812.57.28.png)

## GPS

GPS 也是一個獨立的 Block。目前只是用來測試、把玩，暫時不會放在飛行器上。

![](https://fbcdn-sphotos-a-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/10940426_384280628419828_5298756888991316774_n.jpg?oh=97549e57af81b2d0497a0876114c00cc&oe=55538084&__gda__=1431403836_d1c0840ee35c42dd592fa78486d116dd)

## 通訊模塊連連看

準備就緒，開始上工。一開始要學習 LPC1786 的 Pinout，所以先使用 LPC1768 開發板，透過導線與 WiFi Shield 連接。這個時候就需要 LPC1768 的腳位卡。經過一陣連連看的遊戲後，終於將 ARM mbed 與 WiFi 接通。這個時候的通訊 Block 長像如下圖。

![](https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xpf1/v/t1.0-9/11719_384562985058259_1133189908999328747_n.jpg?oh=7cc3a384f9de6fc90c92db6a588045f6&oe=55635981&__gda__=1430828906_d7c04853614bcfb039ecd6b97f9984b2)

Bluetooth 的 Block 同樣也是，先用連連看的方式做測試。

![](https://scontent-a-sjc.xx.fbcdn.net/hphotos-xpa1/v/t1.0-9/10959573_384563008391590_5548008232315475502_n.jpg?oh=748a1c582a049d1ac94bb61b78ffeda5&oe=55537547)

其它 Sensor Block 也同時，由大家開始認領，開始進行測試，建立每一個 Block。

## 第一次的 Block 整合會議

帶著堅強攻城意志，大家很有效率地陸續完成 Block 的建設。為了實現 Web of Things 的架構，還有一些關鍵問題需要解決。

WoT 是 IoT 的 Application Layer，並且是使用 Web 技術來打造 application。也就是說，IoT + Web-enabled technologies 就是 WoT。對 WoT 來說，最重要的觀念，就是以 URL 來表示 IoT 裝置；為 IoT 加入 URL 的觀念，就是 Google 提出的 Physical Web 計畫。

雖然 WoT 都是使用目前已經存在的軟體技術，但許多觀念都要重新思考，例如：Software Architecture、Application Framework 與 Composition Layer。因此，Mokoversity 農場計畫，也做了相關的研究。

第一個實驗性質的開發專案叫 AutomationJS，這是利用 Virtual DOM 技術，來進行 UI Boundary Composition 的專案。AutomationJS 是 Mokoversity 在 WoT 方面的一個重要專案喔。

AutomationJS 是一個輕量級的 Composition Layer 實作，並且使用 Backbone 做為 Model-View 的基礎；未來也將接軌 HTML 5 的新技術標準－Shadow DOM。

有了 AutomationJS 後，差不多就解決了 WoT 的一個關鍵技術問題。第一次的 Block 整合會議內容如下：

* Block #1：Dust Sensor + WebSocket Client 
 * sockets.mbed.org
 * http://sockets.mbed.org/mbedschool/viewer
* Block #2：AutomationJS
 * Frontend
 * Backbone with Virtual DOM

整合過程遇到一些小問題，不過在即時修改程式碼後，都獲得解決了。很快地，順利完成第一次的 Block 整合會議。在網頁上，可以即時顯示空間的灰塵指數。

![](https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-9/10247473_384920171689207_2903908610409337968_n.jpg?oh=92843bfc7e20de46bcc19acca82a0be9&oe=55541D52&__gda__=1433087451_67604bc920dc5cbecb64718ed980a53c)






