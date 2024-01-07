↑
→
W3C
EPUB 3.3
W3C編輯草稿 06 December 2022

更多關於此份文件的細節
本版本：
https://w3c.github.io/epub-specs/epub33/core/
最新發佈版本：
https://www.w3.org/TR/epub-33/
最新編輯草稿：
https://w3c.github.io/epub-specs/epub33/core/
歷史：
https://www.w3.org/standards/history/epub-33
發布歷程
測試套件：
https://w3c.github.io/epub-tests/index.html
實作報告：
https://w3c.github.io/epub-specs/epub33/reports/
編輯者：
Matt Garrish (DAISY Consortium)
Ivan Herman (W3C)
Dave Cramer (Invited Expert)
提出回饋：
GitHub w3c/epub-specs (提交請求, 新主題, 開放主題)
以郵件主旨[epub-33] … 主題資訊 …寄到public-epub-wg@w3.org（存檔）
Copyright © 1999-2022 W3C® (MIT, ERCIM, Keio, Beihang). W3C liability, trademark and permissive document license rules apply.

摘要

EPUB® 3定義了供數位出版品及文件用於配布及交換的格式。EPUB格式提供表現、包裝，以及編碼結構化和增強語義的網頁內容──包括HTML、CSS、SVG以及其他資源──並以單一檔案容器配布。


本文件狀態

本章節描述了本文件在其發表時的狀態。目前W3C出版品及此技術報告的最新改版之列表皆列於W3C技術報告索引，網址為：https://www.w3.org/TR/

本文件由EPUB 3工作小組發布為編輯草稿。

文件在以工作草稿發表階段，不代表受到所有W3C會員所支持。

本文件為草稿，而且可能會隨時會被其他文件更新、取代、淘汰。編輯作業尚未完成前，不適宜引用本文件。

本文件由基於 W3C專利政策下運作的一個小組所製作。W3C維護了一份與該小組交付成果有關的任何專利披露公開清單，該頁面也包含了專利披露的說明。任何人若實際擁有某項專利知識並相信其包含該專利之主要申請範圍，則必須依照W3C專利政策第六節之規定揭露該訊息。

本文件受2021年11月2日W3C流程文件所規範。

目次

摘要
本文件狀態
1. 介紹
1.1 概要
1.2 構成
1.3 與其他規格之關係
1.3.1 與HTML的關係
1.3.2 與SVG的關係
1.3.3 與CSS的關係
1.3.4 與MathML的關係
1.3.5 與SMIL的關係
1.3.6 與URL的關係
1.4 術語
1.5 符合性
1.6 製作上可用的省略
2. EPUB出版品符合性
2.1 檢查符合性
3. 出版品資源
3.1 介紹
3.1.1 宣告（manifest）平面
3.1.2 書脊（spine）平面
3.1.3 內容（content）平面
3.2 核心媒體類型
3.3 外圍資源
3.4 豁免資源
3.5 資源回退
3.5.1 宣告回退
3.5.2 固有回退
3.5.2.1 HTML audio與video回退
3.5.2.2 HTML img回退
3.5.2.3 HTML script元素
3.6 資源位址
3.7 資料URLs
3.8 檔案URLs
3.9 XML符合性
4. 開放容器格式（OCF）
4.1 介紹
4.2 OCF抽象容器
4.2.1 介紹
4.2.2 檔案與目錄結構
4.2.3 檔案路徑與檔案名稱
4.2.4 取得檔案路徑
4.2.5 OCF抽象容器中的URLs
4.2.6 META-INF目錄
4.2.6.1 包含在OCF抽象容器中
4.2.6.2 解析META-INF目錄中的URL
4.2.6.3 保留的檔案
4.2.6.3.1 容器檔案（container.xml）
4.2.6.3.1.1 container元素
4.2.6.3.1.2 rootfiles元素
4.2.6.3.1.3 rootfile元素
4.2.6.3.1.4 links元素
4.2.6.3.1.5 link元素
4.2.6.3.1.6 範例
4.2.6.3.2 加密檔案（encryption.xml）
4.2.6.3.2.1 encryption元素
4.2.6.3.2.2 壓縮與加密順序
4.2.6.3.3 宣告檔案（manifest.xml）
4.2.6.3.4 後設資料檔案（metadata.xml）
4.2.6.3.5 權利管理檔案（rights.xml）
4.2.6.3.6 數位簽章檔案（signatures.xml）
4.2.6.3.6.1 signatures元素
4.3 OCF ZIP容器
4.3.1 介紹
4.3.2 ZIP檔案規定
4.3.3 OCF ZIP容器媒體類型識別
4.4 字型模糊化
4.4.1 介紹
4.4.2 限制
4.4.3 模糊化密鑰
4.4.4 模糊化演算法
4.4.5 指定模糊化字型
5. 包裝文件
5.1 介紹
5.2 解析包裝文件中的URL
5.3 共享的屬性
5.3.1 dir屬性
5.3.2 href屬性
5.3.3 id屬性
5.3.4 media-type屬性
5.3.5 properties屬性
5.3.6 refines屬性
5.3.7 xml:lang屬性
5.4 package元素
5.5 Metadata區塊
5.5.1 metadata元素
5.5.2 Metadata值
5.5.3 都柏林核心集的必要元素
5.5.3.1 dc:identifier元素
5.5.3.2 dc:title元素
5.5.3.3 dc:language元素
5.5.4 都柏林核心集的選配元素
5.5.4.1 一般定義
5.5.4.2 dc:contributor元素
5.5.4.3 dc:creator元素
5.5.4.4 dc:date元素
5.5.4.5 dc:subject元素
5.5.4.6 dc:type元素
5.5.5 meta元素
5.5.6 最後修正日期
5.5.7 link元素
5.6 Manifest區塊
5.6.1 manifest元素
5.6.2 item元素
5.6.2.1 資源特性
5.6.2.2 範例
5.6.3 bindings元素（不再推薦）
5.7 Spine區塊
5.7.1 spine元素
5.7.2 itemref元素
5.8 集合（Collections）
5.8.1 collection元素
5.8.2 定義集合類型（不再推薦）
5.9 遺存（Legacy）功能
5.9.1 介紹
5.9.2 支援
5.9.3 meta元素
5.9.4 guide元素
5.9.5 NCX
6. EPUB內容文件
6.1 XHTML內容文件
6.1.1 介紹
6.1.2 XHTML規定
6.1.3 HTML延伸
6.1.3.1 結構語義
6.1.3.2 RDFa
6.1.3.3 內容切換（不再推薦）
6.1.3.4 epub:trigger元素（不再推薦）
6.1.3.5 客製化屬性
6.1.4 HTML歧異與限制
6.1.4.1 嵌入MathML
6.1.4.2 嵌入SVG
6.1.4.3 不鼓勵使用的架構
6.1.4.3.1 base元素
6.1.4.3.2 rp元素
6.1.4.3.3 embed元素
6.2 SVG內容文件
6.2.1 介紹
6.2.2 SVG規定
6.2.3 對SVG的限制
6.3 常見資源規定
6.3.1 層疊樣式表（CSS）
6.3.1.1 介紹
6.3.1.2 CSS規定
6.3.1.3 有字首的特性
6.3.2 腳本
6.3.2.1 包含腳本
6.3.2.2 腳本脈絡
6.3.2.2.1 受容器限制的腳本
6.3.2.2.2 書脊層級腳本
6.3.2.3 事件模型
6.3.2.4 腳本可及性
6.3.2.5 腳本回退
7. EPUB導覽文件
7.1 介紹
7.2 導覽文件規定
7.3 nav元素：限制
7.4 nav元素：類型
7.4.1 介紹
7.4.2 toc nav元素
7.4.3 page-list nav元素
7.4.4 landmarks nav元素
7.4.5 其他nav元素
7.5 用於書脊中
8. 版面處理控制
8.1 介紹
8.2 固定版面
8.2.1 介紹
8.2.2 固定版面包裝設定
8.2.2.1 版面
8.2.2.1.1 版面覆寫
8.2.2.2 頁面方向
8.2.2.2.1 方向覆寫
8.2.2.3 同步跨頁
8.2.2.3.1 同步跨頁覆寫
8.2.2.4 跨頁配置
8.2.2.5 顯示範圍空間（不再推薦）
8.2.2.6 內容文件空間
8.3 可重排版面
8.3.1 rendition:flow特性
8.3.1.1 Spine覆寫
8.3.2 rendition:align-x-center特性
9. 媒體層疊
9.1 介紹
9.2 媒體層疊文件
9.2.1 媒體層疊文件規定
9.2.2 媒體層疊文件定義
9.2.2.1 smil元素
9.2.2.2 head元素
9.2.2.3 metadata元素
9.2.2.4 body元素
9.2.2.5 seq元素
9.2.2.6 par元素
9.2.2.7 text元素
9.2.2.8 audio元素
9.3 建立媒體層疊
9.3.1 介紹
9.3.2 與EPUB內容文件之關係
9.3.2.1 層疊架構
9.3.2.2 參照文件斷片
9.3.2.3 層疊粒度
9.3.2.4 文字轉換語音處理
9.3.3 層疊中的結構語義
9.3.4 建立樣式資訊關聯
9.3.5 媒體層疊包裝
9.3.5.1 包含媒體層疊
9.3.5.2 層疊包裝後設資料
9.4 可跳過性與可跳出性
9.4.1 可跳過性（Skippability）
9.4.2 可跳出性（Escapability）
9.5 導覽文件中的層疊
10. 可及性
11. 安全與隱私
11.1 概要
11.2 威脅模型
11.2.1 EPUB特有功能
11.3 推薦
A. 不支援的功能
A.1 實作不足的功能
A.2 不再推薦的功能
B. 允許使用的外部識別碼
C. 表述結構語義
C.1 介紹
C.2 epub:type屬性
D. 用語集
D.1 用語關聯機制
D.1.1 介紹
D.1.2 property資料類型
D.1.3 預設用語集
D.1.4 prefix屬性
D.1.5 保留的字首
D.2 特性欄位定義
D.3 Meta特性用語
D.3.1 alternate-script
D.3.2 authority
D.3.3 belongs-to-collection
D.3.4 collection-type
D.3.5 display-seq
D.3.6 file-as
D.3.7 group-position
D.3.8 identifier-type
D.3.9 meta-auth（不再推薦）
D.3.10 role
D.3.11 source-of
D.3.12 term
D.3.13 title-type
D.3.14 範例
D.4 後設資料連結用語
D.4.1 Link關係
D.4.1.1 acquire
D.4.1.2 alternate
D.4.1.3 marc21xml-record（不再推薦）
D.4.1.4 mods-record（不再推薦）
D.4.1.5 onix-record（不再推薦）
D.4.1.6 record
D.4.1.7 voicing
D.4.1.8 xml-signature（不再推薦）
D.4.1.9 xmp-record（不再推薦）
D.4.2 Link properties
D.4.2.1 onix
D.4.2.2 xmp
D.5 包裝處理用語
D.5.1 客製化處理特性
D.6 宣告特性用語
D.6.1 cover-image
D.6.2 mathml
D.6.3 nav
D.6.4 remote-resources
D.6.5 scripted
D.6.6 svg
D.6.7 switch
D.7 書脊特性用語
D.7.1 page-spread-left
D.7.2 page-spread-right
D.7.3 範例
D.8 媒體層疊用語
D.8.1 active-class
D.8.2 duration
D.8.3 narrator
D.8.4 playback-active-class
E. 有字首的CSS特性
E.1 CSS writing modes
E.1.1 -epub-text-orientation特性
E.1.2 -epub-writing-mode特性
E.1.3 -epub-text-combine-horizontal以及-epub-text-combine特性
E.2 CSS text level 3
E.2.1 -epub-hyphens特性
E.2.2 -epub-line-break特性
E.2.3 -epub-text-align-last特性
E.2.4 -epub-word-break特性
E.2.5 text-transform特性
E.3 CSS text decoration level 3
E.3.1 -epub-text-emphasis-color特性
E.3.2 -epub-text-emphasis-position特性
E.3.3 -epub-text-emphasis-style特性
E.3.4 -epub-text-underline-position特性
F. viewport meta標籤
F.1 介紹
F.2 語法
G. 綱要
G.1 包裝文件綱要
G.2 OCF綱要
G.2.1 container.xml用的綱要
G.2.2 encryption.xml用的綱要
G.2.3 signatures.xml用的綱要
G.3 媒體層疊綱要
H. 完整範例
H.1 資源
H.2 腳本脈絡
H.3 包裝化EPUB
H.4 時鐘值
I. 媒體類型註冊
I.1 application/oebps-package+xml媒體類型
I.2 application/epub+zip媒體類型
J. 索引
J.1 由2023年2月21日本規格定義的術語
J.2 由2023年5月12日本規格定義的術語
J.3 參考資料定義的術語
K. 變更日誌
K.1 由推薦候選以來的主要變更
K.2 由EPUB 3.2以來的主要變更
L. 致謝
M. 參考
M.1 規範性參考文件
M.2 參考性參考文件
1. 介紹

1.1 概要

本節不具規範性。

EPUB 3為目前已廣受採用的數位書籍（電子書）格式，本次改版持續擴充該格式的可能性，以提供對更廣範圍出版品需求的支援，包括複雜版面、富媒體與互動性，以及全球文字排版功能。期盼出版商能夠活用EPUB 3規格於廣範圍的內容，包括書籍、雜誌以及教育、專業和科學出版品上。

本規格呈現EPUB 3的核心，包含對EPUB出版品─本標準的產品─的符合性規定。其他構成EPUB 3的規格如下：

EPUB 3閱讀系統 [epub-rs-33]─定義了對EPUB閱讀系統的處理規定─EPUB閱讀系統為處理EPUB出版品，並且將其內容展示給使用者的應用程式。

EPUB可及性 [epub-a11y-11]─定義了無障礙輔助的符合性以及EPUB出版品的發現性規定。

以正式列表呈現的這些規格可被視為EPUB 3規格，並且其包含的功能正式視為標準的一部分。延伸規格持續發展，會定期為EPUB出版品加入新的功能。本標準核心改版外所定義的特色與功能，無需被正式視為本規格的一部分，但EPUB製作者與閱讀系統開發者依然可以使用。

EPUB 3總覽[epub-overview-33]不具規範性，提供了一般性的EPUB 3介紹。從前一版本迄今的技術變更，位於變更日誌中。

1.2 構成

本節不具規範性。

本章節透過其定義的中心產品：EPUB出版品，來檢視本規格的構成。

一本EPUB出版品，以最基本的理解，為一組具備程序的資源，其程序告知如何處理這些資源，將內容以邏輯順序呈現出來。准許用於EPUB出版品中的資源類型，以及其使用上的限制，定義在3.出版品資源中。

EPUB出版品以一個副檔名為.epub，基於ZIP技術的封存檔包裝所有資源供配布使用。作為合乎規定的ZIP封存檔，EPUB出版品可以由許多軟體程式解壓縮，能讓製作與使用都變得簡單。

該容器格式不僅提供了判斷以ZIP壓縮過的內容是否為EPUB出版品（透過mimetype檔案）的手段，也提供了置放參考性資源的通用名稱目錄（/META-INF）。這些資源的關鍵檔案為container.xml，該檔案指引閱讀系統取得包裝文件。請參見4. 開放容器格式（OCF）以獲得更多關於容器格式的資訊。

一本EPUB出版品一般由單一包裝文件所呈現。該文件包含了供閱讀系統所使用的後設資料，以將內容呈現給使用者，像是在書架上展示書名與作者；也包括了處理用的後設資料（即為，該內容是否為流式或者包含固定版面等）。其也提供了資源的宣告，也包含一份書脊，其中列出處理文件的預設序列，供使用者在內容進行時使用。請參見5. 包裝文件以獲得對包裝文件的規定。

一本EPUB出版品的實際內容─當使用者開始閱讀時所呈現的那些內容─基於開放網頁平台，主要得惠於兩項技術：XHTML與SVG。稱為EPUB內容文件，這些文件一般會參照許多額外的必須資源來進行適當的處理，資源像是圖片、聲音和影片片段、腳本以及樣式表。

請參見6. EPUB內容文件以取得詳細關於製作EPUB內容文件之規則以及規定的詳細資訊，也可以參照[epub-a11y-11]以獲得可及性規定。

一本EPUB出版品也包含另一個關鍵檔案稱為EPUB導覽文件。該文件提供了重要的導覽能力，像是目次，能讓使用者快速且輕易地導覽內容。導覽文件為一份特化類型的XHTML內容文件，能讓EPUB製作者用於內容中（也就是，避免機器處理一份目錄，還要另做一份給使用者閱讀）。請參見7. EPUB導覽文件以獲得與該文件的更多資訊。

EPUB出版品預設上為文字重排（流式）以符合可使用的螢幕空間。但也能夠使用圖片及/或CSS定位來創建精準到像素的固定版面出版品。用於控制版面的後設資料定義在8. 版面處理控制。

媒體層疊文件可作為EPUB內容文件的補充。媒體層疊提供了宣告式標記能讓EPUB內容文件中的文字和預錄的音檔同步播放。結果提供了用於創建朗讀體驗的能力，讓閱讀系統在朗誦時強調文字。請參見9. 媒體層疊以取得媒體層疊文件的定義。

就算概念簡單，但EPUB出版品卻不僅如這裡所描述：是一組以ZIP包裝的HTML頁面與所需素材的集合而已。關於EPUB出版品能提供用於增進閱讀體驗的主要特色與功能，這些額外資訊可透過參照的規格所取得，而更一般性的EPUB 3特色介紹提供於非規範性的[epub-overview-33]。

請參見[epub-rs-33]以取得供閱讀系統使用的處理規定。儘管對EPUB製作者而言，不需要閱讀該份文件也能製作EPUB出版品，但能夠了解閱讀系統如何呈現內容，可以協助製作最佳化表現以提供給使用者。

1.3 與其他規格之關係

本節不具規範性。

警告事項
EPUB 3所奠基的技術持續演進。有些常被稱為「活的（living）」或者「常青（evergreen）」標準，可能每天都會有所變更，也會對EPUB出版品合規性造成即時衝擊。其他技術更新頻率較低，其變更可能不會對EPUB 3到下次改版前造成影響。

在所有的狀況中，可能會發生之前合規的功能被淘汰的狀況（因為缺少支援或者安全問題）。EPUB製作者因而應該在使用缺少廣泛支援的功能時多加注意，並且保持其EPUB符合性檢驗工具為最新。

1.3.1 與HTML的關係

[html]標準不斷演進─也就是不再發佈有編號的版本。該標準持續參照各項不斷演進的技術，例如MathML、SVG、CSS與JavaScript。

這種方式對EPUB的助益為：EPUB出版品可以一直跟隨網頁演進的腳步前進而不需要推出新的版本。然而，EPUB製作者必須持續追蹤HTML的各項變化，以及所參照的各種技術，以確保製作程序跟得上時代。

本規格定義的XHTML子集（Profile），除了另有指定之外，繼承了所有HTML的語義、結構、處理行為定義。

此外，本規格定義了[html]文件模型的一組延伸，以讓EPUB製作者可以包含在XHTML內容文件中。

1.3.2 與SVG的關係

本規格並不參照特定版本的[svg]，而參照無日期的版本。當所參照的版本產生歧義時，權威性參考文件為最新推薦版本。

這種作法確保EPUB可以一直跟隨SVG標準演進的腳步前進。然而，EPUB製作者必須持續追蹤SVG標準的變化，以確保製作程序跟得上時代。

1.3.3 與CSS的關係

EPUB 3支援的CSS定義於CSS工作小組快照[csssnapshot]。EPUB 3也維護一些有字首的CSS特性，以確保對全球語言的穩定支援。

1.3.4 與MathML的關係

EPUB 3僅支援顯示用標記[mathml3]。內容標記僅允許用於有結構的標記註解中。

1.3.5 與SMIL的關係

本規格依靠[smil3]的子集，由該屬性延伸的媒體層疊元素與屬性定義在9.2.2 媒體層疊文件。

1.3.6 與URL的關係

本規格參照了[url]標準，運用術語以及在 EPUB出版品中與URL表述的相關處理。可預期新的以及改版的網頁格式也會採用本標準，但在那之前，這種作法會讓本規格與一些格式（例如，驗證相對路徑）的內部規範產生衝突，特別是關於國際化URL的使用。如果一個格式不允許使用國際化的URL（也就是URL必須合乎[rfc3986]或更早的版本），該規定在這些資源中具有優先地位。

1.4 術語

本規格定義了專門用於EPUB 3的術語如下。

註釋
每一章節中只有術語第一次出現時會連結到其定義。

codec（編碼）
編碼所指的是內容其擁有固有的二進位格式特性，像是影片或者聲音媒體類型為了壓縮最佳化而設計，或者能提供最佳化的串流能力。

container resource（容器資源）
一份出版品資源，其位於EPUB容器之中，相對的是遠端資源，其不位於EPUB容器中。

請參見3.6 資源位址以獲得對特別媒體類型之資源位址的規則。

container root URL（容器根位址）
根目錄的URL [url]代表了OCF抽象容器。雖然僅和實作方相關，但EPUB製作者必須假設其具備定義在4.2.5 OCF抽象容器中的URL一節中的特性。

content URL（內容位址）
在OCF抽象容器中檔案或目錄的URL，定義於4.2.5 OCF抽象容器中的URLs。

core media type resource（核心媒體類型資源）
一份出版品資源，其MIME媒體類型[rfc2046]合乎3.2 核心媒體類型中所列之任一項，因此不需要提供回退（相較於 外圍資源）。

指定「核心媒體類型資源」僅應用於EPUB內容文件以及外圍內容文件處理資源上。核心媒體類型資源不能直接用於書脊，舉例說明：除非具備回退，且回退的媒體類型為EPUB內容文件。

EPUB conformance checker（EPUB符合性檢驗工具）
一款用於檢驗EPUB出版品是否符合本規格的規定，並且報告其符合性的應用程式。

EPUB container（EPUB容器）
OCF ZIP container（OCF ZIP容器）
供EPUB出版品使用，基於ZIP技術的包裝與配布格式，定義在4.3 OCF ZIP容器中。

EPUB容器與OCF ZIP容器為同義詞。

EPUB content document（EPUB內容文件）
一份出版品資源在書脊，或者在宣告回退鏈中受到參照，其定義符合XHTML或SVG內容文件兩者其一。

EPUB內容文件包含一本EPUB出版品的所有或者部分內容（也就是：文字、視覺以及/或者聲音內容）。

EPUB製作者可以在書脊中包含EPUB內容文件，而無需提供回退。

EPUB creator（EPUB製作者）
生產EPUB出版品的個人、組織或者製程。

註釋
製作EPUB出版品的過程通常涉及多數個人的協力，也可能被切分到跨多個組織（例如出版社把全部或一部分的工作外發）。按照製作EPUB出版品的程序不同，責任可能落在組織（例如出版社）、準備出版品的個人（例如技術編輯），或者自動製程（例如作為出版流程的一部分）。結果上而言，並非所有參與者或者製程都要為確保符合所有規定負責，但總該有一位EPUB製作者要為最終EPUB出版品的合規性負責。

本規格之前的版本將EPUB製作者稱為作者（the Author）。

EPUB manifest (or manifest)（EPUB宣告或者宣告）
包裝文件中的區塊，條列出版品資源。

請參見5.6.1 manifest元素以獲得更多資訊。

EPUB navigation document（EPUB導覽文件）
一份特化的XHTML內容文件，其中包含人類與機器皆可以閱讀的全域導覽資訊。EPUB導覽文件須符合在7. EPUB導覽文件中描述的限制。

EPUB publication（EPUB出版品）
一份邏輯上的文件實體，包含一組相互關聯的資源，包裝在一個EPUB容器中。

一本EPUB出版品一般代表單一智慧或藝術作品，但本規格不限制內容的性質。

EPUB reading system (or reading system)（EPUB閱讀系統或者閱讀系統）
一個以合乎本規格之方式處理EPUB出版品呈現給使用者的系統。

EPUB spine (or spine)（EPUB書脊或者書脊）
包裝文件中的區塊，定義了一份EPUB內容文件與外圍內容文件的順序列表。該列表代表EPUB出版品的預設閱讀順序。

請參見5.7.1 spine元素以獲得更多資訊。

exempt resource（豁免資源）
豁免資源為一個特別分類的出版品資源，閱讀系統不需要支援處理這類資源，同時EPUB製作者也不需要為其提供回退。

請參見3.4 豁免資源以獲得更多資訊。

file name（檔案名稱）
位於OCF抽象容器中任何類型檔案的名稱，可以是一個目錄，或者目錄中的一個檔案。

file path（檔案路徑）
一個目錄或一個檔案的檔案路徑為其相對於根目錄的完整路徑，如4.2.4 取得檔案路徑中指定的演算法所定義。

fixed-layout document（固定版面文件）
一份直接在書脊中參照、有著固定尺寸的EPUB內容文件。固定版面文件在包裝文件中指定為預分頁（pre-paginated），如8.2 固定版面所定義。

foreign content document（外圍內容文件）
任何在書脊中透過itemref元素，或者宣告回退鏈所參照的出版品資源，其並非一份EPUB內容文件。

當外圍內容文件在書脊中透過itemref元素參照，其必須要有一個宣告回退鏈至少包含一份EPUB內容文件。

註釋
除了XHTML與SVG以外，所有核心媒體類型資源當在書脊中直接參照時，都是外圍內容文件。

foreign resource（外圍資源）
一份出版品資源，其MIME媒體類型[rfc2046]不符合3.2 核心媒體類型中所列之任一項，外圍資源需符合3.3 外圍資源所定義的回退規定。

指定「外圍資源」僅應用於EPUB內容文件以及外圍內容文件處理資源上。

註釋
外圍資源與外圍內容文件並非互通的術語。用於書脊中的資源類型被考量為外圍，其重要性大過於用於EPUB內容文件中的資源類型被視為外圍。

linked resource（連結的資源）
一份資源，其僅在包裝文件中透過link元素所參照（也就是不會用於EPUB出版品的處理中）。

連結的資源並非出版品資源，但可能儲存在EPUB容器中。他們不需要提供回退。

media overlay document（媒體層疊文件）
一份XML文件，用於讓XHTML內容文件和預錄的聲音旁白相關聯，以提供同步播放的體驗，如9. 媒體層疊所定義。

non-codec（非編碼）
非編碼所指的是內容類型其因為內在資料結構而能得益於壓縮，像是基於字符串的檔案格式（舉例而言，HTML、CSS等）。

OCF abstract container（OCF抽象容器）
OCF抽象容器定義了一個檔案系統模型供OCF ZIP容器中的內容使用，如4.2 OCF抽象容器中所定義。

package document（包裝文件）
一份出版品資源，其按照定義於5. 包裝文件的方式說明如何處理EPUB出版品。包裝文件乘載了EPUB出版品的後設資訊，提供資源宣告並且定義預設閱讀順序。

publication resource（出版品資源）
一份資源，其包含了EPUB出版品處理上所需的內容或者協助處理邏輯的程序。若缺少該資源，閱讀系統可能無法如EPUB製作者所預期般處理EPUB出版品。出版品資源的範例包含：包裝文件、EPUB內容文件、CSS樣式表、聲音、影片、圖片、嵌入字型以及腳本。

EPUB製作者必須在包裝文件宣告中條列出版品資源，並且一般來說，該把所有資源置放於EPUB容器中（資源位置位於EPUB容器外的例外狀況請見3.6 資源位址）。

註釋
對外連節的超連結中，可被識別位於網頁上的資源（也就是透過[html]a元素之href屬性所參照的資源）並非出版品資源。

資料URL也並非出版品資源─他們可被視為其所嵌入資源的一部分。

remote resource（遠端資源）
一份出版品資源其位於EPUB容器之外，通常，但並非必然，位於網頁上。

EPUB容器內的出版品資源被參照為容器資源。

請參見3.6 資源位址以獲得媒體類型專屬的資源位址規則。

root directory（根目錄）
根目錄代表了OCF抽樣容器檔案系統的最底層。該目錄性質上為虛擬。

scripted content document（有腳本的內容文件）
一份包含腳本的EPUB內容文件，或者為一份包含[html] form元素的XHTML內容文件。

請參見6.3.2 腳本以獲得更多資訊。

SVG content document（SVG內容文件）
一份EPUB內容文件，其合乎6.2 SVG內容文件中所表述的規定。

synthetic spread（同步跨頁）
在一台設備的螢幕上連續處理兩張相鄰的頁面。

top-level content document（頂層內容文件）
一份在書脊中參照的 EPUB內容文件或外圍內容文件，不分直接參照或者透過回退鏈參照。

unique identifier（唯一識別碼）
一本EPUB出版品的主要識別碼。唯一識別碼為在包裝文件中具有unique-identifier屬性的dc:identifier的值。

明顯的大改版、刪節等，這類的內容需要新的唯一識別碼。

viewport（顯示範圍）
EPUB閱讀系統處理一本EPUB出版品，視覺上呈現給使用者的區域。

XHTML content document（XHTML內容文件）
一份EPUB內容文件，其合乎6.1 XHTML內容文件中定義的[html]子集。

XHTML內容文件使用了定義在[html]中的XML語法。

1.5 符合性

本規格中被標註為非規範性的章節，以及所有製作準則、圖表、範例以及註釋都為非規範性。本規格其他部分皆為規範性。

關鍵字：可以（MAY）、必須（MUST）、不得（MUST NOT）、選擇性（OPTIONAL）、推薦（RECOMMENDED），需要（REQUIRED）、應該（SHOULD）、不應（SHOULD NOT）在本文件中以如上粗體加底線格式出現時，BCP 14[RFC2119] [RFC8174] 中的敘述解釋。

所有演算法的說明皆為非規範性。

1.6 製作上可用的省略

本節不具規範性。

在包裝文件後設資料範本中，保留的字首不需宣告即可使用。

參照讀柏林核心集的元素[dcterms]使用dc:字首。該字首必須在包裝文件中宣告以確保合規（xmlns:dc="http://purl.org/dc/elements/1.1/"）。

epub命名空間字首[xml-names]也會用於元素以及屬性，所以並非隨時都需要明確地宣告（xmlns:epub="http://www.idpf.org/2007/ops"）。

2. EPUB出版品符合性

一本EPUB出版品：

必須定義至少一個對內容的處理方式如下：

必須包含合乎5. 包裝文件規定的包裝文件，並且符合所有對包裝文件的出版品資源規定。

必須包含合乎7. EPUB導覽文件規定的EPUB導覽文件。

應該合乎定義在[epub-a11y-11]的可及性規定。

必須以定義在4. 開放容器格式（OCF）中定義的EPUB容器進行包裝。

此外，所有出版品資源必須遵守3. 出版品資源中的規定。

本規格其餘部分涵蓋了特定的符合性細節。

2.1 檢查符合性

本節不具規範性。

由於本規格的複雜程度，以及應用在EPUB出版品中的技術眾多，建議EPUB製作者能夠使用EPUB符合性檢查工具來驗證內容是否合規。

EPUBCheck為實際上受到出版產業採用的EPUB符合性檢查工具，並且會隨EPUB新版本推出而更新。其也被整合到多數的製作工具中，以不同的介面和各種語言呈現（若想獲得更多資訊，請參見其App與工具頁面）。

當EPUB製作者驗證其EPUB出版品時，應確保出版品不會違反本規格的規定（實際可以透過關鍵字「必須」、「不得」以及「需要」來識別）。這些類型的問題經常造成EPUB出版品無法被處理，或者以不穩定的方式處理。這些問題一般會以錯誤（errors）或重大錯誤（critical errors）回報。

EPUB製作者也應該確保其EPUB出版品不違反本規格的推薦項目（實際可以透過關鍵字「應該」、「不應」以及「推薦」來識別）。不能遵從這些實踐並不會造成EPUB出版品不合規定，但可能產生相容性或其他問題而影響使用者的閱讀經驗。這些問題一般會以警告（warnings）回報。

註釋
銷售者、經銷者以及其他EPUB出版品的零售者，應該考量推薦實踐的重要性，而不應該以EPUB符合性檢查工具問題零檢出作為採用或者退件的標準。EPUB製作者無法在所有的狀況都遵從推薦實踐，有其合理的原因。

3. 出版品資源

3.1 介紹

本節不具規範性。

一本EPUB出版品由許多不同範疇的資源所組成，這些資源範疇有時會重疊，並非完全彼此互斥。有些資源為出版品資源，有些不是。有些出版品資源預設允許用於書脊，而其他需要提供回退。有些資源會被用於EPUB內容文件處理，有些僅會被用於回退。

透過閱讀每個資源範疇的技術定義以試圖理解這些差別可能不容易。為了讓範疇分類更易於理解，本介紹使用平面的概念來解釋資源如何被分類以及受參照。

三個平面分別為：

manifest（宣告）平面─宣告平面掌握所有EPUB出版品中的資源（如其名，出版品資源以及連結的資源）。.
spine（書脊）平面─書脊平面僅掌握用於處理書脊的資源（如其名，EPUB內容文件以及外圍內容文件）。
content（內容）平面─內容平面僅掌握用於處理EPUB以及外圍內容文件的資源（如其名，核心媒體類型資源、外圍資源以及豁免資源）。
同一份資源可能存在於多於一個的平面，也可能在本規格中按照所討論平面的不同而受到不同的參照。舉個例子，一份核心媒體類型資源用於處理EPUB內容文件（在內容平面上）當其也列於書脊（書籍平面）時，則為外圍內容文件。

以下章節說明這些平面的細節。

註釋
請參見H.1 資源以獲得詳細範例說明這些資源如何匹配到不同平面上。

3.1.1 宣告（manifest）平面

宣告平面定義了所有EPUB出版品中的資源。可以比擬到包裝文件的宣告上，但包括了不需要在其中列出的資源。

這群組中最主要的資源為指定的出版品資源，所有的這些資源都用於將EPUB出版品處理給使用者閱讀。EPUB製作者無論何時都需要將這些資源在manifest元素中表列出來。

出版品資源可更進一步分類，根據用途分配到書脊平面和內容平面。

宣告平面也包含了一系列連結的資源。這些資源和處理沒有直接關係。舉例這些資源包括：後設資料紀錄以及到外部內容的連結（例如：購買EPUB出版品的網站）。

不像出版品資源，這些資源不會列於包裝文件宣告（也就是因為他們對於處理EPUB出版品而言並非必要）。他們會在包裝文件的後設資料中透過link元素來進行定義。這些元素定義了其性質及目的，就像是宣告中item元素用於定義出版品資源（以這種方式，他們會像是宣告的延伸）。

請參見5.5.7 link元素以獲得更多與連結資源相關的資訊。

在宣告平面的資源有時無法連結到他們所在的位置。儘管多數出版品資源都必須置放在EPUB容器中（稱為容器資源），EPUB 3允許聲音、影片、字型與腳本資料資源置放在容器之外。這些例外的目的是為了加速EPUB出版品的下載與載入，因為這些資源通常都相當大，以及，就字型的狀況而言，顯示上並非必要。當遠端託管時，這些出版品資源被稱為遠端資源。

由於連結的資源對處理EPUB出版品而言並非必要，所以也沒有規定他們所在的位址，因此也不會由其所在的位址給予特殊的名稱。他們可以位於EPUB容器中或在之外。

註釋
透過超連結連到EPUB容器之外的內容（例如網頁）並非出版品內容，所以也不需要列於宣告中。閱讀系統一般會透過另外的瀏覽器頁面開啟該連結，而並非EPUB出版品的一部分。

3.1.2 書脊（spine）平面

書脊平面定義了透過書脊建立預設閱讀順序中使用到的資源，其中包括了線性與非線性內容兩方。書脊只是閱讀系統如何載入資源讓使用者逐進度閱讀整本EPUB出版品。儘管許多資源可能一併放在EPUB容器中，但他們並非全都能預設用於書脊中。

EPUB 3定義了特別類型的資源稱為EPUB內容文件，EPUB製作者可以將其用於書脊而沒有任何限制。EPUB內容文件包含XHTML內容文件以及SVG內容文件。

將任何其他種類的資源用於書脊時，就稱呼其為外圍內容文件，會需要包含一個回退指向EPUB內容文件。此可延伸性模型讓EPUB製作者能夠以各種格式進行實驗的同時，確保閱讀系統總能夠處理出一些東西供讀者閱讀，因為對外圍內容文件的支援不在保證範圍內。

稱為宣告回退的機制讓EPUB製作者可以為外圍內容文件提供回退。在此模型下，外圍內容文件的宣告資料項必須包含一個fallback attribute屬性以指向下一個可能供閱讀系統使用的資源，在不支援該格式時嘗試處理。雖然不常見，但回退的資源還可以指定另外一個回退，因而讓資源串起如鍊般的深度。對宣告回退鏈只有一項要求，即為其中必須至少包含一份EPUB內容文件。

儘管並非直接列於書脊，所有在回退鏈中的資源都被視為書脊的一部分，以及書脊平面的延伸部分，因為他們都可能被閱讀系統所使用。

請參見3.5.1 宣告回退以獲得更多資訊。

警告事項
儘管宣告回退符合EPUB技術上規定，但閱讀系統對這技術的實作支援尚少。所以強烈不建議使用，可能會因而作出無法被閱讀的出版品。

註釋
雖然可能為EPUB內容文件提供宣告回退，但並非必要也不常見。例如，一份有腳本的內容文件可以回退到無腳本替代品上，供不支援腳本的閱讀系統使用。

3.1.3 內容（content）平面

鑑別內容平面資源的方法是看是否用於處理EPUB內容文件與外圍內容文件。這些類型的資源包括嵌入用媒體、CSS樣式表、腳本以及字型。這些資源基於閱讀系統支援可以落在三項類型：核心媒體類型資源、外圍資源以及豁免資源。

核心媒體類型資源為閱讀系統必須支援的資源，所以可無限制地使用於EPUB或者外圍內容文件上。請參見3.2 核心媒體類型以獲得更多關於核心媒體類型資源的相關資訊。

註釋
作為核心媒體類型資源並不代表閱讀系統隨時都能處理該資源，就像並非所有閱讀系統都會支援所有EPUB 3的功能一樣。舉個例子，不支援顯示範圍（viewport）的閱讀系統，就不會處理影像這類的視覺內容。

相對於核心媒體類型資源的是外圍資源。閱讀系統不保證能支援這些資源受到處理。結論上來說，就和在書脊中使用外圍媒體文件一樣需要回退以確保能夠處理，在內容文件中使用外圍資源也需要回退。這些回退可以用以下兩種方法之一提供：使用主格式的回退功能或者透過宣告回退。

推薦的方法為使用主格式的回退功能。舉個例子，許多HTML元素都有固有的回退能力。一個案例是[html]中的picture元素，可以讓EPUB製作者指定多種替代的影像格式。

如果無法使用固有的回退方法，也可以使用宣告回退，但是這方法如同前一章節中所警告，不推薦使用。請參見3.3 外圍資源以獲得更多與外圍資源的相關資訊。

在核心媒體類型資源以及外圍資源之間的是豁免資源。這些資源更接近外圍資源，同樣不保證閱讀系統會對其進行處理，但和核心媒體類型相同的是：不需要提供回退。

豁免資源主要應用於處理特殊狀況，其沒有定義在核心媒體類型之中，但要為其提供回退可能過於麻煩或者沒有必要。這些資源包括嵌入的影片、額外的無障礙輔助軌，以及透過[html]link元素連結到的資源。

請參見3.4 豁免資源以獲得更多關於這些例外的資訊。

註釋
核心媒體類型資源經常被混淆的一點是將XHTML與SVG列為核心媒體類型資源並要求其標記須合乎各自的EPUB內容文件定義。這使得EPUB製作者可以將XHTML與SVG文件嵌入EPUB內容文件同時在製作上以及閱讀系統支援上符合規定。

實務上，這意味著EPUB製作者可以將XHTML及SVG核心媒體類型資源放在書脊中且不需做任何修改或提供回退（他們也是合規的XHTML與SVG內容文件），但這是很獨特的案例。所有其他的核心媒體類型資源在用於書脊時，都變成外圍內容文件（也就是外圍內容文件包含了所有外圍資源以及所有核心媒體類型資源，XHTML與SVG除外）。

3.2 核心媒體類型

EPUB製作者可以包含合乎以下表格定義之MIME媒體類型[rfc2046]規格之出版品資源，無論用於EPUB內容文件或者外圍內容文件時，都不需要提供回退。這些資源可被分類為核心媒體類型資源。

除了XHTML內容文件以及SVG內容文件為例外，EPUB製作者在書脊中直接參照核心媒體類型資源時，必須提供宣告回退。在這狀況中，它們為外圍內容文件。

表格的橫列代表了以下資訊：

媒體類型—用於在宣告中表達該出版品資源的MIME媒體類型[rfc2046]。

如果表格列出一個以上的媒體類型時，第一個為推薦的媒體類型。EPUB製作者應該在所有新的EPUB出版品中使用推薦的媒體類型。

內容類型定義—該核心媒體類型資源必須合規的規格。
適用範圍—媒體類型與內容類型定義是用於哪一種出版品資源類型。
媒體類型	內容類型定義	適用範圍
圖片
image/gif	[gif]	GIF圖片
image/jpeg	[jpeg]	JPEG圖片
image/png	[png]	PNG圖片
image/svg+xml	SVG內容文件	SVG文件
image/webp	[webp-container], [webp-lb]	WebP圖片
聲音
audio/mpeg	[mp3]	MP3聲音
audio/mp4	[mpeg4-audio], [mp4]	使用MP4容器的AAC LC聲音
audio/opus	[rfc7845]	使用OGG容器的OPUS聲音
樣式表
text/css	CSS Style Sheets	CSS樣式表
字型
font/ttf
application/font-sfnt
[truetype]	TrueType字型
font/otf
application/font-sfnt
application/vnd.ms-opentype
[opentype]	OpenType字型
font/woff
application/font-woff
[woff]	WOFF字型
font/woff2	[woff2]	WOFF2字型
Other
application/xhtml+xml	XHTML內容文件	使用XML語法[html]的HTML文件
application/javascript
application/ecmascript
text/javascript
[rfc4329]	腳本
application/x-dtbncx+xml	[opf-201]	遺存的NCX
application/smil+xml	Media overlays	EPUB媒體層疊文件
註釋
列於核心媒體類型資源並不表示所有的閱讀系統都會支援對這些資源的處理。閱讀系統支援基於應用程式的能力（例如，支援顯示區域的閱讀系統必須支援圖片核心媒體類型資源，但是一個不支援顯示區域的閱讀系統就不會支援）。請參見[epub-rs-33]的核心媒體類型以獲得更多對閱讀系統支援處理何種核心媒體類型資源的能力規定資訊。

工作小組僅將常見格式列為核心媒體類型資源，因為他們廣泛地受到網頁瀏覽器核心所支援─該排版引擎也用來建構EPUB 3閱讀系統。就像一份在閱讀系統開發者以及EPUB製作者間的協議，以確保EPUB出版品的處理可被預測。

3.3 外圍資源

一份 外圍資源，不像核心媒體類型資源，當在EPUB內容文件或者外圍內容文件中使用時，不保證閱讀系統會對其支援。

EPUB製作者必須對外圍資源提供回退，回退採以下形式之一：

由主格式提供的固有回退機制（例如[html]元素一般提供參照多於一個的媒體類型之能力或者在媒體類型無法被處理時顯示替代嵌入資訊）；或者

在包裝文件的item元素中定義宣告回退鏈。

註釋
請參見[html]與[svg]規格以了解各元素提供的固有回退能力。

3.5.2 固有回退也提供了額外資訊說明特定元素如何進行回退。

3.4 豁免資源

豁免資源與外圍資源以及核心媒體類型資源兩方共享特性。這種資源與外圍資源更為相近，原因是閱讀系統不保證支援，但不像核心媒體類型資源，不需要提供回退。

豁免資源只有一小組特別的案例。舉個例子，豁免的影片不需提供回退，因為在這時間點對於核心媒體類型的影片格式尚無共識（也就是沒有可以回退的格式）。同樣的聲音與影片軌受到豁免，可以讓EPUB製作者使用任何閱讀系統支援最好的格式，以符合可及性規定。

以下列表說明了特定內容的豁免案例，包含EPUB製作者能用在何處的限制。

字型
所有沒有包含在字型核心媒體類型的字型支援都是豁免資源。

這項豁免允許EPUB製作者使用任何格式的字型而無需提供回退，無論閱讀系統是否支援，CSS規則能夠確保在不支援時，總會回退到一個字型上。

請參見[epub-rs-33]對字型的 閱讀系統支援規定以獲得更多資訊。

連結的資源
任何透過[html]link元素所參照，而並非核心媒體類型資源的資源（例如CSS樣式表）都是豁免資源。

影音軌
所有透過[html]track元素參照的聲音與影片軌（也就是[webvtt]字幕、對白與說明）都是豁免資源。

影片
所有透過[html]video參照的影片編碼─包括任何source子元素─都為豁免資源。

註釋
儘管鼓勵閱讀系統至少支援h.264[h264]以及VP8[rfc6386]影片編碼，對影片編碼的支援並非規定的合規性。EPUB製作者包含何種影片格式時，必須考量到各種因素，像是採用的廣度、播放品質，以及技術授權金。

註釋
以上豁免案例並不適用於書脊。假設一個豁免資源用於書脊，其不會變成EPUB內容文件，脈絡上將會需要回退。

除了特定內容的豁免案例外，滿足以下條件的資源也能被視為豁免資源：

並未透過書脊中itemref元素所參照（也就是以外圍內容文件的方式使用）；以及

並非直接被EPUB內容文件嵌入使用（也就是透過[html]嵌入內容以及[svg]的image與foreignObject元素）。

這樣的豁免能讓EPUB製作者能在EPUB容器中包含資源，但並非供EPUB閱讀系統使用。這種豁免最主要的案例就是允許資料檔案隨著EPUB出版品一併提供，無論是供腳本使用來構成EPUB內容文件，或者供外部應用程式使用（例如，科學期刊可能會包含一組資料和教導如何將其從EPUB容器中取出的教程）。

也可以讓EPUB製作者在外圍內容文件中使用外圍資源，同時閱讀系統或者 EPUB符合性檢查工具不需要了解這些資源的回退能力（也就是對外圍內容文件的回退要求涵蓋了其中任何處理問題）。只要資源不在EPUB內容文件中受參照，就會自動從回退中豁免。

3.5 資源回退

3.5.1 宣告回退

宣告回退是包裝文件的一項特色，能為一份出版品資源創立宣告回退鏈，可使閱讀系統選擇能夠處理的替代格式。

回退鏈使用宣告item元素中的fallback attribute屬性來建立。這項屬性參照另一個宣告item的ID[xml]，指定為現在item的回退。從一個item的fallback屬性開始，閱讀系統可以取得所有資源的順序列表，代表了該項目的完整回退鏈。該回退鏈也代表了EPUB製作者偏好的回退順序。

宣告回退有兩種狀況：

書脊回退
EPUB製作者必須為一份外圍內容文件指定回退鏈，以確保閱讀系統都能處理書脊中的項目。在這案例中，回退鏈必須包含至少一份EPUB內容文件。

EPUB製作者可以對EPUB內容文件提供回退（例如為有腳本的內容提供回退）。

當回退鏈包含多於一個EPUB內容文件時，EPUB製作者能使用properties屬性來區分彼此的目的。

內容回退
註釋
內容回退原來的目的是用於指定[html]img 元素的回退圖片。但現在HTML有了固有的圖片回退機制，就強烈不建議使用內容回退。EPUB製作者應該優先使用[html]與[svg]固有的回退能力來提供回退內容。

EPUB製作者在參照外圍資源的元素沒有固有回退能力時，必須為提供其提供內容回退。在這種案例中，回退鏈必須包含至少一個核心媒體類型資源。

EPUB製作者可以為核心媒體類型資源提供宣告回退（例如，讓閱讀系統從多個圖片格式中選擇一種）。

無論使用哪一種類型的宣告回退，回退鏈不得包含對自身的參照或讓鏈中item元素參照成為循環迴圈。

註釋
由於以資料URL呈現的資源無法使用宣告回退，EPUB製作者僅能將資料URL以外圍資源的方式表現，而有固有的回退機制。

3.5.2 固有回退

以下章節提供了關於特定元素固有回退規定的額外說明。

3.5.2.1 HTMLaudio與video回退

EPUB製作者不得在媒體元素（也就是audio或video）中嵌入[html]流式內容作為供聲音外圍資源的固有回退。只有子source元素[html]提供了固有回退能力。

較舊的閱讀系統無法辨識audio或video元素（例如EPUB 3閱讀系統）就會處理嵌入的內容。當閱讀系統支援這些元素，但不支援媒體格式時，就不會將這些嵌入的內容處理給使用者看。

註釋
這項回退規定僅適用於透過audio與video元素參照的聲音外圍資源。影片資源不需要回退；其為豁免資源。

3.5.2.2 HTML img回退

因為EPUB製作者可以在[html]img元素中指定各種來源，以下回退狀態適用於這些用途：

如果作為picture元素的子元素：

當EPUB製作者使用src以及srcset屬性時，必須在屬性中參照核心媒體類型資源；以及
每一個相伴的source元素必須在其src以及srcset屬性中參照核心媒體類型資源，除非在其type屬性中指定了外圍資源的MIME媒體類型[rfc2046]。
除此之外，其可以在其src以及srcset屬性中參照EPUB製作者已定義的外圍資源。
3.5.2.3 HTML script元素

儘管資料區塊的MIME媒體類型[rfc2046]，與在其中的XHTML內容文件有所區隔，但因為在[html]script元素中沒有特定的機制，所以不可能提供固有回退。也不可能提供宣告回退，因為資料區塊無法在EPUB容器中定義成獨立的檔案，而必須以文內script元素的方式嵌入。

但是如同script元素不代表使用者內容─資料區塊若不透過腳本操作就不會被處理，同時由腳本處理的內容已經有了核心媒體類型規定─若原始資料不能提供有用的用途時需要回退。

結果上，為了確保EPUB製作者可以為了腳本目的包含資料區塊，而從回退需求中得到豁免。

註釋
資料區塊的豁免等同於資料檔案的豁免。

註釋
[svg]不將資料區塊定義成出版品，但如果未來更新新增了這概念，也可適用作為特例。

3.6 資源位址

EPUB製作者可以將以下出版品資源類型置放於EPUB容器之外：

聲音資源。

影片資源。

透過腳本APIs取得的資源（也就是透過XmlHttpRequest[xhr]與Fetch[fetch]）。

字型資源。

EPUB製作者必須將所有其他的資源儲存在EPUB容器內。

強烈建議只要可行，盡量將所有資源儲存在EPUB容器內，才能無論連線狀態都能讓使用者存取到所有的內容。

要是資源必須被置放到EPUB容器之外，推薦EPUB製作者透過安全https URI綱要[rfc7230]來參照，以限制出版品及使用者曝露在網路攻擊的威脅下。閱讀系統可能無法載入使用不安全綱要，像是http參照的遠端資源。

這些供出版品資源的定址規則適用於所有資源，無論是核心媒體類型資源或者外圍資源。

註釋
請參見remote-resources特性以獲得更多如何指出一個宣告 item中有參照遠端資源的資訊。

範例 1: 參照一個容器資源
在本範例中，一個位於EPUB容器內的聲音檔案透過[html]audio元素參照。

<html …>
   …
   <body>
      …
      <audio
          src="audio/ch01.mp4"
          controls="controls"/>
      …
   </body>
</html>
範例 2: 參照一個遠端資源
在本範例中，一個位於網頁上的聲音檔案透過[html]audio元素參照。

<html …>
   …
   <body>
      …
         <audio
             src="http://www.example.com/book/audio/ch01.mp4"
             controls="controls"/>
      …
   </body>
</html>
3.7 資料URLs

data: URL綱要[rfc2397]用於把資源直接編碼到一個URL字串中。本綱要的優勢為可以讓EPUB製作者在一份資源中嵌入另一份資源，而避免需要另一個外部檔案。

EPUB製作者不得以如下方式使用資料URLS，因為這樣會影響頂層內容文件或者頂層瀏覽脈絡[html]：

在包裝文件的href屬性中使用─同時適用於宣告item元素以及後設資料link元素；

在[html]或[svg] a元素的href屬性中使用─除了位於一個[html]iframe元素中；

在[html]area元素的href屬性中使用，除了位於一個iframe元素中時；

呼叫到[ecmascript]的window.open或 document.open。

註釋
這些使用資料URLs的限制是為了避免安全問題，也確保閱讀系統能決定要把使用者帶到何處（也就是因為資料URLs無法在書脊中被參照）。

避免使用資料URLs的列表會隨著相關標準在用途上的進化而有所變更。

嵌入的結果就是在資料URL中的資料不被當作一個獨特的出版品資源供宣告報告用途（也就是僅列於包含該資料的出版品資源）。由於該資料有自己的媒體類型，所以還是需要符合外圍資源的規定。EPUB製作者必須將資料URLs編碼成核心媒體類型資源或者使用主格式的固有回退機制提供回退。

3.8 檔案URLs

file: URL綱要定義於[rfc8089]，意義為「位於主機上一個結構化物件命名與存取環境（一個「檔案系統」）中儲存的物件（一個「檔案」）識別使用。」一般用於從本機作業系統取得檔案。

在可能於多個主機間轉移的EPUB出版品裡使用檔案URL，會面對安全風險，同時也不互通。結果上而言，EPUB製作者不得在EPUB出版品中使用檔案URLs。

3.9 XML符合性

所有基於XML媒體資源[rfc2046]的出版品資源都該：

必須為合規的XML 1.0文件，如合規性文件[xml-names]所定義。

可以僅指定一個文件類型宣告，其參照符合其媒體類型的外部識別碼─如B. 允許使用的外部識別碼所定義─或者忽略外部識別碼[xml]。

不得在內部DTD子集[xml]中包含外部實體宣告。

不得利用XInclude [xinclude]。

必須以UTF-8或UTF-16[unicode]編碼，推薦編碼為UTF-8。

以上限制適用於核心媒體類型資源或外圍資源的出版品資源。

註釋
[html]與[svg]正在移除對XML base屬性[xmlbase]的支援。EPUB製作者應該避免使用該特色。

4. 開放容器格式（OCF）

4.1 介紹

本節不具規範性。

OCF為EPUB出版品必須的容器技術。OCF可以在以下工作流程中扮演角色：

在製作EPUB出版品的準備階段，OCF可以被作為容器格式使用，用於將製作途中的出版品在不同個人以及/或者不同組織間傳送。
當一本EPUB出版品從出版社或者製作公司處提供到配布或銷售通路，OCF則為推薦的容器格式作為運輸格式使用。
當將最終版EPUB出版品地送到EPUB閱讀系統或給使用者時，容器必須使用OCF格式以掌握構成出版品的所有素材。
本章節定義以抽象方式建構檔案集合的規則：「抽象容器」。也定義了在一個ZIP封存檔中呈現本抽象容器的規則：「物理容器」。ZIP物理容器的規則建構於由[odf]使用的ZIP技術。

OCF也定義了標準化手段供嵌入字型模糊化使用，在EPUB出版品需要這項功能時可使用。

4.2 OCF抽象容器

4.2.1 介紹

本節不具規範性。

OCF抽象容器檔案系統模型使用單一通用根目錄。所有容器資源都位於根目錄下面的目錄樹中，但本規格不強制規定所使用的檔案系統結構。

檔案系統模型也包含著一個強制性的目錄，名為META-INF，其直接位於根目錄下子目錄，用於存放以下特殊檔案：

container.xml [必要]
識別一或多份包裝文件，其用於定義EPUB出版品。

signatures.xml [選擇性]
包含供各種資產使用的數位簽章。

encryption.xml [選擇性]
包含關於出版品資源加密的資訊。當EPUB製作者使用字型模糊化時，本檔案為必須。

metadata.xml [選擇性]
用來存放關於OCF ZIP容器的後設資料。

rights.xml [選擇性]
用於存放數位權利的資訊。

manifest.xml [選擇性]
由開放文件格式[odf]所允許的容器內容宣告。

請參見4.2.6 META-INF目錄以獲得在META-INF目錄中各種檔案的合規性規定。

4.2.2 檔案與目錄結構

供OCF抽象容器使用的虛擬檔案系統必須擁有單一通用根目錄供容器中的所有內容使用。

OCF抽象容器必須包含一個名為META-INF的目錄來置放設定檔案，其為容器根目錄的直接子目錄。請參見4.2.6 META-INF目錄以獲得該目錄內容的規定。

根目錄下保留檔案名稱mimetype供OCF ZIP容器使用，如4.3 OCF ZIP容器所說明。

EPUB製作者可以將所有其他的檔案放在OCF抽象容器中，根目錄以下的任何位置，但不該放在META-INF目錄中。EPUB製作者不得在EPUB出版品中參照META-INF目錄中的檔案。

註釋
有些閱讀系統不提供對包裝文件所在目錄之外資源的存取。EPUB製作者因而得將所有資源放到包裝文件所在的目錄，或者該目錄之下層，以避免互通性問題。

本問題在為出版品創建多重內容釋義[epub-multi-rend-11]時經常會遇到。

4.2.3 檔案路徑與檔案名稱

在OCF抽象容器脈絡下，檔案路徑與檔案名稱為scalar值字串[infra]（即為，其值需區分大小寫）。

此外設計了以下限制能讓檔案路徑與檔案名稱在多數作業系統中無需修改即可使用：

檔案名稱不得超過255位元組（byte）。

OCF抽象容器中任何目錄或檔案的檔案路徑不得超過65535位元組。

檔案名稱不得使用以下[unicode]字元，主要因為常見的作業系統對這些字元的支援不穩定：

SOLIDUS: / (U+002F)

QUOTATION MARK: " (U+0022)

ASTERISK: * (U+002A)

FULL STOP作為最後一個字元: . (U+002E)

COLON: : (U+003A)

LESS-THAN SIGN: < (U+003C)

GREATER-THAN SIGN: > (U+003E)

QUESTION MARK: ? (U+003F)

REVERSE SOLIDUS: \ (U+005C)

VERTICAL LINE: | (U+007C)

DEL (U+007F)

C0 range (U+0000 … U+001F)

C1 range (U+0080 … U+009F)

Private Use Area (U+E000 … U+F8FF)

所有Unicode非字元，尤其是：

基本多語種平面（Basic Multilingual Plane）中32個連續的字元，位於(U+FDD0 … U+FDEF)

基本多語種平面的最後兩個碼點 (U+FFFE及U+FFFF)

補充平面（Supplementary Planes）的最後兩個碼點(U+1FFFE, U+1FFFF … U+EFFFE, U+EFFFF)

虛缺號(U+FFF0 … U+FFFF)

補充私用區-A（Supplementary Private Use Area-A） (U+F0000 … U+FFFFF)

補充私用區-B（Supplementary Private Use Area-B）(U+100000 … U+10FFFF)

註釋
Unicode字元資料庫[uax44]也包含了一份不再推薦使用的字元列表。建議EPUB製作者避免使用這些字元，同時也希望EPUB符合性檢驗工具能偵測這些字元的使用。

為相容於較舊的閱讀系統，檔案名稱不應包含SPACE (U+0020)字元。

所有在同一個目錄中的檔案名稱必須在遵從Unicode等價正規化（canonical normalization）[uax15]，以及完整大寫轉換（case folding）[unicode]後為獨特（請參見Unicode等價大寫轉換正規化[charmod-norm]步驟以獲得更多資訊）。

註釋
如果EPUB製作者動態地整合資源（也就是命名不受控制），他們應該注意自動截斷檔案名稱以符合255位元組的限制會造成崩潰。主要是因為在像UTF-8這樣的多位元編碼中，位元組與字元有所差異，因此重要的是避免截斷中間字元。請參見[international-specs]中「截斷或限制字串長度」章節以獲得更多資訊。

註釋
當內容的相容性為關鍵時，EPUB製作者應該在檔案命名時得外小心。限制使用字元的列表用於協助避開一些已知的問題領域，但其無法確保所有其他的Unicode字元都受到支援。儘管 現在Unicode的支援已經比EPUB早先版本來得好，但在舊的工具以及工具鏈上還是可能遇到問題（像是僅支援[us-ascii]的ZIP工具）。

4.2.4 取得檔案路徑

若要取得檔案路徑，其位於OCF抽象容器中檔案或者目錄file，可按照以下步驟（使用[infra]中的術語）：

讓path為空白列表。
讓current為file。
當current不是根目錄時：
在path之前加入current的檔案名稱；
將current設定到current的母目錄。
輸入U+002F (/)字元以連結path。
4.2.5 OCF抽象容器中的URL

容器的根URL為根目錄的URL[url]。這是專供實作的資訊，但EPUB製作者必須認為其符合以下特性：

解析與容器根URL出現的「/」，結果須視為base為容器根URL。
解析與容器根URL出現的「..」，結果須視為base為容器根URL。
在OCF抽象容器中檔案或目錄的內容URL，為把容器根URL當做base，解析檔案的檔案路徑的結果。

註釋
容器根URL為閱讀系統指定到EPUB容器之根的URL。一般得看閱讀系統內部對容器檔案系統如何實作。

然而，閱讀系統不能任意地使用任何URL，但推薦符合以上定義的規則。這些規則確保任何EPUB中能找到的相對路徑URL字串一直都能被處理到容器內資源的URL（該資源可能存在或不存在）。這些限制的主要原因是避免潛在的run-time安全問題，可能會在把URL處理到容器檔案以外時發生「溢位（leaking）」。

例如，像這樣的URLs https://localhost:12345/或 https://www.example.org:12345/ 尊重這些特性。但像這樣的URLs https://localhost:12345/path/to.epub/ 、file:///path/to.epub#path=/、或jar:file:/path/to.epub!/EPUB/則不（處理以上三個範本URL字串".."時會分別給回https://localhost:12345/path/、file:///path/、以及處理錯誤）。所以閱讀系統有責任將URL指派到根目錄以遵從以上定義的特性。

註釋
處理時可能會將檔案路徑中的一些字元以其百分比號編碼取代。例如A/B/C/file name.xhtml會變成A/B/C/file%20name.xhtml。

當字串url為一個路徑-相對-無-綱要-位址（path-relative-scheme-less-url）字串時，就是一個合規-相對-ocf-位址-有-斷片（valid-relative-ocf-URL-with-fragment）字串，選擇性地在一個 U+0023 (#)與url-斷片（url-fragment）字串之後，且如果以下步驟回報為true：

將容器根URL設定為https://a.example.org/A/。

說明
按照url使用時的脈落定義（文件或者環境），並且參考包裝文件的內容URL，讓base設定為處理url時必要的基底URL（base URL）。（請參見5.2 解析包裝文件中的URL）。

說明
套用URL解析器處理url包括base時，讓testURLRecord作為其結果。
套用URL序列器（Serializer）處理testURLRecord時，讓testURLStringA作為其結果。
將容器根URL設定為https://b.example.org/B/。

說明
按照url使用時的脈落定義（文件或者環境），並且參考包裝文件的內容URL，讓base設定為解析url時必要的基底URL（base URL）。（請參見5.2 解析包裝文件中的URL）。
套用URL解析器處理url包括base時，讓testURLRecord作為其結果。
套用URL序列器（Serializer）處理testURLRecord時，讓testURLStringB作為其結果。
當testURLStringA不由https://a.example.org/開頭，或者testURLStringB不由https://b.example.org/開頭，回報為true。

說明
當testURLStringA由https://a.example.org/A/開頭，或者testURLStringB由https://b.example.org/B/開頭，回報為true。

說明
回報為false。
在OCF抽象容器中，任何URL字必須為一個絕對-位址-具-斷片（absolute-url-with-fragment）字串或者為一個有效的合規-相對-ocf-位址-有-斷片（valid-relative-ocf-URL-with-fragment）字串。

此外，所有相對-位址-具-斷片（relative-URL-with-fragment）字串[url]在解析之後，必須等於OCF抽象容器中一個存在檔案的內容URL。

註釋
這些對於URL字串的限制意味著：

不允許使用由一個/ (U+002F)開始的相對URL字串（例如/EPUB/content.xhtml）。
不允許使用包含多於到目標檔案的雙點路徑段落（例如EPUB/../../../../config.xml）；
允許其他絕對或相對的URL字串。
請注意在任何狀況中，就算以上說明中不允許的URL字串，在處理後都不會「溢位」容器之外（如本章節第一個註釋所說明）。但為了對不合規或者遺存的閱讀系統與工具鏈也能提供良好的互通性，依然不允許使用。

範例 3: 在同一個目錄中參照檔案
在本範例中，檔案image1.jpg和XHTML內容文件位於同一個資料夾。

<html …>
   …
   <body>
      <img
          src="image1.jpg"
          alt="…" />
   …
   </body>
</html>
範例 4: 一個「外於容器（out-of-container）」的URL
如以下容器結構：

/
├── mimetype
├── META-INF
│   └── container.xml
└── EPUB
    └── content.xhtml
content.xhtml中的URL../../../../EPUB/secret.xhtml透過閱讀系統解析成內容URL後的路徑為EPUB/secret.xhtml，遵循容器根URL的規定。然而該URL還是會被視為一個外於容器的資源，並且產生互通性問題；這會被檢驗工具回報為錯誤。

4.2.6 META-INF目錄

4.2.6.1 包含在OCF抽象容器中

所有OCF抽象容器必須在其根目錄中包含一個稱為META-INF的資料夾。

該資料夾保留供設定檔案，特別是4.2.6.3 保留的檔案中所定義的檔案。

4.2.6.2 解析META-INF目錄中的URL

解析位於META-INF目錄中檔案裡頭的URL字串url時，URL解析器必須套用到url，同時其容器根URL為base。

範例 5: 在容器檔案中解析路徑
如果容器檔案（META-INF/container.xml）有以下內容：

<?xml version="1.0"?>
<container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <rootfiles>
      <rootfile
          full-path="EPUB/Great_Expectations.opf"
          media-type="application/oebps-package+xml" />	
   </rootfiles>
</container>
該路徑code>EPUB/Great_Expectations.opf相對於OCF抽象容器的根目錄，而不相對於META-INF目錄。

4.2.6.3 保留的檔案

4.2.6.3.1 容器檔案（container.xml）

META-INF目錄中需要的container.xml檔案用於在OCF抽象容器中識別可取得的包裝文件。

所有在本章節中定義的[xml]元素，除非有另外指定，都位於urn:oasis:names:tc:opendocument:xmlns:container命名空間[xml-names]裡。

本檔案的內容必須在移除所有來自其他命名空間的元素與屬性（包括這些元素的所有屬性與內容）後，合乎本章節的定義。

註釋
有一份XML綱要非正式地定義了本檔案的內容。
4.2.6.3.1.1 container元素

container元素封裝了所有位於container.xml檔案中的資訊。

元素名稱：
container

用途：
container.xml檔案中需要的根元素[xml]。

屬性：
version [必要]
本屬性值必須為「1.0」。
內容模型：
按此順序：

rootfiles [唯一]
links [0或1]
4.2.6.3.1.2 rootfiles元素

rootfiles元素包含EPUB容器中可以取得的包裝文件列表。

元素名稱：
rootfiles

用途：
container需要的的第一個子元素。

屬性：
無

內容模型：
rootfile [1或多個]
4.2.6.3.1.3 rootfile元素

每一個rootfile元素用於識別EPUB容器中一份包裝文件的位址。

元素名稱：
rootfile

用途：
作為rootfiles元素的子元素。可以重複。

屬性：
full-path [必要]
識別包裝文件位址。

該屬性的值必須為路徑-相對-無-綱要-位址（path-relative-scheme-less-URL）字串[url]。該路徑相對於根目錄。

media-type [必要]
識別包裝文件的媒體類型。

該屬性的值必須為「application/oebps-package+xml」。

內容模型：
空白

如果EPUB製作者定義了多於一個的rootfile元素，每一個都必須參照一份內容文件，且合規於相同版本的EPUB。每一份內容文件代表EPUB出版品的一種處理。

註釋
儘管EPUB容器提供參照多於一個內容文件的能力，本規格不定義如何詮釋或者選擇可取得的選項。請參見[epub-multi-rend-11]以獲得更多關於如何包入多於一種內容處理的方式。

4.2.6.3.1.4 links元素

links元素用於識別處理OCF ZIP容器所必要的資源。

元素名稱：
links

用途：
container選擇性的第二個子元素。可以重複。

屬性：
無

內容模型：
link [1或多個]
註釋
本規格目前不定義links元素的用途。請參見[epub-multi-rend-11]以獲得應用範例。

4.2.6.3.1.5 link元素

元素名稱：
link

用途：
作為links元素的子元素。可以重複。

屬性：
href [必要]
識別資源所在位址。

link元素href屬性的值必須為路徑-相對-無-綱要-位址（path-relative-scheme-less-URL）字串 [url]。該路徑相對於根目錄。

media-type [選擇性]
用於識別參照的資源的類型與格式。

本屬性的值必須為一個媒體類型[rfc2046]。

rel [必要]
識別與資源的關係。

本屬性的值必須為由空白分隔的令牌列表。

內容模型：
空白

4.2.6.3.1.6 範例

本節不具規範性。

範例 6: 一份基本的容器檔案
<?xml version="1.0"?>
<container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <rootfiles>
      <rootfile
          full-path="EPUB/My_Crazy_Life.opf"
          media-type="application/oebps-package+xml" />
   </rootfiles>
</container>
4.2.6.3.2 加密檔案（encryption.xml）

META-INF目錄中選擇性的 encryption.xml檔案掌握容器中所有內容的加密資訊。如果EPUB製作者將容器中任何資源加密，他們必須包含一份encryption.xml檔案以提供關於使用加密的資訊。

4.2.6.3.2.1 encryption元素

元素名稱：
encryption

命名空間：
urn:oasis:names:tc:opendocument:xmlns:container

用途：
encryption.xml檔案中需要的根元素[xml]。

屬性：
無

內容模型：
以任何順序：

EncryptedKey [1或多個]
EncryptedData [1或多個]
encryption元素包含的子元素EncryptedKey與 EncryptedData，其類型由[xmlenc-core1]所定義。

EncryptedKey元素描述了容器中使用的每一個加密密鑰，而EncryptedData元素描述了每一個加密後的檔案。每一個 EncryptedData元素對應參照一個EncryptedKey元素，如XML加密中所描述。

註釋
有一份XML綱要非正式地定義了encryption.xml檔案的內容。s
OCF獨立加密個別檔案，捨棄一些安全性以換得更好的性能，也允許容器內容可以被增量解密。以這種方式加密也會暴露整個包裝的目錄結構與檔案命名。

OCF使用XML加密[xmlenc-core1]以提供一個加密框架，允許使用各種不同的演算法。XML加密指定了對任意資料的加密程序，並以XML呈現其結果。儘管一個OCF抽象容器可能包含非XML資料，EPUB製作者可以使用XML加密對OCF抽象容器中的所有資料加密。OCF加密僅支援對容器內整個檔案加密，而無法用於一部分的檔案。EPUB製作者在有encryption.xml檔案時，不得對其加密。

加密後的資料會在OCF抽象容器中取代未加密的資料。舉個例子，當EPUB製作者加密一個名為photo.jpeg的圖片檔，他們應該以加密後的內容取代photo.jpeg資源的內容。在ZIP目錄中，EPUB製作者應該儲存加密後的檔案而不使用Deflate方式壓縮這些檔案。

請注意在一些狀況中需要對EPUB出版品所參照、儲存於其中的嵌入字型進行模糊化，以讓這些自行難以被抽出供非限制的使用。儘管模糊化並非加密，閱讀系統使用encryption.xml連結字型模糊化演算法供指定字型去模糊化。

EPUB製作者不得加密以下檔案：

mimetype
META-INF/container.xml
META-INF/encryption.xml
META-INF/manifest.xml
META-INF/metadata.xml
META-INF/rights.xml
META-INF/signatures.xml
[= package document =]
EPUB製作者可以使用供XML簽章[xmlenc-decrypt]的解密轉換（Decryption Transform）來加密簽署的資源。這項功能讓閱讀系統可以區別簽署前加密的資料與簽署後加密的資料。

範例 7: 一張加密的圖片
在本範例中，採用了[xmlenc-core1]章節2.2.1，資源image.jpeg使用對稱密鑰演算法（AES）加密，對稱密鑰更近一步使用非對稱密鑰演算法（RSA）加密，其密鑰為「John Smith」。

<encryption
    xmlns ="urn:oasis:names:tc:opendocument:xmlns:container"
    xmlns:enc="http://www.w3.org/2001/04/xmlenc#"
    xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
   <enc:EncryptedKey Id="EK">
      <enc:EncryptionMethod
          Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-1_5"/>
      <ds:KeyInfo>
         <ds:KeyName>
            John Smith
         </ds:KeyName>
      </ds:KeyInfo>
      <enc:CipherData>
         <enc:CipherValue>
            xyzabc
         </enc:CipherValue>
      </enc:CipherData>
   </enc:EncryptedKey>
   <enc:EncryptedData Id="ED1">
      <enc:EncryptionMethod
          Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
      <ds:KeyInfo>
         <ds:RetrievalMethod
             URI="#EK"
             Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
      </ds:KeyInfo>
      <enc:CipherData>
         <enc:CipherReference
             URI="image.jpeg"/>
      </enc:CipherData>
   </enc:EncryptedData>
</encryption>
4.2.6.3.2.2 壓縮與加密順序

當儲存在OCF ZIP容器中時，EPUB製作者應該在加密前，對非編碼（non-codec）內容類型資料流進行壓縮。EPUB製作者必須使用Deflate方式壓縮。這種作法確保存放在ZIP容器中的檔案項目佔用較少的空間。

EPUB製作者不應在加密壓縮編碼（codec）內容類型資料流前進行壓縮。在這些案例中額外的壓縮會造成不必要的處理程序延長製作時間（尤其在處理大型資源檔案時）並且在閱讀時影響影音播放效能。在某些案例中某些加密綱要遇上壓縮時，可能會降低閱讀系統處理部分內容要求的能力（例如HTTP位元組範圍byte range），原因是技術上無法在媒體播放前判斷完整資源的長度（例如HTTP內容長度檔頭Content-Length header）。

當EPUB製作者在加密前壓縮資料流時，他們應該提供額外的EncryptionProperties後設資料來指定資源初始大小（即為，在壓縮與加密之前），如以下定義的Compression XML元素。當EPUB製作者不在加密前壓縮資料流時，他們可以提供額外的EncryptionProperties後設資料來指定初始資源初始大小（即為，在壓縮之前）。

元素名稱：
Compression

命名空間：
http://www.idpf.org/2016/encryption#compression

用途：
EncryptionProperty選擇性的子元素。

屬性：
Method [必要]
識別所使用的壓縮法。

值需為「0」（無壓縮）或「8」（Deflate演算法）。

OriginalLength [必要]
代表資源初始大小（位元組數）。

值為正整數。

內容模型：
空白

範例 8: 一段壓縮的影片
在本範例中，EPUB製作者以Deflate方式壓縮MP4檔案，其原來大小為3500000位元組。

<encryption
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <enc:EncryptedData 
       xmlns:enc="http://www.w3.org/2001/04/xmlenc#">
      …
      <enc:CipherData>
         <enc:CipherReference
             URI="OEPBS/video.mp4"/>
      </enc:CipherData>
      <enc:EncryptionProperties>
         <enc:EncryptionProperty
             xmlns:ns="http://www.idpf.org/2016/encryption#compression">
            <ns:Compression
                Method="8"
                OriginalLength="3500000"/>
         </enc:EncryptionProperty>
      </enc:EncryptionProperties>
      …
   </enc:EncryptedData>
</encryption>
4.2.6.3.3 宣告檔案（manifest.xml）

META-INF目錄中選擇性的manifest.xml檔案，提供容器裡檔案的宣告。

OCF規格不強制指定宣告的格式。

請注意在 包裝文件僅指定用於處理EPUB出版品的宣告。閱讀系統不使用本檔案。

註釋
本功能的存在僅為了相容於[odf]。
4.2.6.3.4 後設資料檔案（metadata.xml）

META-INF目錄中選擇性的metadata.xml檔案，僅用於容器層級的後設資料。

如果EPUB製作者包含一個metadata.xml檔案，他們應該僅使用符合命名空間的元素[xml-names]在其中。該檔案應該包含根元素[xml]metadata，位於命名空間http://www.idpf.org/2013/metadata，但本規格允許其他根元素以能向後相容。

本版本的規格不定義供metadata.xml檔案使用的後設資料。本規格的未來版本可以定義容器層級的後設資料。

4.2.6.3.5 權利管理檔案（rights.xml）

本規格在META-INF目錄中保留選擇性的rights.xml供EPUB出版品在權利擁有人、中間人與使用者間做到可被信任的交換。

當EPUB製作者沒有包含rights.xml檔案時，在容器層級上，OCF抽象容器沒有任何部分受到權利管控。但EPUB出版品內可能會有權利表述存在。

4.2.6.3.6 數位簽章檔案（signatures.xml）

註釋
增添數位簽章並不能確保惡意行為者不能竄改EPUB出版品，原因是閱讀系統不強制要確認簽章。

META-INF目錄中選擇性的signatures.xml檔案掌握容器及其內容的數位簽章。

4.2.6.3.6.1 signatures元素

元素名稱：
signatures

命名空間：
urn:oasis:names:tc:opendocument:xmlns:container

用途：
signature.xml檔案中需要的 根元素[xml]。

屬性：
無

內容模型：
Signature [1或多個]
signatures元素中包含了各類Signature的子元素，如[xmldsig-core1]所定義。EPUB製作者可以將簽章套用於EPUB出版品整體或者其部分，也能夠指定簽署任何種類的資料（也就是不限XML）。

註釋
有一份XML綱要非正式地定義了signatures.xml檔案的內容。
當EPUB製作者未包含signatures.xml檔案時，代表在容器層級OCF抽象容器沒有任何部分受到簽署。EPUB出版品內可能存在數位簽章。

當EPUB製作者為OCF抽象容器建立資料簽章時，他們應該將該簽章添加到signatures元素的最後一個子Signature

註釋
在signatures.xml檔案中的每一個Signature由URL[url]識別簽章適用於哪一份資料，使用[xmldsig-core1]Manifest元素以及其Reference 副元素。EPUB製作者可以分別獲一起簽署獨立的容器檔案。為每個檔案分別簽署可為資源創建摘要值，供閱讀系統獨立驗證使用。這種作法可能讓Signature元素較大。若EPUB製作者將檔案一齊簽署，他們可以在單一XML Signature Manifest元素中列出整組簽署的檔案，並透過一個以上的Signature元素進行參照。

EPUB製作者可以簽署整體OCF抽象容器的任何或者全部檔案，除了signatures.xml檔案，因為該檔案將包含計算過的簽章資訊。EPUB製作者是否以及如何簽署signatures.xml檔案按照其目的而定。

如果EPUB製作者希望簽章在被添加或從OCF抽象容器移除時無需對簽章進行驗證，他們 不應簽署signatures.xml檔案。

如果EPUB製作者希望簽章在被添加或移除時，要簽章進行驗證的話，他們可以使用定義在[xmldsig-core1]章節6.6.4的Enveloped Signature transform方式簽署整個預先存在的簽章檔案，但將要創建的Signature除外。這種轉換可以簽署所有之前的簽章，並且在包裝中加入新的簽章時變得失效。

註釋
如果EPUB製作者希望移除既有的簽章時不需對簽章進行驗證，但也希望能夠新增簽章，他們可以使用XPath transform來對存在的簽章進行簽署。然而，像這種轉換的細節並非本規格的目標。

[xmldsig-core1]規格並沒有為簽章關聯任何語義；使用者端可以包含語義資訊，例如，添加資訊到一個Signature元素來解釋該簽章。[xmldsig-core1]規格解釋了如何為簽章添加額外資訊，像是使用SignatureProperties元素。

範例 9: 簽署資源
在本範例中，基於[xmldsig-core1]第二章中的範本，一個簽章可套用到兩個資源上（EPUB/book.xhtml與EPUB/images/cover.jpeg）。

<signatures
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <Signature
       Id="sig"
       xmlns="http://www.w3.org/2000/09/xmldsig#">
      <SignedInfo>
         <CanonicalizationMethod 
             Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
            <SignatureMethod
                Algorithm="http://www.w3.org/2000/09/xmldsig#dsa-sha1"/>
            <Reference
                URI="#Manifest1">
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>j6lwx3rvEPO0vKtMup4NbeVu8nk=</DigestValue>
            </Reference>
      </SignedInfo>
      <SignatureValue>
         …
      </SignatureValue>
      <KeyInfo>
         <KeyValue>
            <DSAKeyValue>
               <P>…</P>
               <Q>…</Q>
               <G>…</G>
               <Y>…</Y> 
            </DSAKeyValue>
         </KeyValue>
      </KeyInfo>
      <Object>
         <Manifest
             Id="Manifest1">
            <Reference
                URI="EPUB/book.xhtml">                    
               <Transforms>                                                
                  <Transform
                      Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>                        
               </Transforms>
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>…</DigestValue>
            </Reference>
            <Reference URI="EPUB/images/cover.jpeg">
               <Transforms>                                                
                  <Transform
                      Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>                        
               </Transforms>
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>…</DigestValue>
            </Reference>
         </Manifest>
      </Object>
   </Signature> 
</signatures>
4.3 OCF ZIP容器

4.3.1 介紹

本節不具規範性。

OCF ZIP容器為OCF抽象容器的物理單一檔案表徵。該容器可用於：

在不同個人以及/或者不同組織間，交換製作中的EPUB出版品；

從出版社或者製作公司處傳遞EPUB出版品到配布或銷售通路，；以及

將EPUB出版品遞交到 EPUB閱讀系統或使用者處。

4.3.2 ZIP檔案規定

OCF ZIP容器使用[zip]所敘述的ZIP格式，但有著以下限制與說明：

OCF ZIP容器的內容 必須為合規的OCF抽象容器。

OCF ZIP容器不得使用ZIP應用程式附註[zip]中的功能以讓ZIP檔案跨多個儲存媒介或者分割成多個檔案。

OCF ZIP容器必須在ZIP封存檔中僅包括儲存（無壓縮的）以及使用Deflate方式壓縮的ZIP資料。

OCF ZIP容器可以使用定義在ZIP應用程式附註[zip]章節V，子章節G「version 1」的ZIP64延伸，以及應該僅在內容需要時使用這些延伸。

OCF ZIP容器不得使用定義在ZIP格式中的加密功能；相對之下，加密必須使用在4.2.6.3.2 加密檔案（encryption.xml）中說明的功能。

OCF ZIP容器必須使用UTF-8[unicode]編碼檔案系統名稱。

以下限制適用於OCF ZIP容器封存檔的特定領域：

在本機檔案檔頭表格中EPUB製作者必須將version needed to extract欄位的值設定為10、20或45，以符合該檔案所需的最大版本等級（例如使用Deflate方式為20、使用ZIP64為45）。

在本機檔案檔頭表格中，EPUB製作者必須將compression方法欄位設定為0或8。

4.3.3 OCF ZIP容器媒體類型識別

EPUB製作者必須在OCF ZIP容器內包含mimetype檔案並作為第一個檔案。此外：

mimetype檔案的內容必須為MIME媒體類型[rfc2046]字串application/epub+zip，以US-ASCII[us-ascii]編碼。
mimetype檔案不得包含任何開頭或結尾的縮排或者空白。
mimetype檔案不得以Unicode位元組順序符號U+FEFF開頭。
EPUB製作者不得對mimetype檔案壓縮或者加密。
EPUB製作者不得在其ZIP檔頭包含額外的領域。
註釋
請參見 I.2 application/epub+zip媒體類型以獲得更多關於application/epub+zip媒體類型的資訊。

4.4 字型模糊化

警告事項
目前有更好保護字型的方法。例如，[woff]以及[woff2]都允許嵌入授權資訊以及透過壓縮字型表格的方式來提供一些保護。也能將遠端託管的字型作為子集使用。建議EPUB製作者只有在沒有其他可用的選項時，才使用本章節定義的字型模糊化手段。請參見模糊化限制。

4.4.1 介紹

本節不具規範性。

由於OCF ZIP容器基本上是一個ZIP檔案，一般可取得的ZIP工具能用來解壓包裝中任何未加密的內容流。此外ZIP檔案的性質表示其內容在某些系統上可能會以如原生容器一般顯示（例如，一個資料夾的方式）。

雖然ZIP檔案的簡潔性相當有用，但也會面對一個問題：由於沒加密，所以可以簡單地取出其中的字型檔，這是預期外的副作用。EPUB製作者如果想要包含第三方字型在其中的話，一般不希望字型被取出且由其他人使用。更重要的是，許多商售字型允許嵌入，但是將字型嵌入意味著要讓其成為EPUB出版品整合的一部分，而不是隨著內容一併提供原始字型檔案。

由於現代的作業系統多數整合了對ZIP的支援，所以只是把字型放到OCF ZIP容器 不足以表示字型無法被重新用於其他脈絡。這種不確定性會影響原本EPUB出版品很有用的字型嵌入能力。

字型商不希望自己的字型被作為他用，一些可能允許應用於EPUB出版品，但字型用於EPUB出版品時有其他限制。例如，字型檔案不能被以內建的工具直接安裝到電子設備的作業系統使用，以及不能直接被其他EPUB出版品使用。

提供數位權利管理或者字型的強制性系統並非本規格之目標。本章節另外定義了模糊化方法，其需要對最終OCF容器做額外的工夫才能對任何模糊化後的字型獲得一般的存取權。

4.4.2 限制

本節不具規範性。

本規格不宣稱模糊化可取代加密，也不保證能讓資源免於受到侵權。僅希望本演算法能夠符合字型提供者之需求，也就是確保字型不會輕易地透過解壓縮OCF ZIP容器即可複製出資源。

模糊化就像任何保護用的綱要一般，不能完整保護字型免於在其去模糊化的狀態下被存取。這項機制僅對不清楚授權細節的人提供阻礙。但其無法避免有意圖的使用者透過其替代手段取得完整字型的存取權，像是：

利用去模糊化演算法取出原始字型檔案；
透過閱讀系統必須去模糊化才能處理內容的過程存取去模糊化的字型（例如透過基於瀏覽器的閱讀系統存取資源的過程）；或者
透過提供視覺化處理內容的製作工具以存取去模糊化的字型。
結論而言，這種模糊化方式是否能夠滿足個別字型授權的需求，依然是授權方與被授權方的問題。EPUB製作者有責任確保使用模糊化能合乎字型授權需求。

EPUB製作者也應該注意模糊化可能影響到閱讀系統間的互通性，因為不強制要求閱讀系統要對字型做去模糊化。結果來說，出版品視覺上的呈現可能會依閱讀系統不同而變化。

也請注意該演算法僅限制用於模糊化字型。並非可供模糊化EPUB容器中的任何資源使用的通用用途機制。

4.4.3 模糊化密鑰

EPUB製作者必須由其唯一識別碼生成用於模糊化所需的密鑰。

所有在XML 1.0規格2.3節中定義[xml]的所有空白字元，都必須由識別碼中移除─特別是Unicode碼點U+0020、U+0009、U+000D與U+000A。

EPUB製作者必須生成如安全雜湊標準（Secure Hash Standard）[fips-180-4]指定，以UTF-8表達的SHA-1摘要的結果字串。他們可以使用該摘要作為演算法的密鑰。

4.4.4 模糊化演算法

本演算法透過調整字型檔案最初1040位元組（~1KB）的方式來對字型進行模糊化。（雖然字型檔案不大可能少於1040位元組，但在這狀況裡，本程序會調整整個檔案。）

為了模糊化原始資料，結果上會對原始字型檔案的第一個位元組，以及模糊化密鑰的第一個位元組，進行「邏輯互斥或（logical exclusive or, XOR）程序，然後儲存在嵌入字型的第一個位元組。

並且將本程序重複在下一個來源的位元組與密鑰上，直到用完密鑰中的所有位元組。在這時間點程序繼續從密鑰的第一個位元組開始，以及來源的第21個位元組開始。當以這種方式完成1040位元組的編碼時（或者到達來源檔的結尾時），直接將來源剩下的資料複製到目標。

EPUB製作者 必須在壓縮或者將其加到 OCF ZIP容器前對字型進行模糊化。請注意模糊化並非加密，這項需求不會違反4.2.6.3.2 加密檔案（encryption.xml）中在加密前對字型進行壓縮的規定。

以下假代碼展示了模糊化演算法。

set ocf to OCF ZIP container file
set source to font file
set destination to obfuscated font file
set keyData to key for file
set outer to 0
while outer < 52 and not (source at EOF)
set inner to 0
while inner < 20 and not (source at EOF)
read 1 byte from source (Assumes read advances file position)
set sourceByte to result of read
set keyByte to byte inner of keyData
set obfuscatedByte to (sourceByte XOR keyByte)
write obfuscatedByte to destination
increment inner
end while
increment outer
end while
if not (source at EOF) then
read source to EOF
write result of read to destination
end if
Deflate destination
store destination as source in ocf
4.4.5 指定模糊化字型

儘管技術上並非對資料進行加密，所有模糊化字型必須在EPUB出版品中伴隨的encryption.xml中登錄（請見obfuscated fonts have an entry in the file accompanying the (see 4.2.6.3.2 加密檔案（encryption.xml））。

EPUB製作者必須為每一個模糊化字型指定一個EncryptedData元素。每一個EncryptedData元素必須包含一個EncryptionMethod子元素，其Algorithm屬性有值http://www.idpf.org/2008/embedding。本屬性存在指示使用了本規格所描述的演算法。

EPUB製作者 必須CipherDataa元素中的子CipherReference條列模糊化字型的路徑。由於模糊化演算法限制用於字型，CipherReference元素的URI屬性必須 參照一個字型的核心媒體類型資源。

範例 10: 一份模糊化字型的登錄資料
<encryption 
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container" 
    xmlns:enc="http://www.w3.org/2001/04/xmlenc#">
   <enc:EncryptedData> 
      <enc:EncryptionMethod
          Algorithm="http://www.idpf.org/2008/embedding"/> 
      <enc:CipherData> 
         <enc:CipherReference
             URI="EPUB/Fonts/BKANT.TTF"/>  
      </enc:CipherData> 
   </enc:EncryptedData>  
</encryption>
為了避免把嵌入字型無意義地複製到其他EPUB出版品中，EPUB製作者不得在encryption.xml檔案中提供模糊化密鑰。

5. 包裝文件

除另有指定外，所有定義在本章節的[xml]元素都位於http://www.idpf.org/2007/opf命名空間[xml-names]。

5.1 介紹

本節不具規範性。

包裝文件為一份XML文件，其包含了一組元素分別封裝了EPUB出版品個別面向的資訊。這些元素提供了集中化的後設資料，個別資源的細節，以及提供閱讀順序，還有其他處理上必要的資訊。

以下列表概述可在包裝文件中發現的資訊：

後設資料（Metadata）─用於包含以及/或者參照關於EPUB出版品資訊的機制。

宣告（manifest）─透過URL[url]識別、並且透過MIME媒體類型[rfc4839]描述出版品資源的集合。

書脊（spine）─透過ID參照到宣告中頂層資源的排列順序，閱讀系統可以透過頂層資源取得或者使用其他在集合中的資源。書脊定義了預設閱讀順序。

集合（Collections）─用於封裝以及識別EPUB出版品中子元素的方法。

宣告回退鏈（Manifest fallback chains）─為頂層資源的同等內容資源定義有順序列表的機制。閱讀系統可以其為基礎在其中選擇能夠處理的資源。

註釋
一本EPUB出版品可以參照多於一個的包裝文件，允許用於內容的替代表現。要獲得更多資訊，請參見4.2.6.3.1 容器檔案（container.xml）。

註釋
請參見I.1 application/oebps-package+xml媒體類型以獲得更多關於包裝文件檔案特性的資訊。

5.2 解析包裝文件中的URL

為了處理用於包裝文件的URL字串url，URL解析器[url]必須適用於url，並且將包裝文件的內容URL作為base。

5.3 共享的屬性

本章節提供共用屬性的定義（也就是允許用於兩個以上元素的屬性）。

5.3.1 dir屬性

指定文字內容以及使用該屬性元素與其子孫項的屬性值的基礎行文方向[bidi]。

允許使用的值為：

ltr─基礎行文方向由左而右；
rtl─基礎行文方向由右而左；以及
auto─基礎行文方向使用Unicode Bidi演算法[bidi]來進行判斷。
當EPUB製作者忽略該屬性或者使用無效的值時，閱讀系統可以假設其值為auto。

註釋
透過dir屬性指定基礎行文方向並不影響字元在其自有方向行文中的順序，只會影響這些行文的相對排序，以及方向性較弱的字元配置，如標點符號。

範例 11: 為包裝文件中的文字設定全域的行文方向
<package … dir="ltr">
   …
</package>
允許用於：collection、dc:contributor、dc:coverage、dc:creator, dc:description、dc:publisher、dc:relation、dc:rights、dc:subject、dc:title、meta以及package。

5.3.2 href屬性

一個合規的URL字串[url]用於參照資源。

URL字串 不得透過包裝文件中的元素參照資源（也就是透過宣告的code>item或者書脊的itemref 宣告）。

範例 12: 連結後設資料紀錄
<package …>
   <metadata …>
      …
      <link
          rel="record"
          href="meta/9780000000001.xml" 
          media-type="application/marc"/>
      …
   </metadata>
   …
</package>
允許用於：item以及link.

5.3.3 id屬性

元素的ID[xml]，其在整份文件中必須為唯一。

範例 13: 添加一個identifier屬性
<dc:title id="pub-title">The Lord of the Rings</dc:title>
允許用於：collection、dc:contributor、dc:coverage、dc:creator、dc:date、dc:description、dc:format、dc:identifier、dc:language、dc:publisher、dc:relation、dc:rights、dc:source、dc:subject、dc:title、dc:type、item、itemref、link、manifest、meta、package以及spine。

5.3.4 media-type屬性

媒體類型[rfc2046]用於指定參照資源的類型以及格式。

範例 14: 為連結的資料添加一個媒體類型
<package …>
   <metadata …>
      …
      <link
          rel="record"
          href="http://example.org/meta/12389347?format=xmp"
          media-type="application/xml"
          properties="xmp"/>
      …
   </metadata>
   …
</package>
允許用於：item以及link。

5.3.5 properties屬性

一份由空白分隔的特性值列表。

請參照各元素的定義，以取得供屬性使用的保留用語。

範例 15: 在宣告中識別EPUB導覽文件
<package …>
   …
   <manifest>
      …
      <item
          id="nav" 
          href="nav.xhtml"
          properties="nav"
          media-type="application/xhtml+xml"/>
      …
   </manifest>
   …
</package>
允許用於：item、itemref以及link。

5.3.6 refines屬性

為元素或者以該值識別的元素，建立與現行表述的關聯。EPUB製作者EPUB製作者 必須使用路徑-相對-無-綱要-位址（path-relative-scheme-less-URL）字串，選擇性地在U+0023 (#)之後，以及透過一個位址-斷片（URL-fragment）字串來參照其所描述的資源或者元素。

範例 16: 將一位製作者指定為插畫師
<package …>
   <metadata …>
      …
      <dc:creator id="creator02">
         E.H. Shepard
      </dc:creator>
      <meta
          refines="#creator02"
          property="role"
          scheme="marc:relators">
         ill
      </meta>
      …
   </metadata>
   …
</package>
refines屬性為選擇性，按照其表述的後設資料類型。當不存在時，該元素定義了主要表述。

當建立關於出版品資源的表述時，refines屬性應該指定一個斷片識別碼，其參照資源在宣告中登錄的ID[xml]。

精製鏈不得包含循環迴圈或者對自身的參照。

範例 17: 為媒體層疊文件設定長度
<package …>
   <metadata …>
      …
      <meta
          property="media:duration" 
          refines="#c01_overlay">
         0:32:29
      </meta>
      …
   </metadata>
   <manifest>
      …
      <item
          id="c01_overlay"
          href="overlays/chapter01.smil"
          media-type="application/smil+xml"/>
      …
   </manifest>
   …
</package>
允許用於：link 以及meta。

5.3.7 xml:lang屬性

指定文字內容以及使用該屬性元素與其子孫項的屬性值所使用的語言，如[xml]2.12節識別語言所定義。每一個xml:lang屬性的值必須為形式完整的語言標籤[bcp47]。

範例 18: 為包裝文件文字設定全域語言值
<package … xml:lang="ja">
   …
</package>
允許用於：collection、dc:contributor, dc:coverage、dc:creator、dc:description、dc:publisher、dc:relation、dc:rights、dc:subject、dc:title、meta以及package。

5.4 package元素

package元素封裝了所有在包裝文件中表述的資訊。

元素名稱：
package

用途：
包裝文件中需要的 根元素[xml]。

屬性：
dir [選擇性]

id [選擇性]

prefix [選擇性]

xml:lang [選擇性]

unique-identifier [必要]

version [必要]

內容模型：
按此順序：

metadata [唯一]

manifest [唯一]

spine [唯一]

guide [0或1] （遺存）

bindings [0或1] （不再推薦）

collection [0或多個]

version屬性指定該EPUB出版品合乎的EPUB規格版本。該屬性必須有值「3.0」以指出合乎EPUB 3。

註釋
本規格更新不代表為EPUB 3的新版本（也就是每一份新的3.X規格都是EPUB 3格式的延續）。工作小組致力於讓可能使既有內容變得不合規定的變更最小化，讓version屬性的值可以保持不變。

unique-identifier屬性使用一個IDREF [xml]以指向提供偏好、或者主要識別碼的dc:identifier元素。

prefix屬性為非本規格保留的字首提供一個宣告機制。請參見D.1.4 prefix屬性以獲得更多資訊。

5.5 區塊

5.5.1 metadata元素

metadata元素封裝了後設資訊。

元素名稱：
metadata

用途：
package需要的第一個子元素。

屬性：
無

內容模型：
以任何順序：

dc:identifier [1或多個]

dc:title [1或多個]

dc:language [1或多個]

都柏林核心集選擇性元素 [0或多個]

meta [1或多個]

OPF2 meta [0或多個] （遺存）

link [0或多個]

包裝文件 metadata元素有兩個主要功能：

提供最小限的後設資訊供閱讀系統使用，用於在內部對EPUB出版品分類以及讓使用者能夠取得（像是在書架上呈現）。

提供存取所有處理用的後設資料，其對內容顯示和版面控制而言為必要（例如固定版面特性）。

包裝文件不提供複雜的後設資料編碼能力。如果EPUB製作者需要提供更細節的資訊，他們可以使用link元素連結後設資料紀錄（也就是合乎如[onix]般的國際標準，或者供客製化用途建置）。這種作法允許閱讀系統以其原生形式處理後設資料，避免潛在問題以及在轉譯最小限包裝文件結構時的資訊丟失。

為維持這理路，包裝文件僅要求以下最小限度的後設資料：其必須包含[dcterms]dc:title、dc:identifier，以及dc:language 元素，還有[dcterms]dcterms:modified特性。其他所有後設資料都為選擇性。

範例 19: 包裝文件中最小限度的後設資料組合
<package … unique-identifier="pub-id">
    …
    <metadata …>
       <dc:identifier
           id="pub-id">
          urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809
       </dc:identifier>
       <dc:title>
          Norwegian Wood
       </dc:title>
       <dc:language>
          en
       </dc:language>
       <meta
           property="dcterms:modified">
          2011-01-01T12:00:00Z
       </meta>
    </metadata>
    …
</package>
meta元素提供了通用的機制來包含任何用語集的後設資料。一般用於包含定義在EPUB規格中的必要的處理用後設資料，但EPUB製作者可以將本機制用於任何後設資料用途。

註釋
請參見[epub-a11y-11]以獲得推薦的無障礙輔助後設資料。

5.5.2 Metadata值

都柏林核心集元素[dcterms]以及meta元素有著強制性的子文字內容[dom]。為了說明這些元素，本規格將這些內容視為元素的值。

這些元素必須在移除開頭與結尾的ASCII空白[infra]為非空白的值（也就是必須包含至少一個非空白字元）。

在這些元素值中的空白不具意義。在處理時一或多個空白字元的序列都會被結合視為一個空白[infra]。

5.5.3 都柏林核心集的必要元素

5.5.3.1 dc:identifier元素

dc:identifier元素[dcterms]包含如UUID、DOI或ISBN的識別碼。

元素名稱：
dc:identifier

命名空間：
http://purl.org/dc/elements/1.1/

用途：
metadata需要的子元素。可以重複。

屬性：
id [某些狀況為必要]

內容模型：
文字

EPUB製作者必須在一個dc:identifier元素中，提供唯一專屬於EPUB出版品的識別碼─唯一識別碼─該dc:identifier元素必須指定一個id屬性，其值參照package元素中的unique-identifier屬性。

範例 20: 指定一個元素為唯一識別碼
<package … unique-identifier="pub-id">
    <metadata …>
       <dc:identifier id="pub-id">
           urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809
       </dc:identifier>
       …
    </metadata>
</package>
儘管並非固定不變，EPUB製作者應該盡可能地不要變更一本EPUB出版品的唯一識別碼。唯一識別碼應該擁有最大限度的持續性，供參照與配送目的使用。EPUB製作者在進行小改版像是更新後設資料、修正錯字或者類似的小型修正時，不應發行新的識別碼。

EPUB製作者可以指定額外的識別碼。識別碼應該為完整合規的URI。

EPUB製作者可以使用identifier-type特性來指出dc:identifier元素的值合乎哪一項既有的系統或者識別碼發行機構之規定。

範例 21: 指定識別碼類型
在本範例中，identifier-type特性使用ONIX代碼列表5綱要以指示產品識別碼類型為一個DOI（因為在代碼列表5中的值06供DOI使用）。

<metadata …>
   <dc:identifier
       id="pub-id">
      urn:doi:10.1016/j.iheduc.2008.03.001
   </dc:identifier>
   <meta
       refines="#pub-id"
       property="identifier-type"
       scheme="onix:codelist5">
      06
   </meta>
   …
</metadata>
5.5.3.2 dc:title元素

dc:title元素[dcterms]代表EPUB出版品的一項名稱。

元素名稱：
dc:title

命名空間：
http://purl.org/dc/elements/1.1/

用途：
metadata需要的子元素。可以重複。

屬性：
dir [選擇性]

id [選擇性]

xml:lang [選擇性]

內容模型：
文字

文件順序中的第一個dc:title元素為該EPUB出版品的主要標題（也就是閱讀系統主要會呈現給使用者的那一個）。

範例 22: 一個基本的title元素
<metadata …>
   <dc:title>
      Norwegian Wood
   </dc:title>
   …
</metadata>
EPUB製作者應該只使用一個dc:title元素以確保閱讀系統在處理書名時恆定。

註釋
雖然可以包含多於一個的dc:title元素供多部書名使用但閱讀系統對於額外dc:title元素的支援並不穩定。閱讀系統可能會忽略額外的斷片，或者以非預期的方式將其組合起來。

例如，以下範本呈現一個基本的多部書名作品：

<metadata …>
   <dc:title>
      THE LORD OF THE RINGS
   </dc:title>
   <dc:title>
      Part One: The Fellowship of the Ring
   </dc:title>
   …
</metadata>
相同的書名可以使用單一dc:title元素表達如下：

<metadata …>
   <dc:title>
       THE LORD OF THE RINGS, Part One:
       The Fellowship of the Ring
   </dc:title>
   …
</metadata>
本規格之前的版本推薦使用title-type及display-seq特性來對多部書名作品進行識別以及格式化斷片（請參照Great Cookbooks範本）。依然可以添加這些語義，但是在支援程度上不佳。

5.5.3.3 dc:language元素

dc:language元素[dcterms]指定了EPUB出版品內容使用的語言。

元素名稱：
dc:language

命名空間：
http://purl.org/dc/elements/1.1/

用途：
metadata需要的子元素。可以重複。

屬性：
id [選擇性]

內容模型：
文字

每一個dc:language元素的值必須為形式完整的語言標籤[bcp47]。

範例 23: 指定EPUB出版品語言為美式英文。
<metadata …>
   …
   <dc:language>
      en-US
   </dc:language>
   …
</metadata>
儘管EPUB製作者可以為多語系出版品指定額外的dc:language元素，但閱讀系統只會將文件順序中第一個dc:language元素作為EPUB出版品的主要語言。

註釋
出版品資源並不從dc:language元素中繼承該語言。EPUB製作者必須以該格式固有的方式指定資源所使用的語言。

5.5.4 都柏林核心集的選配元素

5.5.4.1 一般定義

除了dc:identifier、dc:language以及dc:title以外的所有[dcterms]元素皆為選擇性。這些元素合乎以下一般性定義：

元素名稱：
dc:contributor | dc:coverage | dc:creator | dc:date | dc:description | dc:format | dc:publisher | dc:relation | dc:rights | dc:source | dc:subject | dc:type

命名空間：
http://purl.org/dc/elements/1.1/

用途：
metadata的選擇性子元素。可以重複。

屬性：
dir [選擇性] – 僅允予用於 dc:contributor、dc:coverage、dc:creator、dc:description, dc:publisher、dc:relation、dc:rights以及dc:subject。

id [選擇性] – 允予用於任何元素。

xml:lang [選擇性] – 僅允予用於dc:contributor、dc:coverage、dc:creator、dc:description、dc:publisher、dc:relation、dc:rights以及dc:subject。

內容模型：
文字

本規格不對除了以下章節特別標注的[dcterms]元素之定義進行變更。

5.5.4.2 dc:contributor元素t

dc:contributor元素[dcterms]用於代表人名、組織名等。其在內容創作中擔任次級角色。

dc:contributor元素規定需在任何方面與dc:creator元素一致。

5.5.4.3 dc:creator元素

dc:creator元素[dcterms]用於代表人名、組織名等，其對內容創作負責。EPUB製作者可以讓該元素與一個associate a role特性相關聯，以指出該創作者所扮演的角色。

範例 24: 將creator指定為作者
在本範例中，使用了MARC關係人綱要來指定角色（值aut在MARC中對應到作者）。

<metadata …>
   …
   <dc:creator
       id="creator">
      Haruki Murakami
   </dc:creator>
   <meta
       refines="#creator"
       property="role"
       scheme="marc:relators"
       id="role">
      aut
   </meta>
   …
</metadata>
dc:creator元素應該包含EPUB製作者預期閱讀系統顯示給使用者的創作者名稱。

EPUB製作者可以使用file-as特性來與該創作者名稱的正規化形式建立相關，以及alternate-script特性以另一種語言或文字來表達該創作者的名稱。

範例 25: 表述creator的排序以及處理資訊
<metadata …>
   …
   <dc:creator
       id="creator">
      Haruki Murakami
   </dc:creator>
   <meta
       refines="#creator"
       property="alternate-script"
       xml:lang="ja">
      村上 春樹
   </meta>
   <meta
       refines="#creator"
       property="file-as">
      Murakami, Haruki
   </meta>
   …
</metadata>
如果一本EPUB出版品有多於一位的創作者，EPUB製作者應該分別以不同的dc:creator元素進行指定。

在metadata區塊中dc:creator元素的文件順序決定了顯示優先度，第一個遇到的dc:creator元素可視為主要創作者。

範例 26: 表述主要創作者
在本範例中，Lewis Carroll因為列於第一位，所以為主要創作者。

<metadata …>
   …
   <dc:creator
       id="creator01">
      Lewis Carroll
   </dc:creator>
   <dc:creator
       id="creator02">
      John Tenniel
   </dc:creator>
   …
</metadata>
EPUB製作者應該使用dc:contributor元素來代表次要創作者。

5.5.4.4 dc:date元素

dc:date元素[dcterms]定義了EPUB出版品的出版日期。出版日期與最後修正日期（last modified date）不同（其為EPUB製作者最後修改EPUB出版品的時間）。

推薦使用符合[iso8601]的日期字串，特別為W3C日期與時間格式[datetime]中所表述的子集，這樣的字串人類與機器兩方都可以閱讀。

範例 27: 表述出版日期
<metadata …>
   …
   <dc:date>
      2000-01-01T00:00:00Z
   </dc:date>
   …
</metadata>
EPUB製作者在表述額外的日期時，應該使用[dcterms]或其他用語集中特化的日期特性。

EPUB出版品不得包含多於一個的dc:date元素。

5.5.4.5 dc:subject元素

dc:subject元素[dcterms]用於指定EPUB出版品的主題。EPUB製作者應該將該元素的值設定為人類可閱讀的標題或者標籤，但在主題語沒有提供獨立說明標籤時，可以使用代碼值。

EPUB製作者可以使用authority特性來指定他們填入元素值所來自的系統或者綱要。

當指定綱要時，EPUB製作者必須要使用term特性來連結一個主題代碼。

範例 28: 指定一個BISAC代碼與標題
<metadata …>
   <dc:subject id="subject01">
      FICTION / Occult &amp; Supernatural
   </dc:subject>
   <meta
       refines="#subject01"
       property="authority">
      BISAC
   </meta>
   <meta
       refines="#subject01"
       property="term">
      FIC024000
   </meta>
</metadata
範例 29: 指定一個供綱要使用的URL
<metadata …>
   <dc:subject id="sbj01">
      Number Theory
   </dc:subject>
   <meta
       refines="#sbj01"
       property="authority">
      http://www.ams.org/msc/msc2010.html
   </meta>
   <meta
      refines="#sbj01"
      property="term">
     11
  </meta>
</metadata>
term特性在不指定綱要時，不得與dc:subject元素相關聯。

dc:subject元素與term特性的值當在指定的綱要有要求時，得區分大小寫。

5.5.4.6 dc:type元素

dc:type元素[dcterms]用於指出EPUB出版品為哪一種特化的類型（例如以EPUB格式提供的註解或者字典）。

EPUB製作者可以使用任何文字字串作為值。

註釋
之前IDPF的EPUB 3工作小組維護了一份供本元素使用參考性特化EPUB出版品類型註冊列表。本工作小組不再維護該列表，也不會再參與開發新的特化出版品類型。

5.5.5 meta元素

meta元素提供了通用的方式來包含包裝後設資料。

元素名稱：
meta

用途：
metadata元素的子元素。可以重複。

屬性：
dir [選擇性]

id [選擇性]

property [必要]

refines [選擇性]

scheme [選擇性]

xml:lang [選擇性]

內容模型：
文字

每個meta元素定義了後設資料表述。property屬性採用一個property資料類型值來定義表述所做出的宣告，以及該元素的文字內容作為說明（請參見D.1 用語關聯機制以獲得更多資訊）。

本規格定義了兩種類型的後設資料表述EPUB製作者可以利用meta元素定義：

主要表述為meta元素中定義的一種表述，其建立了EPUB出版品的某些面向。忽略refines屬性的meta元素即可被定義為主要表述。
次要表述為meta元素定義的一種表述，與另一個表述或者資源透過refines屬性相關聯以增強其意義。例如，次要表述可用來描述一段媒體片段，描述其長度，或者透過定義人物的角色來進一步描述其創作者或者貢獻者。
EPUB創作者可以使用次要表述來精製化其他次要表述的意義，於是建立了資訊鏈。

註釋
所有[dcterms]元素都為主要表述，但允許使用meta元素次要表述來進行精製化。
Meta特性用語集為使property屬性時的預設用語集。

EPUB製作者可以從另外一個用語集添加術語，如D.1 用語關聯機制所定義。

範例 30: 使用保留字首的特性
請參見D.1.5 保留的字首以獲得保留字首的完整列表。

<metadata …>
   …
   <meta
       property="dcterms:modified">
      2016-02-29T12:34:56Z
   </meta>
   <meta
       property="rendition:layout">
      pre-paginated
   </meta>
   <meta
       property="media:active-class">
      my-active-item
   </meta>
   …
</metadata>
scheme屬性用於辨識EPUB製作者取得該元素之值的系統或者綱要。屬性的值必須為property資料類型值能解析到定義該綱要的資源上。scheme屬性並不擁有預設用語集（也就是所有的值都需要字首）。

範例 31: 使用來自綱要的值
在本範例中，scheme屬性指出該標記的值來自[onix]代碼列表5（也就是該值15代表13位的ISBN）。

<metadata …>
   …
   <meta
       refines="#isbn-id"
       property="identifier-type"
       scheme="onix:codelist5">
      15
   </meta>
   …
</metadata>
5.5.6 最後修正日期

metadata區塊必須包含唯一一個dcterms:modified特性[dcterms]包含了最後修正日期。本特性的值必須為一個[xmlschema-2]日期時間合乎以下形式：CCYY-MM-DDThh:mm:ssZ。

EPUB製作者必須以世界協調時間（UTC）表達最後修正日期，以及必須以「Z」（祖魯）時區代碼作結。

範例 32: 表達最後修正日期
<metadata …>
   …
   <meta
       property="dcterms:modified">
      2016-01-01T00:00:01Z
   </meta>
   …
</metadata>
EPUB製作者無論對EPUB出版品做出任何更動，都需要更新最後修正日期。

EPUB製作者可以在包裝文件後設資料中指定額外的modified特性，但他們必須有不同的目的（例如透過refines屬性參照一個元素或者資源）。

註釋
對於最後修正日期的規定主要是為了確保能和前版本EPUB 3相容，其定義了供EPUB出版品使用的發布識別碼[epubpackages-32]。

5.5.7 link元素

link元素讓EPUB出版品能與資源相關聯，像是後設資料紀錄。

元素名稱：
link

用途：
metadata元素的子元素。可以重複。

屬性：
href [必要]

hreflang [選擇性]

id [選擇性]

media-type [某些狀況為必要]

properties [選擇性]

refines [選擇性]

rel [必要]

內容模型：
空白

metadata元素可以包含零或多個link元素，每一項都需要識別出版品資源的位址或者透過需要的href屬性識別連結的資源的位址。

透過link元素參照的資源，在其符合以下條件時為出版品資源：

在書脊中參照；或者

包含或嵌入於EPUB內容文件中（像是一份後設資料以RDFa[rdfa-core]或JSON-LD [json-ld11]格式序列化後以[html]script元素嵌入）。

其他所有的狀況（像是連結到獨立存在的[onix]或[xmp]紀錄），被參照的資源則非出版品資源（像是不符合核心媒體類型規定），從而EPUB製作者不得將其列於宣告。

範例 33: 參照嵌入在一份XHTML內容文件中的紀錄
在本範例中，後設資料紀錄以一個script元素嵌入。請注意嵌入紀錄的媒體類型（即為application/ld+json）是透過script元素的type屬性取得；並未在link元素中所指定。

包裝文件：

<package …>
   <metadata …>
      … 
      <link rel="record"
          href="front.xhtml#meta-json"
          media-type="application/xhtml+xml"
          hreflang="en"/>
      …
   </metadata>
   …
</package>

XHTML：

<html …>
   <head>
      …
      <script id="meta-json" type="application/ld+json">
          "@context" : "http://schema.org",
          "name" : "…",
         …
      </script>
      …
   </head>
   <body>
      …
   </body>
</html>
EPUB製作者可以指向位於EPUB容器內部或之外的連結的資源，但應該考量閱讀系統不強制要求得取得外於EPUB容器的資源。

當連結的資源位於EPUB容器外時，media-type 屬性為選擇性，因為相同的URL[url]可以提供多於一個的媒體類型。EPUB製作者必須為位於EPUB容器內的所有連結的資源指定該屬性。

選擇性的hreflang屬性用於識別連結的資源使用的語言。該值必須為形式完整的語言標籤[bcp47]。

需要的rel屬性使用空白所分隔的特性值列表，建構連結的資源與EPUB出版品之間的關係。

範例 34: 連結到一份MARC XML紀錄
<metadata …>
   …
   <link
       rel="record"
       href="meta/9780000000001.xml" 
       media-type="application/marc"/>
   …
</metadata>
media-type屬性的值不會一直都能用於辨識連結的資源之類型（像是許多基於XML的紀錄格式使用的媒體類型都為「application/xml」）。為協助閱讀系統識別這些通用資源，EPUB製作者可以在properties屬性中指定語義識別碼。

範例 35: 透過property指定紀錄類型
在本範例中，properties屬性用於辨識該連結指向一份XMP紀錄。

<metadata …>
   …
   <link rel="record"
       href="http://example.org/meta/12389347?format=xmp"
       media-type="application/xml"
       properties="xmp"/>
   …
</metadata>
後設資料連結用語為rel和properties屬性的預設用語集。

EPUB製作者可以從其他的用語集添加關係以及特性，如D.1 用語關聯機制所定義。

範例 36: 宣告一個新的link關係
在本範例中，link元素使用FOAF用語集和作者的首頁相關聯。請注意foaf並非預定義的字首，而必須在prefix屬性中宣告。

<package
    …
    prefix="foaf: http://xmlns.com/foaf/spec/">
   <metadata …>
      … 
      <link
          refines="#creator01"
          rel="foaf:homepage"
          href="http://example.org/book-info/12389347" />
      …
   </metadata> 
   …
</package>
EPUB製作者可以提供一或多個連結的後設資料紀錄以提供更多的資訊給閱讀系統使用，但閱讀系統可能會忽略這些紀錄。

當閱讀系統處理連結的紀錄[epub-rs-33]時，link元素的文件順序在產生衝突時用於決定何者有最高的優先順位（也就是文件順序的第一個有最高的優先順位）。

範例 37: 指定後設資料順位
在本範例中，第一個遠端紀錄有著最高的順位，本地紀錄為次高，在metadata元素中的後設資料為最低。

<metadata …>
   <link rel="record"
       href="http://example.org/onix/12389347"
       media-type="application/xml"
       properties="onix" />
    
   <link rel="record"
       href="meta/meta.jsonld"
       media-type="application/ld+json" />
    
    <dc:title>The Sound and The Fury</dc:title>
    <dc:identifier>urn:isbn:9780101010101</dc:identifier>
    <dc:language>en-us</dc:language>
    …
</metadata>
註釋
由於EPUB製作者可以連結到EPUB出版品的後設資料紀錄，其格式與序列化多種多樣，造成在彼此之間對應後設資料相當複雜，本規格不要求閱讀系統必須處理連結記錄。

在完整記錄之外，EPUB製作者也可以使用link元素來指定可以替代格式取得的獨立後設資料特性。

範例 38: 連結到一份描述
在本範例中，EPUB出版品的描述包含在一份HTML文件中。

<metadata …>
   …
   <link
       rel="dcterms:description"
       href="description.html"
       media-type="text/html"/>
   …
</metadata>
5.6 Manifest區塊

5.6.1 manifest元素

manifest元素提供了用於處理內容的出版品資源之窮舉列表。

元素名稱：
manifest

用途：
package需要的第二個子元素，在metadata之後。

屬性：
id [選擇性]

內容模型：
item [1或多個]

EPUB製作者必須在manifest中列出所有出版品資源，無論是容器資源或者遠端資源。此外，manifest必須僅用於表列出版品資源。

請注意manifest不可以自我參照：EPUB製作者不得指定一個item元素參照到包裝文件自身。

註釋
無法提供完整資源宣告會導致處理上的問題。閱讀系統可能無法解壓縮這樣的資源或者可能因為安全原因而避開對資源的存取。

5.6.2 item元素

item元素代表一份出版品資源。

元素名稱：
item

用途：
manifest的子元素。可以重複。

屬性：
fallback [某些狀況為必要]

href [必要]

id [必要]

media-overlay [選擇性]

media-type [必要]

properties [選擇性]

內容模型：
空白

每一個item元素透過其href 屬性中的URL[url]來識別出版品資源。該值必須為一個絕對-（absolute-）或者 路徑-相對-無-綱要-位址（path-relative-scheme-less-URL）字串[url]。EPUB製作者必須確保每一個URL在manifest範圍內經過解析後皆為唯一。

透過item元素識別的出版品資源必須合乎其media-type 屬性所提供的MIME媒體類型[rfc2046]所推斷應適用的規格。對核心媒體類型資源而言，EPUB製作者必須使用列於3.2 核心媒體類型中的媒體類型。

fallback屬性所參照的出版品資源為回退時的指定項目。fallback屬性的IDREF[xml]值必須解析到manifest中的另一個item。

一個item的回退可以指定fallback到另外一個item，以此類推，創立了fallback選項鏈。請參見3.5.1 宣告回退以獲得使用回退鏈相關的額外規定。

media-overlay屬性使用一個IDREF[xml]來識別媒體層疊文件作為解釋本item的資源。請參見9.3.5 媒體層疊包裝以獲得更多資訊。

註釋
manifest中的item元素順序不具意義。spine 元素提供了內容文件的顯示順序。

5.6.2.1 資源特性

properties屬性提供閱讀系統關於該資源內容的資訊。這項資訊可用於發現關鍵資源，像是封面圖片以及EPUB導覽文件.。也讓閱讀系統能夠針對其做最佳化處理，例如，是否該資源包含嵌入腳本、MathML或者SVG。

後設資料連結用語為properties屬性的 預設用語集。

EPUB製作者當在item元素所參照的資源符合相關定義時，必須設定以下特性：

mathml
remote-resources
scripted
svg
switch
範例 39: 識別一份有腳本的內容文件其中有嵌入的MathML
<item
    properties="scripted mathml"
    id="c2"
    href="c2.xhtml"
    media-type="application/xhtml+xml" />
這些特性不可以遞迴套用到包含該內容的資源上（像是透過[html]iframe元素）。例如當一份沒有腳本的XHTML內容文件嵌入一份有腳本的內容文件，只有被嵌入的文件之宣告item properties屬性有scripted值。

EPUB製作者必須使用nav特性宣告唯一item為EPUB導覽文件。

範例 40: 指定EPUB導覽文件
<item
    properties="nav"
    id="c1"
    href="c1.xhtml"
    media-type="application/xhtml+xml" />
如果一本EPUB出版品包含封面圖片，推薦使用cover-image特性來設定，但本特性為選擇性。

範例 41: 指定封面圖片
<item
    properties="cover-image"
    id="ci"
    href="cover.svg"
    media-type="image/svg+xml" />
EPUB製作者可以從其他用語集新增術語，如D.1 用語關聯機制所定義。

5.6.2.2 範例

範例 42: 一份僅有核心媒體類型資源的宣告
<package …>
   …
   <manifest>
      <item
          id="nav" 
          href="nav.xhtml" 
          properties="nav"
          media-type="application/xhtml+xml"/>
      <item
          id="intro" 
          href="intro.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c1" 
          href="chap1.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c1-answerkey" 
          href="chap1-answerkey.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c2" 
          href="chap2.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c2-answerkey" 
          href="chap2-answerkey.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c3" 
          href="chap3.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="c3-answerkey" 
          href="chap3-answerkey.xhtml" 
          media-type="application/xhtml+xml"/>    
      <item
          id="notes" 
          href="notes.xhtml" 
          media-type="application/xhtml+xml"/>
      <item
          id="cover" 
          href="./images/cover.svg" 
          properties="cover-image"
          media-type="image/svg+xml"/>
      <item
          id="f1" 
          href="./images/fig1.jpg" 
          media-type="image/jpeg"/>
      <item
          id="f2" 
          href="./images/fig2.jpg" 
          media-type="image/jpeg"/>
      <item
          id="css" 
          href="./style/book.css" 
          media-type="text/css"/>   
   </manifest>
   …
</package>
範例 43: 書脊中有回退的外圍內容文件
以下範例呈現宣告回退鏈，因為外圍內容文件（JPEG）可以回退到一份SVG內容文件，所以可以被列於書脊中。

<package …>
   …
   <manifest>
      …
      <item
          id="page-001"
          href="images/page-001.jpg"
          media-type="image/jpeg"
          fallback="page-001-svg"/>

      <item
          id="page-001-svg"
          href="images/page-001.svg"
          media-type="image/svg+xml"/>
      … 
      …
   </manifest>
   <spine>
      …
      <itemref idref="page-001"/>
      …
   </spine>
</package>
範例 44: 以「檢視連結」方式嵌入核心媒體類型資源作為頂層內容文件
以下範例呈現一份EPUB內容文件嵌入了一張JPEG（透過img標籤）並且提供一個超連結以讓其能以獨立頁面開啟（為能更簡單地縮放）。雖然使用img標籤嵌入圖片不需要列於書脊或者提供回退，但添加超連結會讓文件將其作為頂層內容文件開啟。由於用於書脊會讓其變成外圍內容文件，EPUB製作者必須包含一個回退指向EPUB內容文件。

XHTML:
<html …>
   …
   <body>
      …
      <img
          src="images/infographic.jpg"
          alt="…"/>
      <a
          href="images/infographic.jpg">
         Expand Image
      </a>
      …
   </body>
</html>

包裝文件：
<package …>
   …
   <manifest>
      …
      <item
          id="img01"
          href="images/infographic.jpg"
          media-type="image/jpeg"
          fallback="infographic-svg"/>

      <item
          id="infographic-svg"
          href="images/infographic.svg"
          media-type="image/svg+xml"/>
      …
   </manifest>
   <spine>
      …
      <itemref
          idref="img01"
          properties="layout-pre-paginated"
          linear="no"/>
      …
   </spine>
</package>
範例 45: 「檢視連結」外圍資源作為頂層內容文件
以下範例呈現一個連結指向CSV原始資料檔案。由於該資料在閱讀系統內會被以頂層內容文件開啟，EPUB製作者必須將其列於書脊。由於用於書脊會使其成為外圍內容文件，EPUB製作者必須也提供一份回退指向EPUB內容文件。因為無法保證使用者以其原始形式存取資料，也一併提供如何將檔案從EPUB容器中取出的教學。

XHTML：
<html …>
   …
   <body>
      …
      <p>
         <a href="../data/raw.csv">
            [Open the raw CSV data for this project.]
         </a>
      </p>
      <p class="small">To extract the data file
         from this publication, unzip the EPUB file.
         The data is located in the
      	<code>/EPUB/data/raw.csv</code> file.
      </p>
      …
   </body>
</html>

包裝文件：
<package …>
   …
   <manifest>
      …
      <item
          id="data01"
          href="data/raw.csv"
          media-type="text/csv"
          fallback="data-html"/>

      <item
          id="data-html"
          href="xhtml/data-table.html"
          media-type="application/xhtml+xml"/>
      …
   </manifest>
   <spine>
      …
      <itemref
          idref="data01"
          linear="no"/>
      …
   </spine>
</package>
範例 46: 遠端資源作為出版品資源
以下範例呈現對一個遠端聲音檔案的參照。因為該音檔在EPUB內容文件中以audio元素嵌入，該檔案會被視為出版品資源。EPUB製作者 因而必須將聲音檔案列於宣告中，並且指示其嵌入的EPUB內容文件包含遠端資源。

XHTML：
<html …>
   …
   <body>
      …
      <audio
          src="http://www.example.com/book/audio/ch01.mp4"
          controls="controls"/>
      …
   </body>
</html>

包裝文件：
<package …>
   …
   <manifest>
      …
      <item
          id="audio01"
          href="http://www.example.com/book/audio/ch01.mp4"
          media-type="audio/mp4"/>
   
      <item
          id="c01"
          href="XHTML/chapter001.xhtml"
          media-type="application/xhtml+xml"
          properties="remote-resources"/>
      …
   </manifest>
   …
</package>
範例 47: 外部資源並非出版品資源
以下範例呈現一個超連結指向託管於網頁上的聲音檔案。閱讀系統會在新的瀏覽器視窗中開啟這樣的外部內容；聲音檔案不會在出版品中處理。在這案例中，EPUB製作者不用在宣告中列出該檔案因為其並非出版品資源。

XHTML：
<html …>
   …
   <body>
      …
      <a
          href="http://www.example.com/book/audio/ch01.mp4">
         Listen to audio
      </a>
      …
   </body>
</html>

宣告：
不用登錄
5.6.3 bindings元素（不再推薦）

bindings元素定義了一組客製化處理程序供本規格不支援的媒體類型使用。

不再推薦使用此元素。

請參照[epubpublications-301]中的bindings元素定義以獲得更多資訊。

5.7 Spine區塊

5.7.1 spine元素

spine元素定義了參照宣告item的排序列表，以呈現預設的閱讀順序。

元素名稱：
spine

用途：
package需要的第三個子元素，在manifest之後。

屬性：
id [選擇性]

page-progression-direction [選擇性]

toc [選擇性] （遺存）

內容模型：
itemref [1或多個]

spine必須指定至少一個EPUB內容文件或者外圍內容文件。

EPUB製作者必須在spine中條列所有EPUB與外圍內容文件，包括在spine中被連結到的出版品資源，其中超連結包含任何要求使用者由目前資源離開的連結機制。一般的超連結機制包含[html]a以及area元素的href屬性以及腳本的連結（也就是透過DOM事件及/或表單元素）。條列超連結的資源要求適用於遞迴（也就是EPUB製作者必須列出所有從超連結的文件所連到的所有EPUB與外圍內容文件，以此類推）。

EPUB製作者也必須在spinee中列出所有EPUB與外圍內容文件，其被EPUB導覽文件透過超連結所連結，無論EPUB製作者是否在spine中包含EPUB導覽文件。

註釋
超連結連到外於EPUB容器的資源並非出版品資源，也並非需要被包含在書脊中的對象（例如網頁或者託管於網頁上的資源）。

用於處理書脊項目的出版品資源（也就是透過[html]嵌入內容所參照的對象）同樣也不需要包含在書脊內。

page-progression-direction屬性設定了全域的內容行頁方向。可以使用的值為ltr（由左向右）、rtl（由右而左）以及default。當EPUB製作者指定default值時，所表達的是沒有特別偏好，而閱讀系統可以選擇處理的方向。

雖然page-progression-direction屬性設置全域行頁方向，個別EPUB內容文件以及一部分的EPUB內容文件可以覆蓋該設定（例如透過writing-mode CSS特性）。閱讀系統也可以提供機制覆蓋預設方向（例如透過按鍵或者設定選項來允許使用替代的樣式表）。

遺存的toc屬性採用IDREF [xml]來指定宣告項目中的NCX。

5.7.2 itemref元素

itemref元素按照預設閱讀順序指定EPUB內容文件或者外圍內容文件。

元素名稱：
itemref

用途：
spine的子元素。可以重複。

屬性：
id [選擇性]

idref [必要]

linear [選擇性]

properties [選擇性]

內容模型：
空白

每一個itemref元必須透過idref屬性以IDREF[xml]方式參照宣告中item的ID[xml]。item元素的ID不得被參照多過一次。

每一個被參照的宣告item必須為其一 a)一份EPUB內容文件 或 b)一份外圍內容文件並且在其宣告回退鏈中包含一份EPUB內容文件。

註釋
雖然 EPUB出版品規定需要一份EPUB導覽文件，但並不強制一定要包含在書脊中。

linear屬性指示被參照的item所包含的內容是否有助於主要閱讀順序，以及閱讀系統必須依序閱讀（「yes」），或者為輔助內容用於加強或增進主要內容，閱讀系統可以不按順序呈現（「no」）。輔助內容的範例包括：註解、說明以及答案。

linear屬性讓閱讀系統得以辨別內容是否為使用者須應該在預設閱讀順序中存取的一部分，或者是閱讀系統可以，例如透過跳出視窗，或者從聲音處理中忽略的輔助用內容。

然而，將內容指定為非linear並不要求閱讀系統以特別的方式呈現之；只是提供一個提示而已。例如，閱讀系統可以呈現spine中的非linear內容，或者可以跳過它，直到使用者到達書脊之最末才顯示。

註釋
EPUB製作者應該在書脊的結尾列出非linear的內容，除非該內容在兩份線性書脊項目中出現才具意義。

線性itemref元素為其linear屬性值明確設定為「yes」，或者忽略其屬性─閱讀系統會假定沒有該屬性的itemref元素之值為「yes」。spine必須包含至少一個線性itemref元素。

EPUB製作者必須提供存取所有非線性內容的手段（例如在內容中使用超連結，或者透過EPUB導覽文件）。

書脊特性用語為該properties屬性的預設用語集。

EPUB製作者可以從其他用語集新增術語，如D.1 用語關聯機制所定義。

範例 48: 一份基本的書脊
在本範例中，書脊中的項目呼應到上面的宣告範本。

<spine
    page-progression-direction="ltr">
   <itemref
       idref="intro"/>
   <itemref
       idref="c1"/>
   <itemref
       idref="c1-answerkey"
       linear="no"/>
   <itemref
       idref="c2"/>
   <itemref
       idref="c2-answerkey"
       linear="no"/>
   <itemref
       idref="c3"/>
   <itemref
       idref="c3-answerkey"
       linear="no"/>
   <itemref
       idref="notes"
       linear="no"/>
</spine>
5.8 集合

5.8.1 collection元素

collection元素定義了相關的資源群組。

元素名稱：
collection

用途：
package選擇性的第六個元素。可以重複。

屬性：
dir [選擇性]

id [選擇性]

role [必要]

xml:lang [選擇性]

內容模型：
按此順序：metadata [0或1]，（collection[1或多個]或（collection[0或多個]、link[1或多個]））

collection元素讓EPUB製作者可以組合資源作為邏輯上的群組以供各種潛在的用途：用於重組成一個有意義的內容單位跨多個EPUB內容文件使用（例如，一份切分跨多個文件的索引），識別供特別目的使用的資源（例如，預覽用內容），或者將內容集合起來表現關於該EPUB出版品的額外資訊。

EPUB製作者必須使用role屬性識別每一個collection元素的角色，其值class="rfc2119">必須為一或多個NMTOKENs[xmlschema-2]及/或絕對-位址-具-斷片（absolute-url-with-fragment）字串[url]。

製作特化的集合之規定，由相關的規格定義之。

註釋
之前IDPF的EPUB 3工作小組維護了一份註冊列表同時供role延伸以及客製化延伸role使用。本工作小組不再維護這些列表。

範例 49: 一份跨文件的索引
<collection role="index">
   <link href="subjectIndex01.xhtml"/>
   <link href="subjectIndex02.xhtml"/>
   <link href="subjectIndex03.xhtml"/>
</collection>
5.8.2 定義集合類型（不再推薦）

不再推薦創建新的collection元素角色。

請參見[epubpackages-32]中collection元素定義以獲得更多關於創建特化集合的資訊，包含規定與用途上的限制。

5.9 遺存（Legacy）功能

5.9.1 介紹

包裝文件從EPUB 3繼承的遺存功能僅讓EPUB製作者在製作內容時，能在某些程度上，於僅支援EPUB 2出版品的閱讀系統上運作。

添加這些機能主要是為了解決EPUB 3閱讀系統開發的重疊期間，當時有很高的可能性，使用者可能會以EPUB 2閱讀系統開啟EPUB 3出版品。

由於現在僅支援EPUB 2出版品的閱讀系統變得少見，EPUB製作者在花力氣添加這些遺存功能時，應該考量其出版品可能會以這些老設備開啟的可能性。

5.9.2 支援

EPUB製作者可以為了與EPUB 2閱讀系統相容的目的，包含本章節中定義的遺存功能。

EPUB 3閱讀系統在呈現出版品給讀者時，不會使用這些功能。

註釋
EPUB符合性檢驗工具在發現EPUB出版品中存在遺存功能時，不應警告EPUB製作者，因為他們包含這些功能對向後相容性而言合乎規定。EPUB符合性檢查工具必須在遺存功能不合乎其定義，或者違反用途規定時警告EPUB製作者。

5.9.3 meta元素

meta元素[opf-201]提供了為EPUB 2 閱讀系統提供包含通用後設資料的手段。

請參見[opf-201]中對meta元素的定義以獲得更多資訊。

註釋
EPUB 3 meta元素使用不同的屬性以及必須要有文字內容，才能供EPUB 3閱讀系統提供後設資料的能力。

[opf-201]meta元素也能讓EPUB製作者為EPUB 2閱讀系統指定封面圖片。在EPUB 3中，封面圖片必須在宣告 item中對圖片使用cover-image特性來指定。

5.9.4 guide元素

guide元素[opf-201]提供機器可讀取的導覽為EPUB 2閱讀系統提供關鍵結構。

請參見[opf-201]中對guide元素的定義以獲得更多資訊。

註釋
EPUB導覽文件中的 landmarks nav為EPUB 3閱讀系統提供了本項功能。

5.9.5 NCX

[opf-201]的NCX為EPUB 2閱讀系統提供了目次。

請參見[opf-201]中對NCX的定義以獲得更多資訊。

註釋
EPUB導覽文件在EPUB 3中取代了NCX。

6. EPUB內容文件

6.1 XHTML 內容文件

6.1.1 介紹

本節不具規範性。

本章節定義了[html]的子集以創建XHTML內容文件。作為XML文件的實例，其需要符合該子集，並且為核心媒體類型資源，同時在本規格中參照為一份XHTML內容文件。

6.1.2 XHTML 規定

一份XHTML內容文件：

必須為合乎XML語法的[html]文件。

必須合乎由[html]定義的所有文件架構符合性範疇，除非在6.1.4 HTML歧異與限制中有明確取代。

可以包含定義在6.1.3 HTML延伸中定義的[html]文法延伸，以及必須合乎該章節定義的所有內容符合性限制。

除非另外有指定，不然XHTML內容文件從[html]規格繼承所有語義、結構、處理行為的定義。

註釋
推薦EPUB出版品遵循[epub-a11y-11]中的無障礙輔助規定，應用到XHTML內容文件上。請見可及性。

6.1.3 HTML 延伸

本章節定義EPUB 3 XHTML內容文件，對其仰賴[html]文件模型的延伸。

註釋
儘管[html]允許使用者代理支援中立的延伸，但除了列在本章節的延伸外，都不是EPUB 3所支援的功能。

6.1.3.1 結構語義

EPUB製作者可以在XHTML內容文件中使用epub:type屬性以表述結構語義。

該屬性不得用於head元素或者後設資料內容中[html]。

6.1.3.2 RDFa

[html-rdfa]規格定義了可以讓a data-link-type="dfn" href="#dfn-epub-creator" class="internalDFN" id="ref-for-dfn-epub-creator-69">EPUB製作者用於XHTML內容文件的一組屬性，以對內容提供更豐富的語義。使用這些屬性時，必須合乎定義在[html-rdfa]中的規定。

[html-rdfa]規格定義了當作者使用RDFa屬性時，[html]內容模型的變更。這項變更的內容模型在XHTML內容文件中合乎規定。

註釋
提供RDFa的列表並不代表工作小組的偏好，僅表示這些屬性可作為HTML文法的延伸。EPUB製作者也可以在XHTML內容文件中指定microdata屬性[html]與連結資料[json-ld11]，兩者都受到原生支援。

6.1.3.3 內容切換（不再推薦）

switch元素提供了簡單的機制，讓EPUB製作者可以為使用者量身定制呈現的內容，這種方式不需依存EPUB閱讀系統對腳本的支援能力。

不再推薦使用該元素。

請參見[epubcontentdocs-301]對switch元素的定義以獲得更多資訊。

6.1.3.4 epub:trigger元素（不再推薦）

trigger元素用於製作標記定義的使用者介面，能控制多媒體物件，像是聲音以及影片播放，同時支援需腳本與不需腳本的脈絡。

不再推薦使用該元素。

請參見[epubcontentdocs-301]對epub:trigger元素的定義以獲得更多資訊。

6.1.3.5 客製化屬性

XHTML內容文件可以包含客製化屬性，客製化屬性就是使用字首[xml-names]的屬性，其命名空間URL並未包括在以下這些網域[url]字串中：

w3.org
idpf.org
當使用客製化屬性時，無論閱讀系統是否會對其處理，內容必須維持無資訊丟失或者明顯劣化的狀況下，供使用者消費。

註釋
客製化屬性通常定義特定閱讀系統的行為，而不預期會被其他閱讀系統所使用。本規格應該額外提供多數獨立閱讀系統可使用的延伸列表。

6.1.4 HTML歧異與限制

本章節定義了EPUB 3XHTML內容文件與所基於的[html]文件模型有什麼不同以及限制。

6.1.4.1 嵌入MathML

XHTML內容文件支援嵌入[mathml3]。當使用MathML標記時，必須合乎MathML規格[mathml3]中表述的規定，並且有以下額外的限制：

顯示用MathML
math元素 必須僅包含顯示用MathML，除了在annotation-xml元素內。

內容MathML
EPUB製作者可以在XHTML內容文件中的MathML標記包含內容MathML，當使用時，必須在semantics元素中包含一個annotation-xml子元素來置放。

當EPUB製作者照以上情形包含內容MathML時，其必須將該annotation-xml元素的encoding屬性設定成功能上同等的值MathML-Content或application/mathml-content+xml，以及name屬性為contentequiv。

該子集簡化了閱讀系統實作的門檻，並且能促進可及性，同時保留[html]使用者代理的相容性。

註釋
宣告item元素中的mathml特性指出該XHTML內容文件包含嵌入式MathML。

6.1.4.2 嵌入SVG

XHTML內容文件支援嵌入SVG文件斷片[svg]，可透過參照（透過參照嵌入，例如，透過一個img或object元素）以及透過包含（以直接在XHTML內容文件中包含一個svg元素嵌入）。

在XHTML內容文件中嵌入SVG，內容合規性規定如 6.2.3 對SVG的限制中對SVG內容文件所定義的一樣。

註釋
宣告item元素中的svg特性指出該XHTML內容文件包含嵌入式SVG。

6.1.4.3 不鼓勵使用的架構

本節不具規範性。

6.1.4.3.1 base元素

[html]base 元素可以用於指定文件的基底URL，供解析URL目的使用。當在EPUB出版品中使用時，對base元素的解析可能會在參照遠端資源時產生非預期的結果。可能會造成閱讀系統錯誤解析超連結的位址（例如將出版品中到其他文件的相對連結，在base元素指定絕對URL時，視為一個對網站的連結）。為了避免明顯的互通性問題，EPUB製作者 不應使用base元素。

6.1.4.3.2 rp元素

[html] rp元素之目的是為了讓較舊，無法識別ruby標記的閱讀系統提供回退（也就是在ruby標記前後加入括號）。由於EPUB 3閱讀系統都對ruby有所認知，所以能提供回退，EPUB製作者不應使用rp元素。

6.1.4.3.3 embed元素

由於[html]embed元素不包含固有的機制，為不支援腳本的閱讀系統供回退內容，所以不鼓勵EPUB製作者在參照包含腳本的資源時使用該元素。[html] object 元素為更好的替代方案，因為其包含了固有的回退能力。

6.2 SVG內容文件

警告事項
閱讀系統可能不支援[svg]的所有功能，或者無法在閱讀系統運行的所有平台都提供支援。當使用這些功能時，EPUB製作者應該考量在互通性與文件保存時限上特有的風險。

6.2.1 介紹

本節不具規範性。

可縮放向量圖形（Scalable Vector Graphics,SVG）規格[svg]定義了供表現文字與圖形最終形式的格式。

雖然EPUB製作者通常會使用XHTML內容文件作為XHTML內容文件 as the 頂層文件類型，但也允許使用SVG內容文件。EPUB製作者通常僅會在某些特殊的狀況下會需要用到SVG，像是最終形式頁面圖片為內容唯一適合的表現形式（像是封面圖片，或者在漫畫書的脈絡中使用）。

本章節定義了[svg]文件的子集。作為XML文件的實例，其需要符合該子集，並且為核心媒體類型資源，同時在本規格中參照為一份SVG內容文件。

註釋
本章節定義了SVG內容文件的符合性規定。請參見6.1.4.2 嵌入SVG以獲得在XHTML內容文件中嵌入SVG時的符合性規定。

6.2.2 SVG 規定

一份SVG內容文件：

必須為獨立且合規的SVG檔案[svg]定且符合6.2.3 對SVG的限制中所表述的所有內容符合性規定。

可以包含epub:type屬性供表述結構性語義使用。當指定時，該屬性必須只能包含在structural、shape或text元素中[svg]。

可以包含其他所有可應用的用語關聯機制。

註釋
推薦 EPUB出版品遵循[epub-a11y-11]中的無障礙輔助規定，應用到SVG內容文件上。請見可及性。

6.2.3 對SVG的限制

本規格對SVG內容文件以及在XHTML內容文件中嵌入SVG規定的限制如下：

對於[svg] foreignObject元素：

兩者中必須包含其一：[html]流式內容或者唯一一個[html]body元素。

註釋
當嵌入SVG時，不准許使用body元素，如[html]中定義的SVG限制。
必須包含一個合規的文件斷片，其合乎定義在6.1.2 XHTML規定中的XHTML內容文件模型。

如果[svg]title元素包含標記文字，該標記必須僅包含在HTML命名空間[infra]中宣告的元素。

註釋
雖然[svg]title元素允許使用標記元素，但對該功能的支援有限。建議EPUB製作者僅使用文字標題以獲得最大互通性。

6.3 常見資源規定

本章節定義可用於XHTML與SVG內容文件之技術的規定。

6.3.1 層疊樣式表（CSS）

6.3.1.1 介紹

本節不具規範性。

CSS為開放網頁平台整合的一部分。讀者、出版社以及文件作者預期CSS「沒問題」，正如他們預期HTML沒問題一般。

過去EPUB定義了CSS的子集，強制要求對特定特性支援，並且對許多其他的特性提供了有字首的版本。儘管CSS工作小組不再推薦使用有字首的特性，本規格還會維護一些有字首的特性以避免影響既存的內容。除了本章節定義的一些小例外外，EPUB跟隨W3C定義的CSS。

註釋
請注意，一些閱讀系統將不再支援所有預期的CSS功能，以下為目前所知較有問題的部分：

閱讀系統作出的分頁可能與樣式表搭配造成不良的結果，因為閱讀系統有時使用分欄來進行分頁。這可能造成顯示區域尺寸的值錯誤。固定（Fixed）與絕對（absolute）定位特別容易出問題。

許多螢幕類型在處理動畫與過場時不佳（例如那些反應速度慢的）。

6.3.1.2 CSS規定

一份CSS樣式表：

可以包含任何CSS特性，但有以下例外：

其不得包含direction特性[css-writing-modes-3]。

其不得包含unicode-bidi特性[css-writing-modes-3]。

可以包含定義在6.3.1.3 有字首的特性中的有字首的特性。

必須以UTF-8或UTF-16[unicode]編碼，推薦編碼為UTF-8。

註釋
本規格限制使用 direction以unicode-bidi特性，因為閱讀系統可能沒實作，或者關閉了CSS處理。EPUB製作者當想要控制這些處理面向時，必須使用以下格式指定的方法：

更改行內基礎行文方向時，使用dir屬性[html]以及direction屬性[svg]。

更改雙向文字時，使用bdo元素配dir屬性[html]以及替代unicode-bidi的presentation屬性[svg]。

6.3.1.3 有字首的特性

之前的EPUB版本包含了有字首的CSS特性，因為當時許多與世界各種語言相關的CSS功能尚未成熟。為確保使用這些字首製作的內容之向後相容性，則必須保留在本規格中。除非有特別指出，不然有字首的特性與值和其沒有字首的對等項目在其對應的CSS規格中之描述表現一致。有字首的特性另記述在E. 有字首的CSS特性。

警告事項
EPUB製作者應該使用沒有字首的特性，以及閱讀系統應該支援最新的CSS規格。本規格保留這些廣受使用有字首的特性自[epubcontentdocs-301]起，但移除了對較少使用的支援。EPUB製作者應該使用CSS原生的處理方式來取代被移除了的特性，如果有的話。

工作小組建議現在還在使用有字首特性的EPUB製作者，在支援允許的狀況下盡快轉為使用無字首的版本，因為工作小組在下次EPUB的大型改版時不會再支援這些特性。

6.3.2 腳本

6.3.2.1 包含腳本

EPUB內容文件可以使用定義在各自依靠的規格（[html]與[svg]）中的機制來包含腳本。當一份EPUB內容文件包含腳本時，本規格將其參照為有腳本的內容文件。該標籤也適用於包含[html]form元素的XHTML內容文件。

宣告item元素中的scripted特性用於指示該EPUB內容文件為有腳本的內容文件。

當一個[html]script元素包含一個資料區塊[html]時，其不被視為有腳本的內容。

註釋
[svg]並不將資料區塊定義為出版品的一部分，但是當未來更新加入這概念時，也適用相同的排除原則。

EPUB製作者應該注意，閱讀系統規定要將每一本EPUB出版品處理得像是獨特來源[html]。實際上意味著腳本不可能在EPUB出版品間分享資料。

腳本用於何種脈絡也決定了閱讀系統對其施予的權利與限制（請參照腳本[epub-rs-33]以獲得更多資訊）。

註釋
閱讀系統可以以關閉其他EPUB能力及/或提供不同處理以及使用者體驗的方式，來處理腳本化內容文件（例如關閉分頁）。

6.3.2.2 腳本脈絡

EPUB 3定義腳本執行的兩種脈絡：

容器限制─當腳本的執行只發生在一個[html]iframe元素中；以及
書脊層級─當腳本直接在一份頂層內容文件中執行。
註釋
腳本可以其他脈絡執行，但是閱讀系統 對這些脈絡的支援為選擇性。例如，有腳本的SVG文件可以透過一個[html]object元素所參照。

請參見[epub-rs-33]處理腳本以獲得更多資訊。

無論EPUB製作者直接透過一個script元素嵌入代碼，或者透過元素的src屬性進行參照，都不影響其執行脈絡。

EPUB製作者以何脈絡使用腳本，會影響到腳本可以實行的動作，以及閱讀系統支援的可能性，如以下子章節所說明。

註釋
請參見H.2 腳本脈絡以獲得兩種脈絡間的差異範例。

6.3.2.2.1 受容器限制的腳本

一個受容器限制的腳本為以下其一：

為一個[html]script元素的實例，其包含一份XHTML內容文件裡，該文件透過[html]iframe元素嵌入到另一份XHTML內容文件中。

為一個[svg]script文件的實例，其包含在一份SVG內容文件中，該文件透過[html]iframe元素嵌入到另一份XHTML內容文件中。

一個受容器限制的腳本不得包含變更嵌入其EPUB內容文件之DOM的程序（且就是包含iframe元素的那一份）。其也不得包含操控其包含方塊的程序。

EPUB製作者應該注意閱讀系統對受容器限制腳本的支援僅推薦用於可重排的文件[epub-rs-33]。更進一步說，閱讀系統在固定版面文件中對其支援為選擇性。

EPUB製作者應該確保受容器限制的腳本能在不具腳本支援的閱讀系統中優雅降級（請參見6.3.2.5 腳本回退）。

註釋
EPUB製作者選擇限制腳本的用途，限縮到受容器限制的模型可以確保有腳本與沒有腳本內容的使用者體驗一致（例如分頁行為一致）。

6.3.2.2.2 書脊層級腳本

書脊層級腳本為[html]script或[svg]script元素的實例，其包含在一份頂層內容文件中。

EPUB製作者應該注意閱讀系統對頂層腳本的支援僅推薦應用於固定版面文件，以及設定為捲動的可重排文件[epub-rs-33]。更進一步，閱讀系統對其他所有脈絡的支援都為選擇性。

包含書脊層級腳本的頂層內容文件應該在腳本被關閉或者無法取得時，依然能在沒有任何資訊丟失或者其他明顯劣化的狀況下，讓使用者可以消費（例如透過部署漸進強化技巧或者回退）。頂層文件如果無法不能在無腳本環境中被處理，會造成EPUB出版品無法被閱讀。

6.3.2.3 事件模型

本節不具規範性。

EPUB製作者在為其EPUB出版品添加腳本功能時，應該廣泛考量各種可能的閱讀系統實作（像是，並非所有設備都擁有實體鍵盤，以及在許多狀況下，軟體鍵盤只會在有文字輸入元素時啟動）。結論上而言，EPUB製作者不應該僅依賴鍵盤事件；他們應該總能提供替代的方式來啟動預期的動作。

6.3.2.4 腳本可及性

包含腳本的EPUB內容文件應該部署相關的[wai-aria]無障礙輔助技巧以確保所有使用者可以消費內容。

6.3.2.5 腳本回退

包含腳本的EPUB內容文件 可以提供對這些內容的回退，無論使用固有的回退機制（像是[html]的object以及canvas元素就有提供）或者，當不能使用固有回退時，可以使用宣告層級回退。

EPUB製作者必須確保腳本僅生成核心媒體類型資源或者斷片等。

7. EPUB導覽文件

7.1 介紹

本節不具規範性。

EPUB導覽文件為EPUB出版品中的必要元件。其允許EPUB製作者包含一份人類與機器都可以讀取的全域導覽層，以能確保增進對使用者的易用性與可及性。

EPUB導覽文件為一份特化類型的XHTML內容文件，定義了供閱讀系統使用的目次。也可以包含其他特化的導覽元素，像是 頁面列表，以及關鍵地標列表。這些導覽元素在其內容有額外的限制，以便於進行處理。

EPUB導覽文件並非僅供機器處理，然而，對於EPUB導覽文件特化導覽元素的之外的結構與內容沒有限制（也就是EPUB製作者可以如其他XHTML內容文件一般標記文件剩下的部分。）就結果而言，其也可以作為線性閱讀順序中的一部分，能避免提供多份目錄。EPUB製作者可以利用hidden屬性隱藏僅供機器閱讀的導覽元素（像是頁面列表）。

請注意閱讀系統在從EPUB導覽文件中取得資訊生成導覽介面時，會除去腳本、樣式以及HTML格式，這可能會讓結果難以閱讀。如果EPUB製作者需要這樣的格式以及功能，也應該將EPUB導覽文件包含在書脊中。為導覽文件的腳本與樣式使用漸進強化技巧，能夠確保內容在以非瀏覽器脈絡處理時，也能維持其完整。

7.2 導覽文件規定

一份合乎規定的EPUB導覽文件：

必須合乎定義在6.1.2 XHTML規定中XHTML內容文件的內容符合性規定；

必須 合乎定義在7.3 nav元素：限制中對nav元素的規定；

必須如7.4.2 toc nav元素所定義，包含唯一一個toc nav元素。

7.3 nav元素：限制

當在EPUB導覽文件中nav元素帶有epub:type屬性，本規格對該元素及其子孫向的內容模型限制如下：

內容模型：
nav
按此順序：

h1-h6 [0或1]

ol [唯一]

ol
按此順序：

li [1或多個]

li
按此順序：

(span或a) [唯一]

ol [某些狀況為必要]

span以及a
以任何順序：

HTML段落型內容[1或多個]

請注意對於允許用於這些元素的屬性沒有任何限制。

請參見以下定義以獲得額外的規定。

以下對nav元素內容模型的打磨解釋了各種元素的目的以及限制：

nav元素的ol子元素代表了內容導覽的主要層級。

具有順序列表中的每一項列表項目都代表了一個標題、架構、或者其他領域的項目。子元素a描述連結該指向的目標，同時一個span元素用來當作標頭以將列表區分為明顯的群組（例如，EPUB製作者可以將一個大的插畫列表區分為多個列表，每一章各一份）。

a或span元素必須在連接所有子內容，並且使用空白正規劃規則裡後，提供為非零長度的文字標籤。當要判斷是否合於此規定時，整合後的標籤必須為非文字的子元素使用title或alt屬性來包含文字內容。

如果一個aspan元素包含HTML嵌入內容[html]的實例，由於無法以固有方式提供替代文字，該元素必須也包含一個title屬性提供處理連結標籤使用的替代文字。

透過a元素的href屬性提供URL[url]參照：

在toc nav、landmarks nav以及page-list nav中時，必須解析到頂層內容文件或其中的斷片。

在所有其他的nav類型時，可以參照外於EPUB容器的內容（也就是放在網頁上的資源）。

ol（排序列表）元素代表了次要的內容層級（也就是所有章節中的子章節標題）可以在a元素之後。

ol（排序列表）元素必須在一個span元素之後（span元素不能在「單葉（leaf）」li元素中）。

無論前面是一個a或span元素，每一份子列表必須依附定義在本章節供建構主要導覽列表的內容規定。

範例 50: 導覽元素的基本模式
<nav epub:type="…">
   <h1>…</h1>
   <ol>
      <li>
         <a href="chap1.xhtml">
            一個基本的單葉節點
         </a>
      </li>
      <li>
         <a href="chap2.xhtml">
            一個有連結的標題
         </a>
         <ol>
            …
         </ol>
      </li>
      <li>
         <span>一個沒連結的標題</span>
         <ol>
            …
         </ol>
      </li>
      <li>
         <a href="appendix.xhtml">
            <img src="app1.jpg" alt="An image-based heading"/>
         </a>
      </li>
   </ol>
</nav>
警告事項
儘管在nav元素中的標題與連結允許使用任何[html]段落型內容，App形式的閱讀系統經常只會處理間單的文字標籤。因為這些App建構自己的導覽小工具，並非基於HTML處理，這些工具通常無法保留嵌入圖片或者多媒體、MathML與行內樣式和其他基於元素或者屬性的處理程序。EPUB製作者應該避免使用這些類型的元素，因為無法顯示會產生易用性問題。

作為合規的XHTML內容文件，EPUB製作者 可以將EPUB導覽文件包含在書脊之中。

在本規格的脈絡中，nav元素中列表項目的預設顯示樣式等同於list-style: none特性[csssnapshot]。EPUB製作者可以使用CSS指定替代的列表樣式供文件放書脊中處理使用。

7.4 nav元素：類型

7.4.1 介紹

本節不具規範性。

定義在EPUB導覽文件中的nav元素要在語義上透過其epub:type屬性的值進行區分。

本規格定義了三種導覽協助：

toc
識別該nav元素包含目次。toc nav為EPUB製作者唯一必須包含在EPUB導覽文件中的導覽協助。

page-list
識別該nav元素包含印刷或其他固定分頁來源之頁面列表。

landmarks
識別該nav元素包含興趣點列表。

一份EPUB導覽文件中，以上各類型最多可以各包含一份導覽協助。

EPUB導覽文件可以包含額外的導覽類型。請參見7.4.5 其他nav元素以獲得更多資訊。

7.4.2 toc nav元素

toc nav元素定義主要導覽用的架構。其概念上對應到印刷作品的目次（例如，其提供了對出版品中主要結構章節的導覽）。

EPUB製作者 應該在toc nav元素中對參照對象排序時能反映以下兩者：:

書脊中EPUB內容文件的參照順序；以及

目標元素在其各自EPUB內容文件中的順序。

7.4.3 page-list nav元素

page-list元素提供內容中固定頁面邊界的導覽。這些邊界可以對應到一份固定翻頁的來源，像是印刷書或者可以專門對EPUB出版品定義。

page-list nav元素在EPUB導覽文件中為選擇性，並且不得出現多於一次。

page-list nav元素應該包含唯一一個ol子項（也就是不得有巢狀子列表）。

EPUB製作者可以在個別EPUB內容文件中，使用pagebreak術語[epub-ssv-11]來識別page-list參照的標的。

7.4.4 landmarks nav元素

landmarks nav元素用於識別內容中的基礎結構元件，讓閱讀系統得以讓使用者能有效率地進行存取（例如，透過使用者介面上的按鍵）。

landmarks nav元素在EPUB導覽文件中為選擇性，並且 and 不得出現多於一次。

landmarks nav元素應該包含唯一一個ol子項（也就是不得有巢狀子列表）。

landmarks nav元素的子a元素中，epub:type屬性為必要。在landmarks nav元素中連結標的的結構化語義由該屬性的值所決定。

範例 51: 一個基本的landmarks nav
在本範例中，epub:type屬性值用於結構性語義，其來自 [epub-ssv-11]。

<nav epub:type="landmarks">
   <h2>Guide</h2>
   <ol>
       <li>
          <a epub:type="toc"
             href="#toc">
            目次
          </a>
       </li>
       <li>
          <a epub:type="loi"
             href="content.html#loi">
            插畫列表
          </a>
       </li>
       <li>
          <a epub:type="bodymatter"
             href="content.html#bodymatter">
            內容開始
          </a>
       </li>
   </ol>
</nav>
landmarks nav不得包含多個具有相同epub:type值的資料，指向相同的資源或者其中的斷片。

EPUB製作者應該限制定義在landmarks nav中的項目數，僅提供閱讀系統可能會用於其使用者介面的項目。該元素不是為了重新做一次目次。

以下地標在可用時，推薦包含在內：

bodymatter[epub-ssv-11]─閱讀系統常會用到本地標來自動讓使用者開始閱讀時，跳過front matter（本文前）的部分。
toc[epub-ssv-11]─當在書脊中有目次時，閱讀系統可以使用該地標將使用者帶到包含目次的文件。
其他可能包含在landmarks nav裡的為關鍵參考章節，像是索引和詞彙表。

雖然landmarks nav是為了供閱讀系統使用，EPUB製作者還是應該確保landmarks nav的標籤可以供人類閱讀。閱讀系統可以將這些連結直接提供給讀者。

7.4.5 其他nav元素

EPUB導覽文件可以在前章節中定義的toc、page-list以及landmarks nav元素之外，另包含一或多個nav元素。如果這些nav元素是為了供閱讀系統處理使用，其必須擁有一個epub:type屬性，並且受到7.3 nav元素：限制中定義的內容模型限制所規範。

本規格不對任何額外的nav元素添加語義上的限制：他們可以呈現為任何資訊領域提供導覽用語義，以及他們可以包含同類或者異質語義的連結目標。

範例 52: 添加一個客製化導覽元素
在本範例中，語義lot指示EPUB製作者添加了一個「表格列表」導覽元素。

<nav
    epub:type="lot"
    aria-labelledby="lot">
   <h2 id="lot">List of tables</h2>
   <ol>
      <li>
         <span>第一章中的表格</span>
         <ol>
            <li>
               <a href="chap1.xhtml#table-1.1">
                  表格1.1
               </a>
            </li>
            <li>
               <a href="chap1.xhtml#table-1.2">
                  表格1.2
               </a>
            </li>
         </ol>
      </li>
      …
   </ol>
</nav>
7.5 用於書脊中

本節不具規範性。

雖然可以將EPUB導覽文件再利用於書脊裡，但常見的狀況是，並非所有導覽結構或者其中的分支都為必要。EPUB製作者常會想要隱藏頁面列表以及地標導覽元素，並且裁減目次，尤其是有太多子章節層級的書。

對具備顯示範圍的閱讀系統而言，display特性[csssnapshot]可以控制EPUB導覽文件的視覺處理，但沒有顯示範圍（viewport）的閱讀系統就可能不會支援CSS了。為了更有效確保在這些閱讀系統的處理正確，EPUB製作者應該使用[html]hidden屬性來指示哪一（如果有）部分的導覽資訊需要在內容留處理中除外。

hidden屬性不會影響閱讀系統如何在內容流外處理導覽資料（像是透過閱讀系統提供的專用導覽使用者介面）。

註釋
hidden屬性可以和display特性一起使用，讓跨所有閱讀系統的互通性擴到最大。

範例 53: 在書脊中隱藏一個nav元素
在本範例中，nav元素中hidden屬性的存在指示，在書脊處理該文件時，頁面列表將會從內容流處理中排除。

<nav
    epub:type="page-list"
    hidden="hidden">
   <h2>Pagebreaks of the print version, third edition</h2>
   <ol>
      <li>
         <a href="frontmatter.xhtml#pi">
            I
         </a>
      </li>
      …
   </ol>
</nav>
範例 54: 隱藏nav元素中的一個分支
在本範例中，在書脊中不想被處理的分支（ol元素）有一個hidden屬性。在處理時，會限制目次僅顯示兩個最上層的樹狀層級。

<nav
    epub:type="toc"
    id="toc">
   <h1>Table of contents</h1>
   <ol>
      <li>
         <a href="chap1.xhtml">
            Chapter 1
         </a>
         <ol>
            <li>
               <a href="chap1.xhtml#sec-1.1">
                  Chapter 1.1
               </a>
               <ol hidden="">
                  <li>
                     <a href="chap1.xhtml#sec-1.1.1">
                        Section 1.1.1
                     </a>
                  </li>
                  …
               </ol>
            </li>
            …
         </ol>
      </li>
      …
   </ol>
</nav>
8. 版面處理控制

8.1 介紹

本節不具規範性。

處理上的資訊無法全部透過EPUB所奠基、依賴的技術進行表述。例如，雖然有CSS的HTML可以提供強力的排版能力，但這些能力限於被處理的文件範圍內。

本章節定義一些特性，能讓EPUB製作者表達包裝層級處理上的意圖（像是僅能由EPUB閱讀系統所實做的功能）。如果一個閱讀系統支援想要的處理，這些特性能讓使用者看到EPUB製作者最理想的設計。

8.2 固定版面

8.2.1 介紹

本節不具規範性。

EPUB出版品，不像印刷書或者PDF檔案，設計上就是會變動。內容流動，或者稱為重排，能適應螢幕以及使用者的需求。如同在排版與CSS中所提出的「內容呈現可由讀者調整成適合的樣貌，而不是讀者非得去配合特定的內容呈現形式。」[epub-overview-33]

但這項原則並非對所有類型的文件都通用。有些內容與設計彼此交織而不可能分離。任何對外觀的變更都可能會造成意義的改變或者失去所有意義。當可重排的EPUB無法適用於該內容時，固定版面文件給予EPUB製作者對呈現很大的控制權。

EPUB製作者可以使用包裝文件中一系列的特性來定義固定版面，控制在閱讀系統中的處理。此外，他們也可以為每一份EPUB內容文件設定固定版面的頁面尺寸。

註釋
EPUB 3包含多重表現固定版面內容的機制。當固定版面內容為必要時，EPUB製作者需要從許多面向決定所要採用的機制，包含想要的精準程度、檔案大小、可及性等。本章節並不試圖教導EPUB製作者選擇機制。

8.2.2 固定版面包裝設定

8.2.2.1 版面

rendition:layout特性指定內容為可重排（reflowable）或者預先分頁（pre-paginated）。

當在一個meta 元素中指rendition:layout特性時，其指示分頁或者可重排版面樣式套用到全域（也就是所有的書脊項目）。

EPUB製作者必須在 rendition:layout特性中使用以下值：

reflowable
內容並非預先分頁（也就是閱讀系統在處理時採動態分頁）。預設值。

pre-paginated
本內容為預先分頁（也就是閱讀系統在處理時，每一個書脊中的 itemref處理成正好一頁）。

註釋
閱讀系統通常會對預先分頁文件套用使用者或者使用者代理樣式表進行限制或者拒絕，因為動態變更樣式很有可能會對這些文件的固有特性造成非預期的結果。EPUB製作者應該在使用預先分頁取代可重排內容時，考量這些限制對易用性與可及性上的負面影響。請參見指引1.4 - 提供文字設定[uaag20]以獲得相關資訊。

當書脊項目的特性設定為pre-paginated時，該內容尺寸必須如8.2.2.6 內容文件尺寸之定義般設定。

EPUB製作者不得宣告多於一次的rendition:layout特性。

也不得使用refines屬性來宣告該特性。請參見8.2.2.1.1 版面覆寫以了解如何針對單一EPUB內容文件設定該特性。

範例 55: 有媒體查詢（media queries）的固定版面文件
在本範例中，文件版面設定成pre-paginated（也就是定義上的固定版面文件）。更進一步，媒體查詢[mediaqueries-3]用來將不同樣式表適用於三種不同裝置範疇。請注意媒體查詢只會是影響套用到文件的樣式表；透過viewport meta標籤設定構成的內容區域尺寸為固定。

包裝文件：

<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      …
   </metadata>
   …
</package>
XHTML：

<html …>
   <head>
      <meta
          name="viewport"
          content="width=1200,
          height=900"/>
      
      <link
          rel="stylesheet"
          href="eink-style.css"
          media="(max-monochrome: 3)"/>
         
      <link
          rel="stylesheet"
          href="skinnytablet-style.css"
          media="((color) and (max-height:600px) and (orientation:landscape),
                  (color) and (max-width:600px) and (orientation:portrait))"/>
      
      <link
          rel="stylesheet"
          href="fattablet-style.css"
          media="((color) and (min-height:601px) and (orientation:landscape),
                  (color) and (min-width:601px) and (orientation:portrait))"/>	
   </head>
   …
</html>
8.2.2.1.1 版面覆寫

EPUB製作者可以在個別書脊itemref元素中指定以下特性，以讓該書脊項目覆寫過全域值：

rendition:layout-pre-paginated
指定該書脊項目為預先分頁。
rendition:layout-reflowable
指定該書脊項目為可重排。
EPUB製作者不得在任何書脊項目中使用多於一個的覆寫。

8.2.2.2 頁面方向

rendition:orientation特性指定了EPUB製作者希望內容被處理的頁面方向。

當在一個meta元素中指定rendition:orientation特性時，其指示預期的頁面方向套用到全域（也就是所有的書脊項目）。

EPUB製作者 必須在rendition:orientation特性中使用以下值：

landscape
閱讀系統應該將內容處理為landscape（橫寬直窄）方向。

portrait
閱讀系統應該將內容處理為portrait（直寬橫窄）方向。

auto
內容不受頁面方向限制。預設值。

EPUB製作者不得宣告多於一次的rendition:orientation特性。

也不得使用refines屬性來宣告該特性。請參見8.2.2.2.1 方向覆寫以了解如何針對單一EPUB內容文件設定該特性。

範例 56: 將全域指定為landscape方向
在本範例中，書脊中的各項目都將被處理成landscape模式。

<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>

      <meta
          property="rendition:orientation">
         landscape
      </meta>
   </metadata>
   …
</package>
8.2.2.2.1 方向覆寫

EPUB製作者可以在書脊itemref元素中指定以下特性，以讓該書脊項目覆寫過全域值：

rendition:orientation-auto
指定閱讀系統可自行決定將該書脊項目處理成何種頁面方向。
rendition:orientation-landscape
指定閱讀系統應該將該書脊項目處理成landscape方向。
rendition:orientation-portrait
指定閱讀系統應該將該書脊項目處理成portrait方向。
EPUB製作者不得在任何書脊項目中使用多於一個的覆寫。

8.2.2.3 同步跨頁

rendition:spread特性指定了希望的閱讀系統同步跨頁行為。

當在一個meta元素中指定rendition:spread特性時，其指示預期的同步跨頁行為套用到全域（也就是所有的書脊項目）。

EPUB製作者必須在rendition:spread特性中使用以下值：

none
不將書脊項目包含在同步跨頁中。閱讀系統應該將該項目以單獨顯示區域顯示，並置放在螢幕的中央。

landscape
只有在設備為landscape方向時，將書脊項目處理成同步跨頁。

portrait （不再推薦）
不再推薦使用僅於portrait方向時跨頁。

EPUB製作者應該使用替代的值「both」，但得讓跨頁能在portrait方向中可閱讀，同時在landscape中也可閱讀。

both
無論何種設備方向，都應該處理同步跨頁。

auto
EPUB製作者沒有定義明確的同步跨頁行為。預設值。

EPUB製作者不得宣告多於一次的rendition:spread特性。

也不得使用refines屬性來宣告該特性。請參見8.2.2.3.1 同步跨頁以了解如何針對單一EPUB內容文件設定該特性。

註釋
當同步跨頁用於XHTML和SVG內容文件的脈絡時，單一頁面的尺寸分別透過viewport meta元素以及viewBox屬性來提供。

註釋
請參見spine元素以獲得關於使用page-progression-direction屬性指定全域行頁方向，以及在內容文件中指定局部page-progression-direction的相關資訊。

範例 57: 一本沒有同步跨頁的固定版面EPUB出版品
<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      
      <meta
          property="rendition:spread">
         none
      </meta>
   </metadata>
   …
</package>
圖1 處理三份沒有同步跨頁的固定版面文件。
（漫畫感謝xkcd提供，基於cc by-nc 2.5授權。）
Progression of FXL pages both in portrait and in landscape modes, showing one page at a time everywhere
圖片說明
範例 58: 指定只在landscape方向時使用同步跨頁
<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      
      <meta
          property="rendition:spread">
         landscape
      </meta>
   </metadata>
   …
</package>
圖2 處理三份僅在landscape方向時同步跨頁的固定版面文件。
（漫畫感謝xkcd提供，基於cc by-nc 2.5授權。）
Progression of FXL pages both in portrait and in landscape modes, showing one page at a time in portrait and using synthetic spread in landscape.
圖片說明
範例 59: 指定在landscape方向與portrait方向都使用同步跨頁
也請見圖3。

<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      
      <meta
          property="rendition:spread">
         both
      </meta>
   </metadata>
   …
</package>
圖3 處理三份在landscape方向與portrait方向都同步跨頁的固定版面文件
（漫畫感謝xkcd提供，基於cc by-nc 2.5授權。）
Progression of FXL pages both in portrait and in landscape modes, using synthetic spread in both cases.
圖片說明
範例 60: 覆寫全域跨頁行為
在本範例中，EPUB製作者為書脊中的介紹頁面覆寫了全域設定改為可重排。意圖要閱讀系統將其處理成可重排的文件。

<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      <meta
          property="rendition:spread">
         both
      </meta>
   </metadata>
   
   <spine>
      <itemref
          idref="introduction"
          properties="rendition:layout-reflowable"/>
      …
   </spine>
   …
</package>
圖4 將介紹文件處理成可重排的版面，後接三張固定版面文件在portrait方向中同步跨頁。
（漫畫感謝xkcd提供，基於cc by-nc 2.5授權。）
Progression of FXL pages both in portrait using synthetic spread in both cases, preceded by an introduction with reflowable contnt.
圖片說明
8.2.2.3.1 同步跨頁覆寫

EPUB製作者可以在書脊itemref元素中指定以下特性，以讓該書脊項目覆寫過全域值：

rendition:spread-auto
指定閱讀系統可自行決定何時將書脊項目處理成同步跨頁。
rendition:spread-both
指定閱讀系統應該在portrait和landscape方向都將書脊項目處理成同步跨頁。
rendition:spread-landscape
指定閱讀系統應該只在landscape方向將書脊項目處理成同步跨頁。
rendition:spread-none
指定閱讀系統不應將書脊項目處理成同步跨頁。
rendition:spread-portrait
不再推薦rendition:spread-portrait特性。

請參見[epubpublications-301]中對spread-portrait特性定義以獲得更多資訊。

EPUB製作者不得在任何書脊項目中使用多於一個的覆寫。

8.2.2.4 跨頁配置

當閱讀系統處理同步跨頁時，預設的行爲是處理下一份EPUB內容文件，置放在下一個可用未填滿的顯示區域中，以填滿跨頁。下一個可用的顯示區域由給出的行頁方向，或者EPUB內容文件中本地宣告決定。EPUB製作者可以在書脊itemref元素中指定以下特性來覆寫這種自動填滿行為，強制閱讀系統置放文件到指定的顯示區域中：

rendition:page-spread-center
rendition:page-spread-center特性為spread-none特性的別名，可將書脊項目置中。
rendition:page-spread-left
rendition:page-spread-left特性為page-spread-left特性的別名，可將書脊項目在兩頁跨頁中置於左手邊的格中。
rendition:page-spread-right
rendition:page-spread-right特性為page-spread-right特性的別名，可將書脊項目在兩頁跨頁中置於右手邊的格中。
rendition:page-spread-center、rendition:page-spread-left以及rendition:page-spread-right特性可以適用於預先分頁以及可重排內容兩方。但僅在閱讀系統建立同步跨頁時才適用。

雖然EPUB製作者經常只是在特定裝置方向時使用跨頁，但內容自身不會顯示真正的跨頁（也就是閱讀系統必須將兩張連續的頁面為了易讀性而以相鄰處理，像是兩頁的地圖）。為了只是兩張連續的頁面以真正的跨頁方式呈現，EPUB製作者應該對書脊項目中兩份相鄰的EPUB內容文件使用rendition:page-spread-left以及rendition:page-spread-right特性，並且對單頁或者兩頁顯示都能接受的書脊項目刪去這些特性。

EPUB製作者不得為書脊項目宣告多於一個rendition:page-spread-*特性，及/或其沒有字首的同等值（然而，在閱讀系統僅支援其中一項特性時，同時指定「rendition:page-spread-left page-spread-left」合規。

註釋
rendition:page-spread-left以及 rendition:page-spread-right特性之所以被創造出來，是為了使用單一用語集包括所有固定版面特性。EPUB製作者可以使用任一組特性，但是較舊的閱讀系統可能僅會識別沒有字首的版本。

rendition:page-spread-center之所以被創造出來是為了讓EPUB製作者易於了解在兩頁跨頁與單一中央頁間切換的過程。EPUB製作者可以使用rendition:page-spread-center或spread-none其一來關閉閱讀系統中的跨頁行為。

範例 61: 開始的第一份文件位於右頁
<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
          reflowable
      </meta>
	  
      <meta
          property="rendition:spread">
          landscape
      </meta>
      …
   </metadata>
   <spine page-progression-direction="ltr">
      …
      <itemref
          idref="first-panel"
          properties="rendition:page-spread-right"/>
      …
   </spine>
</package>
圖5 處理三份固定版面文件，在landscape方向中同步跨頁右頁起。
（漫畫感謝xkcd提供，基於cc by-nc 2.5授權。）
Progression of FXL pages in landscape modes, showing synthetic spread in both cases but with the first page appearing on the right side of the first page.
圖片說明
範例 62: 在跨頁中置放單獨書脊項目
在本範例中，EPUB製作者希望在任何設備方向下，閱讀系統都可以以同步跨頁創建兩頁固定版面置中對開。請注意EPUB製作者對其他部分（可重排）未定義跨頁內容，因此預設全域rendition:spread初始值為auto。

<package …>
   …
   <spine page-progression-direction="ltr">
      …
      <itemref
          idref="center-plate-left"
          properties="rendition:spread-both rendition:page-spread-left"/>
      <itemref
          idref="center-plate-right"
          properties="rendition:spread-both rendition:page-spread-right"/>
      …
   </spine>
</package>
範例 63: 建立一個置中版面
<package …>
   <metadata …>
      …
      <meta
          property="rendition:layout">
         pre-paginated
      </meta>
      <meta
          property="rendition:spread">
         auto
      </meta>
   </metadata>
   <spine>
      …
      <itemref
          idref="center-plate"
          properties="rendition:page-spread-center"/>
      …
   </spine>
   …
</package>
8.2.2.5 顯示範圍空間（不再推薦）

rendition:viewport特性讓EPUB製作者能為rendition:layout特性設置為pre-paginated的XHTML以及SVG內容文件，表述CSS初始包含塊（initial containing block ,ICB）[css2]。

不再推薦使用本特性。

請參見[epubpublications-301]中對rendition:viewport特性的定義以獲得更多資訊。

8.2.2.6 內容文件空間

本章節定義了規則用於表述以及詮釋固定版面文件的空間特性。

固定版面文件指定其初始包含塊[css2]以該格式能適用的方式：

在XHTML中表述
對XHTML固定版面文件而言，初始包含塊[css2]可由viewport meta標籤中取得需要的height與width定義，其：

height特性必須其值為正數，或者使用關鍵字device-height；以及
width特性必須其值為正數，或者使用關鍵字device-width。
device-width以及device-height值可分別參照為閱讀系統顯示範圍之100%寬與高。

EPUB製作者不得在單一viewport meta標籤或者指定多重viewport meta標籤來重複指定height或width定義。

範例 64: 在viewport meta標籤中指定初始包含塊
<html …>
   <head>
      …
      <meta
          name="viewport"
          content="width=1200, height=600"/>
      …
   </head>
   …
</html>
在SVG中表述
對SVG固定版面文件而言，初始包含塊[css2]尺寸必須使用viewBox屬性[svg]進行表述。

範例 65: 在viewBox屬性中指定初始包含塊
在本範例中，viewBox屬性設定ICB的比例為844像素寬與1200像素高。

<svg xmlns="http://www.w3.org/2000/svg"
     version="1.1" 
     viewBox="0 0 844 1200">
   …
</svg>
註釋
初始包含塊定義只會影響所位於的文件。同一本出版品，包含塊在其他內容文件中的尺寸可能不同。
8.3 可重排版面

儘管控制EPUB內容文件的處理來建立固定版面是明顯的需求，也無法由其他技術所處理，也需要考量可重排內容對EPUB出版品的獨特性（例如，如何控制顯示範圍中的內容流動）。本章節定義特性能讓EPUB製作者控制可重排內容的呈現面向。

8.3.1 rendition:flow特性

rendition:flow特性指定EPUB製作者的偏好，告知閱讀系統應該如何處理內容溢流。

當在一個meta元素中指定rendition:flow特性時，其指示EPUB製作者對溢流內容處理的全域偏好（也就是對所有的書脊項目）。EPUB製作者可以指示偏好為分頁或者捲動。對捲動的內容，也可以指定連續的EPUB內容文件要被一起處理成一份連續捲動的顯示，還是分開來處理（也就是在每一份之間提供動態分頁）。

EPUB製作者必須對rendition:flow特性使用以下值之一：

paginated
對所有溢流內容進行動態分頁。

scrolled-continuous
將所有EPUB內容文件的溢流內容處理成可捲動，並且EPUB出版品以一個連續卷軸方式呈現，可以從一項書脊項目捲到另一個書脊項目（除了區域覆寫外）。

請注意EPUB製作者不應製作出版品其中不同資源包含不同的區塊流動方向，這樣在EPUB閱讀系統處理連續捲動時會出問題。

scrolled-doc
將所有EPUB內容文件的溢流內容處理成可捲動，每一項書脊項目都以區分的可捲動文件呈現。

auto
將溢流內容使用閱讀系統預設方式或者使用者偏好，以可適用的方式進行處理。預設值。

請注意當兩份可重排的EPUB內容文件在書脊中為序列時，對其[html]a href="https://html.spec.whatwg.org/multipage/#the-body-element" id="ref-for-index-term-body-2">body元素的預設處理需要永遠透過page-break-before特性[csssnapshot]，值設定為always。在使用rendition:flow特性時，EPUB製作者可以透過合適的樣式表宣告覆寫其行為，如果閱讀系統支援的話。

EPUB製作者不得宣告多於一次的rendition:flow特性。

也不得使用refines屬性宣告該特性。請參見8.3.1.1 Spine覆寫為個別EPUB內容文件設定該特性。

圖6 處理一本僅有一個書脊項目的EPUB出版品，其rendition:flow設定為paginated。
The continuous progression of paginated content produced for a single document.
圖片說明
圖7 處理一本有著多個書脊項目的EPUB出版品，其rendition:flow設定為paginated。
The continuous progression of paginated content produced for each document with transitions to
					new pages between documents.
圖片說明
圖8 處理一本僅有一個書脊項目的EPUB出版品，其rendition:flow設定為 scrolled-continuous。
The progression of a continuous scroll of content extends vertically off the user's screen,
					with new documents added to the bottom as encountered.
圖片說明
圖9 處理一本有著多個書脊項目的EPUB出版品，其rendition:flow設定為scrolled-doc。
The progression of scrollable documents depicting how only the content within each document
					is scrollable.
圖片說明
8.3.1.1 Spine覆寫

EPUB製作者可以在書脊個別itemref元素中指定以下特性以讓該書脊項目覆寫全域值：

rendition:flow-auto
指示EPUB製作者對溢流內容的處理沒有偏好。
rendition:flow-paginated
指示EPUB製作者偏好以動態分頁處理溢流內容。
rendition:flow-scrolled-continuous
指示EPUB製作者偏好以捲動呈現處理溢流內容，且有這特性的連續書脊項目需要被以連續卷軸的方式處理。
rendition:flow-scrolled-doc
指示EPUB製作者偏好以捲動呈現處理溢流內容，且有這特性的每一份書脊項目需要被以分開的捲動文件處理。
EPUB製作者不得在任何書脊項目中使用多於一次的覆寫。

範例 66: 覆寫全域分頁流動宣告
在本範例中，EPUB製作者意圖讓一份分頁的EPUB出版品有一份捲動的目次。

<package …>
<metadata …>
	…
	<meta
		property="rendition:flow">
		paginated
	</meta>
	…
</metadata>

…

<spine>
	<itemref
		idref="toc"
		properties="rendition:flow-scrolled-doc"/>
	<itemref
		idref="c01"/>
</spine>
</package>
8.3.2 rendition:align-x-center特性

rendition:align-x-center特性指定書脊項目應該在顯示範圍或者跨頁中水平置中。

本特性不得被設定為全域供所有EPUB內容文件使用（也就是在meta元素中而沒有refines屬性）。其只能透過itemref元素的properties屬性，供單獨EPUB內容文件以書脊覆寫使用。

註釋
本特性原本開發用於處理「Naka-Tobira（中扉）」（章節標題頁），因為在內容處理時沒有可靠的置中控制項。然而，隨著CSS分頁媒體的進步，這項特性預期會變成不再推薦。推薦EPUB製作者在可以使用CSS解決時使用。

9. 媒體層疊

9.1 介紹

本節不具規範性。

包含同步聲音旁白的作品，其範例包括主流電子書、教育工具以及專為無法閱讀印刷書個人而特別製作格式的電子書。在EPUB 3規格中，EPUB製作者可以製作這類型的電子書，使用媒體層疊文件來描述預錄聲音旁白的時間點，以及如何與EPUB內容文件標記相關聯。本規格定義了供媒體層疊使用的檔案格式，其為[smil3]之子集，[smil3]為W3C推薦規格，以XML格式表現同步多媒體資訊。

透過媒體層疊啟動文字與聲音的同步，可為任何難以閱讀傳統書籍文字的使用者提供增強的無障礙輔助能力。媒體層疊也未因為任何理由而無法閱讀文字的讀者提供了連續聆聽體驗，傳統嵌入聲音的技巧無法提供這種體驗。甚至可以進一步應用在非傳統無障礙輔助考量到的用途之上（例如供語言學習使用）。

媒體層疊這項特色對於不支援的EPUB閱讀系統來說像是透明一般。在EPUB出版品中包含媒體層疊不會影響到對媒體層疊無意識的閱讀系統處理EPUB出版品時的能力，因為媒體層疊就只會不呈現出來而已。

EPUB中的媒體層疊不等同於有聲書，有聲書主要以音訊為基礎，有時會將文字以替代格式提供。W3C推薦標準[audiobooks]可供建立音訊出版品。

雖然本規格的未來版本可能會加上對影片媒體的支援（例如讓文字與手語同步播放的書），但本版本僅支援讓音訊媒體與EPUB內容文件同步播放。

9.2 媒體層疊文件

9.2.1 媒體層疊文件規定

一份媒體層疊文件：

必須合乎定義在G.3 媒體層疊綱要中的媒體層疊使用的綱要，並且合乎在9.2.2 媒體層疊文件定義中的所有內容合規性規定。

可以參照多於一份的EPUB內容文件，但不得讓多於一份的媒體層疊文件參照相同的EPUB內容文件。

9.2.2 媒體層疊文件定義

所有定義在本章節中的元素，除另有指定外，皆[xml]位於命名空間[xml-names]https://www.w3.org/ns/SMIL。

9.2.2.1 smil元素

smil元素封裝了所有位於媒體層疊文件中的資訊。

元素名稱：
smil

用途：
媒體層疊文件中需要的 根元素[xml]。

屬性：
version [必要]
指定該份媒體層疊文件所使用的[smil3]規格之版本號碼。

本屬性必須擁有值「3.0」。

id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

epub:prefix [選擇性]
宣告額外的後設資料用語字首。

請參見9.3.3 層疊中的結構語義以獲得更多資訊。

內容模型：
按此順序：

head [0或1]

body [唯一]

9.2.2.2 head元素

head元素為

元素名稱：
head

用途：
head元素為smil元素中第一個選擇性的子元素。

屬性：
無

內容模型：
metadata [0或1]

本規格不定義任何必須出現在媒體層疊文件中的後設資料特性，所以head元素為選擇性。

9.2.2.3 metadata元素

metadata元素用於在媒體層疊文件中表現後設資料。metadata元素為一延伸點，允許用來包含來自任何後設資訊結構語言的後設資料。

元素名稱：
metadata

用途：
head元素的子元素。

屬性：
無

內容模型：
從任何命名空間來的[0或多個]元素

本規格不要求在媒體層疊文件中提供任何後設資料；metadata元素供客製化後設資料需求使用。

9.2.2.4 body元素

body元素為媒體層疊文件中內容表示的開始點。其包含了由par及seq元素構成的主要序列。

元素名稱：
body

用途：
body元素為smil元素中需要的子元素。當有head元素時，位於其之後。

屬性：
epub:type [選擇性]
用來和EPUB內容文件中元素相呼應的結構語義表述。

其值為一個由空白區隔的特性類型列表。請參見9.3.3 層疊中的結構語義以獲得更多資訊。

id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

epub:textref [選擇性]
參照相關的EPUB內容文件，以及選擇性地用於識別文件中指定部分。

該值必須為路徑-相對-無-綱要-位址（path-relative-scheme-less-url）字串，選擇性地在U+0023 (#)以及位址-斷片（URL-fragment）字串之後。

內容模型：
以任何順序：

seq [0或多個]

par [0或多個]

必須包含一個par或seq。

9.2.2.5 seq元素

seq為一個序列時間容器，供媒體物件及/或子時間容器使用。

元素名稱：
seq

用途：
在body以及seq元素中可以一或多次出現的子元素。

屬性：
epub:type [選擇性]
和EPUB內容文件中元素相呼應的結構語義表述。

其值為一個由空白區隔的特性類型列表。請參見9.3.3 層疊中的結構語義以獲得更多資訊。

id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

epub:textref [必要]
參照相關的EPUB內容文件，以及選擇性地用於識別文件中指定部分。

該值必須為路徑-相對-無-綱要-位址（path-relative-scheme-less-url）字串，選擇性地在U+0023 (#)以及位址-斷片（URL-fragment）字串之後。

請參見9.3.2.1 層疊架構以獲得更多資訊。

內容模型：
以任何順序：

seq [0或多個]

par [0或多個]

必須包含一個par或seq。

9.2.2.6 par元素

par元素為供媒體物件使用的平行時間容器。

元素名稱：
par

用途：
在body以及seq元素中可以一或多次出現的子元素。

屬性：
epub:type [選擇性]
和EPUB內容文件中元素相呼應的結構語義表述。

其值為一個由空白區隔的特性類型列表。請參見9.3.3 層疊中的結構語義以獲得更多資訊。

id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

內容模型：
以任何順序：

text [唯一]

audio [0或1]

9.2.2.7 text元素

text元素參照EPUB內容文件中的一個元素。一個text元素一般參照一個文字性質的元素，但也可以參照其他EPUB內容文件的媒體元素。在沒有伴隨的audio元素時，被本元素參照的文字性質內容可以透過文字轉換語音（text-to-speech）處理。

元素名稱：
text

用途：
par元素需要的子元素。

屬性：
src [必要]
參照相關的EPUB內容文件，以及選擇性地用於識別文件中指定部分。

該值必須為路徑-相對-無-綱要-位址（path-relative-scheme-less-url）字串，選擇性地在U+0023 (#)以及位址-斷片（URL-fragment）字串之後。

id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

內容模型：
空白

註釋
本規格不對text元素的src屬性施予任何限制。然而EPUB製作者應該參照到可以透過CSS賦予樣式的內容，以使與樣式資訊的關聯有效（例如XHTML中可被觸知的內容，或者SVG中的路徑、基本形狀或者文字元素）。
註釋
[epub-rs-33]不再為閱讀系統提供播放時序媒體的播放指引（也就是自動開始播放參照的媒體）。雖然一個text元素的src屬性可能參照到嵌入的時序媒體（像是透過一個[html]video元素），對這類媒體的參照可能會有非預期的結果。
9.2.2.8 audio元素

audio元素代表一段音訊媒體。

元素名稱：
audio

用途：
par元素的選擇性子元素。

屬性：
id [選擇性]
元素的ID[xml]，其在整份文件範圍內必須為獨特。

src [必要]
相對或絕對位址字串[url]參照到一個音訊檔案。該音訊檔案必須為列於核心媒體類型資源表格中的聲音格式。

clipBegin [選擇性]
指定物理媒體的偏移量之時鐘值，呼應到一個聲音片段的開始點。

必須為一個[smil3]時鐘值。

請見H.4 時鐘值。

clipEnd [選擇性]
指定物理媒體的偏移量之時鐘值，呼應到一個聲音片段的結束點。

必須為一個[smil3]時鐘值。

請見H.4 時鐘值。

結束位址在時序上的偏移值必須在clipBegin屬性中所指定的開始偏移值之後。

內容模型：
空白

9.3 建立媒體層疊

9.3.1 介紹

本節不具規範性。

EPUB製作者可以利用一系列音訊片段來作為出版品預錄的旁白，每一段對應到EPUB內容文件的一部分。例如，單一音訊片段，一般為單一句子或者段落，但是和無法推測和其他片段的順序關係或與文字間的關係。媒體層疊透過[smil3]標記，將結構化音訊旁白與EPUB內容文件中對應的文字（或其他媒體），捆綁在一起來解決這項問題。媒體層疊實際上為SMIL 3.0簡化的子集，其定義了播放這些片段的順序。

SMIL主要用於結構化媒體的元素為body（用於主要序列）、seq（序列）以及par（平行）。（請參見9.2.2 媒體層疊文件定義以獲得更多與這些和其他SMIL元素的資訊）。

par元素為媒體層疊中最基本的組件區塊，呼應到EPUB內容文件中的句子。該元素提供了兩項關鍵資訊供內容同步使用：1)音訊片段包含了句子的旁白；以及2)一個指標對應到相關的EPUB內容文件斷片。par元素使用兩個子媒體元素來表達這些資訊：一個audio元素以及一個text元素。因為par元素的子媒體物件在平行播放中定下了時間，閱讀系統同時處理音訊片段以及EPUB內容文件斷片，就會造成同步呈現的結果。

text元素的src屬性透過其URL[url]參照相關聯的單字、語句或者其他EPUB內容文件中的斷片。audio元素的src屬性類似地參照對應音訊片段的位址並且添加選擇性的clipBegin與clipEnd屬性以指示在該片段中指定的偏移點。

範例 67: 媒體層疊供一語句或句子的標記
<par>                        
   <text
       src="chapter1.xhtml#sentence1"/>
   <audio
       src="chapter1_audio.mp3"
       clipBegin="23s"
       clipEnd="30s"/>
</par>
EPUB製作者將par元素依序列置放以建構一系列片語或句子。並非所有EPUB內容文件中的元素都會需要對應到媒體層疊文件中的par元素，只有對應到聲音旁白的元素需要。

範例 68: 一份基本的媒體層疊文件，包含了語句序列
在本範例中，body元素作為整份文件的主要序列。

<smil
    xmlns="http://www.w3.org/ns/SMIL" 
    version="3.0">
   <body>
      <par id="par1">
         <text
             src="chapter1.xhtml#sentence1"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0s"
             clipEnd="10s"/>
      </par>
      <par id="par2">
         <text
             src="chapter1.xhtml#sentence2"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="10s"
             clipEnd="20s"/>
      </par>
      <par id="par3">
         <text
             src="chapter1.xhtml#sentence3"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="20s"
             clipEnd="30s"/>
      </par>
   </body>
</smil>
EPUB製作者也可以在seq元素中添加par元素來定義更為複雜的結構，像是部以及章（請參見9.3.2.1 層疊架構）。

9.3.2 與EPUB內容文件之關係

註釋
本章節中，EPUB內容文件推定為一份XHTML內容文件。但EPUB製作者可以將媒體層疊用於SVG內容文件，但因為無法保證互通性，所以播放行為可能會不穩定。

9.3.2.1 層疊架構

媒體層疊文件中的body包含兩個元素：par元素與seq元素。這些元素的順序代表閱讀系統如何在播放時處理相對應EPUB內容文件之內容。

par元素代表了內容的斷片，像是一個字、一個詞、一段句子、表格之一格、列表項目、圖片或者其他在標記中可識別的內容片段。每一個元素識別在播放時要顯示的內容（在text元素中），以及要同步的聲音（在audio元素中）。

seq元素代表序列─seq與/或par元素的組合一起代表了內容的一個邏輯元件。EPUB製作者可以用其來表達巢狀容器，像是：章節、次要內容、標頭、表格、列表以及註解。也讓EPUB製作者可以在媒體層疊文件中保留這些容器所承繼的結構。

seq元素必須包含一個epub:textref屬性。由於seq元素並不提供同步程序，本屬性能讓閱讀系統將斷片對應到文字中的位址。

註釋
在一個seq元素中群組如章節、圖片、表格以及註釋等結構的原因是，如此一來閱讀系統可以在播放時識別其開始與結束位置。閱讀系統因此能為內容版面提供專屬的播放選項，像是跳過連續的長圖片，關閉換頁時的宣告（請見9.4 可跳過性與可跳出性），或者客製化閱讀模式以符合結構，例如表格。

範例 69: 一份媒體層疊文件其中包括巢狀seq元素
本範例呈現一個章節，同時包括一個章節表頭以及一份圖片。

媒體層疊文件：

<smil
    xmlns="http://www.w3.org/ns/SMIL"
    xmlns:epub="http://www.idpf.org/2007/ops"
    version="3.0">
   <body>

      <!-- a chapter -->
      
      <seq
          id="id1"
          epub:textref="chapter1.xhtml#sectionstart"
          epub:type="chapter">

         <!-- the section title -->
         
         <par id="id2">
            <text
                src="chapter1.xhtml#section1_title"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:23:23.84"
                clipEnd="0:23:34.221"/>
         </par>

         <!-- some sentences in the chapter -->
         
         <par id="id3">
            <text
                src="chapter1.xhtml#text1"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:23:34.221"
                clipEnd="0:23:59.003"/>
         </par>
         <par id="id4">
            <text
                src="chapter1.xhtml#text2"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:23:59.003"
                clipEnd="0:24:15.000"/>
         </par>

         <!-- a figure -->
         
         <seq
             id="id7"
             epub:textref="chapter1.xhtml#figure">
            <par id="id8">
               <text
                   src="chapter1.xhtml#photo"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:24:18.123"
                   clipEnd="0:24:28.764"/>
            </par>
            <par id="id9">
               <text
                   src="chapter1.xhtml#caption"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:24:28.764"
                   clipEnd="0:24:50.010"/>
            </par>
         </seq>

         <!-- more sentences in the chapter (outside the figure) -->
         
         <par id="id12">
            <text
                src="chapter1.xhtml#text3"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:25:45.515"
                clipEnd="0:26:30.203"/>
         </par>
         <par id="id13">
            <text
                src="chapter1.xhtml#text4"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:26:30.203"
                clipEnd="0:27:15.000"/>
         </par>
      </seq>
   </body>
</smil>
XHTML內容文件：

<html …>
   <head>
      <title>
         Media Overlays Example of
         EPUB content document
      </title>
   </head>
   <body id="sec1">
      <section
          id="sectionstart"
          epub:type="chapter">
         
         <h1 id="section1_title">
            The Section Title
         </h1>
         
         <p id="text1">
            The first phrase of the main text body.
         </p>
         
         <p id="text2">
            The second phrase of the main text body.
         </p>
         
         <figure id="figure">
            <img id="photo"
                src="photo.png" 
                alt="a photograph for which there is a caption" />
            
            <figcaption id="caption">
               The photo caption
            </figcaption>
         </figure>
         
         <p id="text3">
            The third phrase of the main text body.
         </p>
         
         <p id="text4">
            The fourth phrase of the main text body.
         </p>
      </section>
   </body>
</html>
9.3.2.2 參照文件斷片

epub:textref屬性以及text元素的src屬性，兩者都可以包含一個位址-斷片（URL-fragment）字串來參照相關EPUB內容文件中的特定部分（例如透過ID指定元素）。

對XHTML與SVG內容文件而言，位址-斷片（URL-fragment）字串應該透過其ID分別參照指定元素，或者一個SVG斷片識別碼，[svg]。

EPUB製作者可以使用其他斷片識別碼綱要，但閱讀系統可能不支援這樣的識別碼。

9.3.2.3 層疊粒度

本節不具規範性。

媒體層疊的粒度等級按照EPUB製作者如何對EPUB內容文件做出標記，以及在text元素中的src屬性和seq元素中的epub:textref屬性使用何種類型的斷片識別碼。例如，當參照[html]元素時，如果標記最細的等級位於段落等級，那就是媒體層疊同步最細的可能等級。同樣的，如果具備子段落標記，像是透過[html]span元素來代表單字或者句子，那在媒體層疊中就可以提供更細的粒度。更細的粒度讓使用者能夠在搜尋文字或者透過文字與單詞導覽時，獲得更精準的結果供同步播放，但會增加媒體層疊文件的檔案大小。斷片識別碼綱要能夠提供更細膩的粒度而不需要仰賴元素，但需要支援才行。

9.3.2.4 文字轉換語音處理

本規格允許在預錄音訊片段之外，使用文字轉換語音（text-to-speech, TTS）─該機制使用合成語音將EPUB出版品中的文字性質內容處理成人工朗讀聲音。

當媒體層疊par元素不具audio元素時，該text元素可能會被閱讀系統透過TTS進行處理。如果文字斷片不適合供TTS處理（例如並非文字元素，以及/或者沒有文字回退），這可能會造成非預期的結果。

註釋
請參照EPUB 3文字轉換語音支援[epub-tts-10]以獲得更多在EPUB出版品中使用TTS技術的資訊。

9.3.3 層疊中的結構語義

為了在媒體層疊文件中表述結構語義，EPUB製作者em class="rfc2119">可以在par、seq、以及body元素中使用epub:type屬性指定。

epub:type屬性協助閱讀系統在處理指定語義類型時做出適當的行為。這些行為的範例如可跳過性與可跳出性以及表格閱讀模式[epub-rs-33]。

媒體層疊文件可以使用可適用的用語相關機制，讓epub:type屬性定義額外的語義。

範例 70: 為一份有著圖片的媒體層疊文件進行語義標記
<smil
    xmlns="http://www.w3.org/ns/SMIL" 
    xmlns:epub="http://www.idpf.org/2007/ops"
    version="3.0">
   <body>
      <seq
          id="id1"
          epub:textref="chapter1.xhtml#figure"
          epub:type="figure">
         <par id="id2">
            <text
                src="chapter1.xhtml#figuretitle"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:24:15.000"
                clipEnd="0:24:18.123"/>
         </par>
         <par id="id3">
            <text
                src="chapter1.xhtml#figurecaption"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:24:18.123"
                clipEnd="0:24:38.530"/>
         </par>
         <par id="id4">
            <text
                src="chapter1.xhtml#figuretext1"/>
            <audio
                src="chapter1_audio.mp3"
                clipBegin="0:24:38.530"
                clipEnd="0:25:00.515"/>
         </par>
      </seq>
   </body>
</smil>
9.3.4 建立樣式資訊關聯

EPUB製作者可以為目前播放的EPUB內容文件元素，在CSS樣式表中使用作者定義的Class來陳述視覺處理資訊。

當使用時，EPUB製作者必須在包裝文件中使用active-class以及playback-active-class特性宣告使用的class名稱。

EPUB製作者必須在每一個其定義的特性中，指定唯一一個CSS Class名稱。每個特性必須定義一個有效的CSS Class名稱，且不包含任何選擇器[css2]。本規格不為這些特性保留所使用的名稱。

EPUB製作者可以為指定的CSS特性定義任何CSS特性，但必須確保與媒體層疊文件相關聯的每一份EPUB內容文件都包含一份（無論嵌入或者連結）包含該Class定義的CSS樣式表。若無法取得這樣的定義，閱讀系統可能提供自行定義的樣式，或者完全沒有樣式。

EPUB製作者不得以連結refines屬性的方式使active-class以及playback-active-class特性，因為這樣會永遠套用到整份EPUB出版品上。

範例 71: 與目前播放的EPUB內容文件建立樣式資訊連結
作者定義的CSS Class名稱在包裝文件中使用後設資料active-class以及 playback-active-class特性進行宣告：

<package …>
   <metadata …>
      …
      <meta
          property="media:active-class">
         my-active-item
      </meta>
      <meta
          property="media:playback-active-class">
         my-document-playing
      </meta>
      …
   </metadata>
   …
</package>
包含使用者定義Class名稱的CSS樣式表：

/* emphasize the active element */
.my-active-item {
    background-color: yellow;
    color: black !important;
}

/* fade out the inactive text */
html.my-document-playing * {
    color: gray;
}
相關的EPUB內容文件的一部分：

<html>
   …
   <body>
      …
      <span id="txt1">
         This is the first phrase.
      </span>
      <span id="txt2">
         This is the second phrase.
      </span>
      <span id="txt3">
         This is the third phrase.
      </span>
      …
   </body>
</html>
在本範例中，閱讀系統會在播放時，套用作者定義的my-active-item class到EPUB內容文件的每一個正在作用的文字元素上。反過來說，閱讀系統會在該元素停止作用時，移除該Class名稱。使用者會看到該元素在播放時，EPUB內容文件中的元素加上黃色背景樣式。

閱讀系統也會在媒體層疊開始時，套用作者定義的my-document-playing class到EPUB內容文件的整份文件元素上。閱讀系統會在播放停止時移除Class名稱。對於XHTML內容文件而言，閱讀系統會套用該Class名稱到html元素[html]上。對SVG內容文件而言，閱讀系統會套用Class名稱到svg元素[svg]上。使用者在媒體層疊播放時，可以看到所有未作用的文字變成灰色。當播放停止時，所有元素的顏色都會回到原來的預設值。

9.3.5 媒體層疊包裝

9.3.5.1 包含媒體層疊

如果一份EPUB內容文件整體或者部分參照了一份媒體層疊文件，其宣告item元素必須指定media-overlay屬性。該屬性必須參照對應媒體層疊文件之宣告item的ID[xml]。

EPUB製作者必須在參照EPUB內容文件的宣告item元素中僅指定media-overlay屬性。

媒體層疊文件的宣告項目其媒體類型必須為application/smil+xml。

範例 72: 一份EPUB內容文件和其相關聯媒體層疊文件在包裝文件宣告中的資料
<package …>
   …
   <manifest>
      <item
          id="ch1" 
          href="chapter1.xhtml" 
          media-type="application/xhtml+xml" 
          media-overlay="ch1_audio"/>
   
      <item
          id="ch1_audio" 
          href="chapter1_audio.smil" 
          media-type="application/smil+xml"/>
      …
   </manifest>
</package>
9.3.5.2 層疊包裝後設資料

EPUB製作者必須在包裝文件中，使用meta元素包含duration特性，來指示整份EPUB出版品的長度。

此外，EPUB製作者必須提供每一份媒體層疊文件的長度。EPUB製作者必須使用refines屬性來讓對應的宣告item建立關聯以宣告長度。

每一份媒體層疊文件的長度加總應該等同於總長度，誤差為加減一秒。

註釋
雖然個別長度的加總可能不會精準對應到整體長度，因為時間會四捨五入到最近的秒數，如果把大於一秒的差距視為不匹配，會造成其他的問題。

EPUB製作者可以在包裝文件中指定narrator的資訊，如作者定義的CSS Class名稱，可套用到目前播放EPUB內容文件的元素上。

註釋
media:字首保留供在包裝後設資料包含這些特性所使用。

範例 73: 包裝文件中的媒體層疊後設資料
<package …>
   <metadata …>
      …
      <meta
          property="media:duration"
          refines="#ch1_audio">
         0:32:29
      </meta>
      
      <meta
          property="media:duration"
          refines="#ch2_audio">
         0:34:02
      </meta>
      
      <meta
          property="media:duration"
          refines="#ch3_audio">
         0:29:49
      </meta>
      
      <meta
          property="media:duration">
         1:36:20
      </meta>
      
      <meta
          property="media:narrator">
         Joe Speaker
      </meta>
      
      <meta
          property="media:active-class">
         my-active-item
      </meta>
      
      <meta
          property="media:playback-active-class">
         my-document-playing
      </meta>
      …
   </metadata>
</package>
9.4 可跳過性與可跳出性

9.4.1 可跳過性（Skippability）

當在閱讀時，使用者可能會希望開啟或關閉內容的特定部分，像是註解、頁碼或其他類型的次要內容。這項功能稱為可跳過性。閱讀系統使用媒體層疊元素epub:type屬性提供的語義資訊來決定何時要提供使用者選項來跳過這些內容。

EPUB製作者可以使用以下語義來啟動可跳過性：

footnote [epub-ssv-11]

endnote [epub-ssv-11]

pagebreak [epub-ssv-11]

然而，本列表並非窮舉。這些術語來自於結構語義用語集[epub-ssv-11]，並且為閱讀系統最有可能提供可跳過性選項的幾項。

範例 74: 有換頁資訊的媒體層疊文件
在本範例中，閱讀系統可以提供使用者選項來開啟及關閉換頁/頁碼提醒，這提醒有時候聽起來很煩。

媒體層疊文件：

<smil
    xmlns="http://www.w3.org/ns/SMIL" 
    xmlns:epub="http://www.idpf.org/2007/ops"
    version="3.0">
   <body>
      <!-- a paragraph -->
      <par id="id1">
         <text
             src="chapter1.xhtml#para1"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0:23:22.000"
             clipEnd="0:24:15.000"/>
      </par>

      <!-- a page number -->
      <par
          id="id2"
          epub:type="pagebreak">
         <text
             src="chapter1.xhtml#pgbreak1"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0:24:15.000"
             clipEnd="0:24:18.123"/>
      </par>

      <!-- another paragraph -->
      <par id="id3">
         <text
             src="chapter1.xhtml#para2"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0:24:18.123"
             clipEnd="0:25:28.530"/>
      </par>
   </body>
</smil>
EPUB內容文件：

<html … >
   …
   <body>
      <p id="para1">
         This is the paragraph before the page break …
      </p>
      
      <span
          id="pgbreak1"
          role="doc-pagebreak"
          aria-label="14"/>
      
      <p id="para2">
         This is the paragraph after the page break …
      </p>
   </body>
</html>
9.4.2 可跳出性（Escapability）

可跳出的項目為巢狀結構，例如表格與列表，這些內容使用者可能會希望能跳出，繼續從巢狀結構後的點讀下去。可跳出性功能不同於可跳過性，不會對於所有項目類型提供啟動或者關閉的選項，而是提供跳出的方式（例如，使用者在決定跳出前，會聽到一部分的內容）。

EPUB製作者可以使用以下語義來啟動可跳出性：

table [epub-ssv-11]

list [epub-ssv-11]

figure [epub-ssv-11]

aside [epub-ssv-11]

然而，本列表並非窮舉。這些術語來自於結構語義用語集[epub-ssv-11]，並且為閱讀系統最有可能提供可跳出性選項的幾項。

註釋
有時可跳出的結構可能包含可跳出的結構。例如，表格由很多行與列與格所構成，使用者可能想分別跳出。閱讀系統對這樣結構跳出的支援變得複雜並且現在可能支援不佳。EPUB製作者應該避免指定巢狀可跳出的結構，除非有更好的支援。

範例 75: 可跳出的結構
在本範例中，供EPUB內容文件使用的媒體層疊文件裡包含了一個段落、一個表格，以及另一個段落。支援可跳出性的閱讀系統可以提供使用者選項來中斷表格的播放並且繼續播放下一個段落。

<smil
    xmlns="http://www.w3.org/ns/SMIL" 
    xmlns:epub="http://www.idpf.org/2007/ops"
    version="3.0">
   <body>
      <!-- a paragraph, part of the regular document text -->
      <par id="id1">
         <text
             src="c01.xhtml#para1"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0:23:22.000"
             clipEnd="0:24:15.000"/>
      </par>

      <!-- a table with two nested rows -->
      <seq
          id="id2"
          epub:textref="c01.xhtml#t1"
          epub:type="table">
         
         <seq
             id="id3"
             epub:textref="c01.xhtml#tr1"
             epub:type="table-row">
            
            <par
                id="id4"
                epub:type="table-cell">
               <text
                   src="c01.xhtml#td1"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:24:15.000"
                   clipEnd="0:24:18.123"/>
            </par>
            
            <par
                id="id5"
                epub:type="table-cell">
               <text
                   src="c01.xhtml#td2"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:24:18.123"
                   clipEnd="0:25:28.530"/>
            </par>
            
            <par
                id="id6"
                epub:type="table-cell">
               <text
                   src="c01.xhtml#td3"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:25:28.530"
                   clipEnd="0:25:45.515"/>
            </par>
         </seq>
         
         <seq
             id="id7"
             epub:textref="c01.xhtml#tr2"
             epub:type="table-row">
            
            <par
                id="id8"
                epub:type="table-cell">
               <text
                   src="c01.xhtml#td4"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:25:45.515"
                   clipEnd="0:26:45.700"/>
            </par>
            
            <par
                id="id9"
                epub:type="table-cell">
               <text
                   src="chapter1.xhtml#td5"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:26:45.700"
                   clipEnd="0:28:02.033"/>
            </par>
            
            <par
                id="id10"
                epub:type="table-cell">
               <text
                   src="chapter1.xhtml#td6"/>
               <audio
                   src="chapter1_audio.mp3"
                   clipBegin="0:28:02.033"
                   clipEnd="0:28:52.207"/>
            </par>
         </seq>
      </seq>

      <!-- another paragraph -->
      <par id="id11">
         <text
             src="c01.xhtml#para2"/>
         <audio
             src="chapter1_audio.mp3"
             clipBegin="0:28:52.207"
             clipEnd="0:30:01.000"/>
      </par>
   </body>
</smil>
9.5 導覽文件中的層疊

本節不具規範性。

由於EPUB導覽文件也是一份XHTML內容文件，EPUB製作者可以使其與媒體層疊文件相關聯。然而，不像傳統的XHTML內容文件，閱讀系統必須在EPUB導覽文件就算不包含在書脊內時，也必須將其呈現給使用者（請見導覽文件處理[epub-rs-33]）。就結果而論，與媒體層疊建立關聯的方法也會按照以下脈絡而在行為上有變化：

當包含在書脊中時，EPUB導覽文件之媒體層疊文件的播放，與其他XHTML內容文件遵循一樣的符合性規定。

當出現在表現的脈絡下，且允許使用者存取並啟動連結時，閱讀系統可以實作額外的表現行為讓使用者存取導覽連結時播放聲音做為回饋。

註釋
指定實作上的細節超過本規格的目標。DAISY媒體層疊播放需求文件為EPUB製作者說明了最佳實踐並且提供給閱讀系統開發者的推薦事項。

10. 可及性

本節不具規範性。

EPUB 3便捷地建構在開放網頁平台，因此能得力於其架構、語義以及延伸一步，利用所基於技術所內含的可及性。

建立無障礙網頁內容的規定與實踐已經被記載於W3C的網頁內容無障礙指引（WCAG）[wcag2]。本指引也提供了定義EPUB出版品可及性的基礎。

目前的WCAG指引（第二版）主要關注於網頁上，另一份獨立的規格，EPUB可及性[epub-a11y-11]定義了如何將該標準應用在EPUB出版品上。其也新增了專屬於EPUB的規定以及後設資料、分頁以及媒體層疊的推薦項目。

本規格推薦EPUB出版品合乎無障礙相關規定，定義在[epub-a11y-11]。遵從這些推薦項目的好處是，可以有助於確保EPUB出版品能符合全世界各司法管轄區中法規上的無障礙規定。

然而，EPUB製作者應該應該將法律規定當作基本，並且將可及性視為全部內容都該遵循的規則。EPUB出版品越能提供無障礙輔助，越能擁有更多潛在的讀者。

註釋
本規格不將可及性規定整合，主要是希望其能獨立於EPUB規格之外並且演進─可及性的實踐經常需要更頻繁地更新。可及性規格也希望能用於過去、現在以及未來的EPUB版本。將規格獨立出來可以確保EPUB的演進不會可及性讓鎖死（也就是讓製作舊版本EPUB的人能參照最新的可及性規定）。

11. 安全與隱私

11.1 概要

本節不具規範性。

EPUB出版品的特質在於其結構。EPUB格式提供了表現、包裝以及將一組有結構並在語義上強化的網頁內容─包括HTML、CSS、SVG、JavaScript以及其他資源─編碼以單一檔案容器配布的手段。

這意味著EPUB 3的安全與隱私問題主要與這些格式的特質相連結，並且近乎要面對所有網頁內容的威脅。

儘管內容上的風險經常等同於創作者有心為惡，但EPUB製作者需要注意到許多出於好意的實踐也可能讓使用者暴露於隱私與安全問題中。本章節剩下的部分將探討EPUB 3的風險模型，以協助EPUB製作者認識並減輕這類危害。

註釋
與閱讀系統相關的風險，請參見[epub-rs-33]中的安全與隱私章節。

11.2 威脅模型

本節不具規範性。

EPUB出版品讓不特定使用者面對各式各樣的隱私與安全威脅。這些威脅很多與網頁內容重疊，但是EPUB也會面對其專屬的攻擊手法，會被用於帶領使用者存取惡意內容，或者用於提供敏感資訊。其中有些較為重要的攻擊維度，EPUB製作者與使用者需要有所知覺，包括：

嵌入遠端資源
EPUB 3允許一些出版品資源源位於遠端託管，特別是那些尺寸上可能會對下載及開啟EPUB出版品造成負面效應的資源（例如聲音、影片以及字型）。雖然以這些方式使用能夠對使用者有益，但這些例外狀況也會被用於將惡意內容注射進出版品中。

此項威脅並不僅限於存取由惡意人士製作的內容。如果EPUB製作者從無法被信任的來源（例如第三方的聲音與影片）嵌入內容，就會一直造成使用者收到被改竄資源的機會。

在配布時檢查惡意軟體或弱點並非隨時都可靠，不像嵌入在EPUB容器中的資源，惡意內容隨時都可以在發布後被置換。

EPUB的源頭對EPUB製作者以及對每一種閱讀系統實作來說都為未知。結論上，如果EPUB製作者在自己控制的網頁伺服器上託管遠端資源，該伺服器實際上不能使用需要制定允許來源的的安全功能，像是供CORS的檔頭、Content-Security-Policy，或者X-Frame-Options。

連結到外部資源
無論是否有意圖，連結到外部網站與資源都會讓使用者面對潛在的漏洞，其可能影響到閱讀系統或者作業系統。儘管外部連結一般會透過網頁瀏覽器開啟，並且作為瀏覽器安全模型的對象，但不能保護使用者免於所有漏洞。

儘管EPUB製作者的意圖並非惡意，但為外部連結添加追蹤資訊也會對使用者隱私造成問題，因為可以在使用者不知道的情形下，允許追蹤使用者的活動。

過期連結騎劫（Broken-link hijacking）─當網域過期並且由另一方購買利用指向的連結─也會引導使用者取得EPUB製作者未預期的資源。

包含惡意內容
嵌入於EPUB容器內的資源不會對惡意人士免疫，尤其是從不受信任的來源取得的EPUB出版品。資源可能包含漏洞或者會傳送敏感資料給非預期第三方的表單。這些人士可能也會使用文件間接技巧試圖取得對遠端資源的存取權，像是符號連結或者檔案捷徑。

使用第三方內容，像是遊戲或者問答，在EPUB製作者無法全面審視內容的狀況下，可能也會引起安全與隱私問題。

允許腳本存取網路
當腳本能存取裝置的網路時，就會提供各種管道危害使用者：

搜集關於使用者以及其行為的資訊，無論是否為惡意；
試圖存取檔案系統以及本機儲存以獲取資訊；
嘗試釣魚（也就是讓一份EPUB內容文件看來像是一個受信任的網站以獲得使用者提交登入訊息）；以及
從外部網站注入惡意內容到EPUB出版品中。
網路存取可以讓第三方內容危害使用者，儘管並非EPUB製作者的意圖。

以數位權利管理強化內容安全
使用數位權利管理綱要對EPUB出版品進行加密及解密可能讓能用於辨識使用者個人的資訊，以及所使用的零售商，以及他們的閱讀偏好傳遞給第三方。

這些攻擊之所以會有效，有時依靠欺騙使用者相信他們所互動的出版品來自可信任的來源。這些欺騙可能會採取以下形式：

偽造出版品資訊
該EPUB出版品可能包含關於自身的錯誤資訊以欺騙使用者相信來自於合法的管道。惡意的EPUB製作者可能，例如，偽造作品的書名、作者、識別碼以及出版社。

儘管這些誤導資訊自身不會造成立即的危害，但也可能引導使用者相信惡意的表格、連結以及其他EPUB出版品內的內容，認為其來自可信賴的來源。

欺騙的平台
惡意EPUB製作者可以設計其內容以模仿或者仿造某個平台的體驗來欺騙使用者相信其內容。

11.2.1 EPUB特有功能

EPUB 3試圖避免對其所基於的技術進行延伸，但還是有一些新的特色。對這些功能之目的進行限制降低他們可能面對的的威脅，然而：

內容切換以及多媒體控制元素僅允許用於隱藏內容以及在HTML中採無腳本方式播放。更進一步，這些特色在EPUB 3.0的第一次發布之發表，但已經進入不再推薦使用的狀態。

在HTML和SVG中表述結構語義僅允許對元素加註。

唯一潛在的例外是epubReadingSystem物件[epub-rs-33]其准許EPUB製作者查詢目前閱讀系統的資訊。EPUB製作者需要注意使用此物件揭露的資訊僅用於提昇對內容的處理（也就是避免使用這些資訊來側寫讀者以及其環境）。

11.3 推薦

儘管EPUB製作者無法避免所有危害使用者的管道，他們也須為內容的安全架構負最終的責任。這意味著他們必須預警來限制EPUB出版品暴露在前章節中所敘述的各種惡意威脅中。

實務上的做法包括：

確保遠端資源使用穩定的連結。
避免第三方資源，尤其是託管在不受EPUB製作者所控制的伺服器上的資源。
避免連結到不受信任的網站（也就是瀏覽器不認為安全的網站）。
使用安全連線連結到外部網站以及資源（也就是使用HTTPS協定）。
不使用腳本在使用者不知情的狀況下透過網路傳送或接收資料。
取得使用者同意使用有隱私考量的網頁API，像是地理位置[geolocation]以及推播通知[push-api]。
避免嵌入並非由聲譽良好的組織或個人提供的內容。
避免使用不再推薦的EPUB功能，因為可能在實作上有尚未發現的臭蟲。
EPUB製作者也需要考量到使用者的隱私權，以及避免刻意搜集資料的狀況。理想上，EPUB製作者不應追蹤使用者，但這並非所有類型出版的現實。

當EPUB製作者必須追蹤使用者時，他們應該在開啟EPUB出版品前，取得使用者的同意來搜集資訊（例如在教育課程作品上）。如果沒辦法做到，他們應該在使用者初次存取EPUB出版品前取得權限。EPUB製作者也應該允許使用者退出追蹤，以及提供使用者管理以及刪除從他們處搜集資料的能力。

EPUB製作者也需要考量不經意地搜集使用者資訊。連結到出版社網站，或者存在其伺服器上的遠端託管資源，都可能導致側寫使用者的結果，特別是在網址內加入獨特追蹤識別碼時。

當在EPUB出版品中搜集並且儲存使用者資訊時（例如透過使用cookies以及網頁儲存[html]），EPUB製作者需要考量到閱讀系統上其他EPUB出版品潛在的資料盜取行為。儘管[epub-rs-33]提出了供EPUB出版品使用的唯一來源規則，其限制了這種攻擊的潛在可能，但還是有風險，如閱讀系統讓EPUB出版品能存取共享的持久性儲存空間（例如，較舊的閱讀系統沒有更新，以及不合規的新的閱讀系統）。結論上，EPUB製作者不應將敏感的使用者資料存在持久性儲存空間。如果EPUB製作者必須儲存敏感資料，應該將資料加密以避免漏洞對其進行細碎的存取。

當出版社及零售商必須使用數位權利管理綱要時，應該採用不會利用或者傳輸使用者及其內容資訊給外部人士進行加密或解密的綱要。

為了最大限度降低安全與隱私風險，EPUB製作者應該在製作其EPUB出版品時，將長期保存當作目標。EPUB出版品以這種方式製作，一般能獨立運作，不仰賴網路連線，並且不使用數位權利管理加密，移除許多可能的攻擊管道。[iso22424]為供EPUB出版品使用的保存格式範例。但可以理解並非所有EPUB製作者都可以做到這種程度的獨立等級，但盡可能地遵從這些實踐，也能增進整體使用者隱私與安全性。

A. 不支援的功能

本規格包含了一些功能，不受到閱讀系統所完整支援，工作小組不再推薦使用，或者僅是為了與EPUB 3閱讀系統維持互通性而保留。本章節定義了這些功能名稱背後的意涵，以及對支援的期盼。

A.1 實作不足的功能

實作不足的功能為早於EPUB 3.3推出的功能，而工作小組尚未能夠建立足夠的實作經驗。

儘管有這些限制，這些功能依然被視為重要而要保留，因為受到EPUB製作者所知悉並且實作（另外，不使用這些功能會使既有的內容變得失效）以及/或者他們被整合到EPUB所基於的內容模型之中。

如果本規格指定一項功能為實作不足，EPUB製作者可以如以下敘述使用這些功能。

註釋
EPUB符合性檢驗工具在EPUB出版品中遇到實作不足的功能時，應該警告EPUB製作者，但是不得把包含這些功能當作違反標準（也就是不視為錯誤或警告）。

警告事項
標準的未來版本，會移除實作不足的標籤或者變成不再推薦，現時點無法做出判斷。EPUB製作者應該慎重考慮現在以及未來使用這些功能可能會引起的互通性問題。

註釋
將功能標記為實作不足為一次性的事件，主要用來處理EPUB被帶進 W3C前使用不同的程序制訂。本標籤將不會用於以 W3C程序制訂的新功能上。

A.2 不再推薦的功能

不再推薦的功能為工作小組於本版本規格中不再推薦使用的功能。不再推薦的功能一般僅受到閱讀系統及/或EPUB出版品有限的支援或者完全沒有支援。

如果本規格指定一項功能為不再推薦，EPUB製作者不應在其EPUB出版品中使用該功能。

註釋
EPUB符合性檢驗工具在EPUB出版品中遇到不再推薦的功能時，應該警告EPUB製作者。

B. 允許使用的外部識別碼

以下表格列出允許用於文件類型宣告[xml]的公用以及系統識別碼。

EPUB製作者 可以將這些外部識別碼使用於具備列表中媒體類型[rfc2046]的出版品資源，在其宣告項目中進行指定（請參見3.9 XML符合性以獲得更多資訊）。

媒體類型（Media Type(s)）	公用識別碼（Public Identifier）	系統識別碼（System Identifier）
application/mathml+xml
application/mathml-presentation+xml
application/mathml-content+xml
-//W3C//DTD MathML 3.0//EN	http://www.w3.org/Math/DTD/mathml3/mathml3.dtd
application/x-dtbncx+xml	-//NISO//DTD ncx 2005-1//EN	http://www.daisy.org/z3986/2005/ncx-2005-1.dtd
image/svg+xml	-//W3C//DTD SVG 1.1//EN	http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd
C. 表述結構語義

C.1 介紹

本節不具規範性。

結構語義對元素所扮演的特殊結構目的增添額外的意義。epub:type屬性用於在EPUB內容文件以及媒體層疊文件中表述特定領域的語義，所攜帶的結構資訊補足了潛在用語。

套用的語義細化了所包含元素的意義，而不會改變其在輔助技術中的性質，但使用類似的role屬性[html]就會產生變化。該屬性不會增強內容的可及性，換句話說；僅提供關於其目的的提示。

語義後設資料強化內容供出版流程以及作者定義的目的使用。也讓閱讀系統能夠對文件的結構與內容有更多理解（例如在媒體層疊中啟動可跳過性與可跳出性）。enable skippability and escapability in media overlays).

本規格定義了使用屬性軸增添結構語義的方法：而不使用添加新元素的做法，EPUB製作者能在既有元素透過epub:type屬性擴充想要的語義。

C.2 epub:type屬性

屬性名稱：
epub:type

命名空間：
http://www.idpf.org/2007/ops

用途：
請參見XHTML、SVG以及媒體層疊的規定。

值：
一份由空白區隔的特性值列表，限制定義於D.1 用語關聯機制。

空白為一組定義在[xml]的字元。

警告事項
雖然epub:type屬性在性質上近似於role屬性;[html]，但這些屬性服務不同的目的。epub:type屬性的值不會增強輔助科技所提供的近用性，像是報讀機，他們也不會對應到這些技術所使用的可及性API。這意味著添加epub:type值到語義中立的元素，像是[html]的div與span不會讓他們對輔助科技來說更具無障礙輔助能力。只有ARIA roles會影響輔助科技，使其更能理解這些元素。

epub:type屬性結果上僅供出版用語義以及增強閱讀系統使用。閱讀系統可以使用epub:type的值來提供可及性增強，像是內建朗讀或者媒體層疊功能，這些功能並不一定要和輔助科技連動。

請參見數位出版WAI-ARIA模組[dpub-aria]以獲得更多關於無障礙出版roles的資訊。

epub:type屬性反映了其所出現的元素之語義。該值為一或多個由空白區隔的用語，基於該文件範圍內所相關連的外部用語集。

epub:type屬性的預設用語集為EPUB 3結構語義用語集epub-ssv-11]。EPUB製作者可以包含該用語集之外，無字首的術語，但建議在添加客製化語義時，透過使用字首的方式來達成。請參見 D.1 用語關聯機制以獲得更多資訊。

範例 76: 識別導言（preamble）
<html
    …
    xmlns:epub="http://www.idpf.org/2007/ops">
   …
   <body>
      …
      <section epub:type="preamble">
         …    
      </section>
      …
   </body>
</html>
範例 77: 識別詞彙表
<html
    …
    xmlns:epub="http://www.idpf.org/2007/ops">
   …
   <body>
      …
      <dl epub:type="glossary">
         …    
      </dl>        
      …
   </body>
</html>
範例 78: 添加換頁語義
<html
    …
    xmlns:epub="http://www.idpf.org/2007/ops">
   …
   <body>
      …
      <p>
         … 
         <span
            epub:type="pagebreak"
            id="p234"
            role="doc-pagebreak"
            aria-label="234"/>
         …
      </p>    
      …
   </body>
</html>
D. 用語集

本附錄定義了一組通用機制，讓本規格中的屬性可以從用語集中參照術語。也定義了專屬於EPUB的用語集供這些屬性使用。

D.1 用語關聯機制

D.1.1 介紹

本節不具規範性。

EPUB定義了一個正規的方式，使用property資料類型來參照定義在後設資料中的術語與特性，以及語義用語集。epub:type屬性在EPUB內容文件以及媒體層疊文件中，使用這種資料類型來添加結構語義，例如在包裝文件中，property以及rel屬性使用該資料類型來定義特性和關係。

property的值像是一個CURIE[rdfa-core]─以精簡的形式表達一個URL[url]。該表述包含了一個字首與參照對象，字首─無論字面上或者隱含─為對應到URL的捷徑，一般可以解析到一個用語集的術語。當閱讀系統轉換該字首到其URL表述並且與參照對象組合時，得到的URL結果一般可以解析到用語集中的斷片，其中包含該術語人類以及/或者機器可讀取的資訊。

為了減低製作上的麻煩，每一個包含property資料類型的屬性也定義了一個預設用語集。術語與特性可由預設用語集參照閱讀系統預先定義對應的URL，但不包含字首。

property資料類型的特色在於容易延伸。若要增添新的術語與特性，EPUB製作者僅需要宣告字首。提供另一項製作上的方便，本規格也保留字首供許多常用的出版用語集（也就是為選擇性宣告）。

以下章節提供了property資料類型與用語關聯機制的額外細節。

D.1.2 The property資料類型

property資料類型為一個簡易的表述方式，包含了URL[url]以及一個選擇性的字首透過一個冒號進行區隔與參照。

(EBNF productions ISO/IEC 14977)
所有終端符號都位於Unicode區塊 'Basic Latin' (U+0000至U+007F)。
property	=	[ prefix , ":" ] , reference;	 
prefix	=	? xsd:NCName ? ;	 
reference	=	? path-relative-scheme-less-URL string [url] ? ;	/* as defined in [url] */
本規格從定義在[rdfa-core]的CURIE資料類型延伸出property資料類型。property代表了CURIEs的子集。

然而與CURIEs有著兩個關鍵差異：

空白的reference不是合規的property值，儘管合乎以上定義（也就是僅包含一個字首以及冒號的property值不合規）。

空白字串不是合規的property，儘管合乎以上定義。

範例 79: 展開一個後設資料property值
在本範例中，property值由字首dcterms與參照的modified所組成。

<meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>
經由[epub-rs-33]處理後，該property會被擴充為以下URL：

http://purl.org/dc/terms/modified
dcterms: 字首為一個保留的字首，對應到URL"http://purl.org/dc/terms/"。

當EPUB製作者在property中沒有提供字首時，會快速地從該屬性的預設用語集中參照所表達的術語。

範例 80: 展開一個宣告property值
在本範例中，一個宣告item元素中指定了mathml特性：

<item … properties="mathml"/>
本特性展開為：

http://idpf.org/epub/vocab/package/item/#mathml
用語集中的字首URL與參照相結合。

D.1.3 預設用語集

預設用語集為EPUB製作者不需要宣告字首即可使用的術語與特性，也具有預期的property值。EPUB製作者不得為預設用語集的術語與特性添加字首。

EPUB製作者不得對使prefix屬性的用語所關聯的URL指定字首。

註釋
請參見採用property資料類型各屬性的定義，以獲得更多關於其預設用語集的資訊。

D.1.4 prefix屬性

prefix屬性定義了用於property值所對應的字首映射。

prefix屬性的值為空白區隔的列表，包含一或多個字首對URL（prefix-to-URL）映射，以此形式：

(EBNF productions ISO/IEC 14977)
所有終端符號都位於Unicode區塊 'Basic Latin' (U+0000至U+007F)。
prefixes	=	mapping , { whitespace, { whitespace } , mapping } ;	 
mapping	=	prefix , ":" , space , { space } , ? xsd:anyURI ? ;	 
prefix	=	? xsd:NCName ? ;	 
space	=	#x20 ;	 
whitespace	=	(#x20 | #x9 | #xD | #xA) ;	 
由於有保留字首的例外EPUB製作者必須在文件內宣告所有使用的字首。EPUB製作者必須僅在個別格式的根元素[xml]指定prefix屬性。

該屬性用於包裝文件時，不具命名空間。

範例 81: 在包裝文件中宣告字首
在本範例中，EPUB製作者宣告了供「朋友的朋友（Friend of a Friend, foaf）與DBPedia（dbp）用語集使用的字首。

<package
    … 
    prefix="foaf: http://xmlns.com/foaf/spec/
            dbp: http://dbpedia.org/ontology/">
   …
</package>
EPUB製作者必須EPUB內容文件以及媒體層疊文件的命名空間http://www.idpf.org/2007/ops中宣告該屬性。

範例 82: 在XHTML內容文件中宣告字首
在本範例中，EPUB製作者宣告了供Z39.98結構語義用語使用的字首

<html …
      xmlns:epub="http://www.idpf.org/2007/ops"
      epub:prefix="z3998: https://www.daisy.org/z3998/2012/vocab/structure/">
   …
</html>
註釋
儘管prefix屬性的模型基於[rdfa-core]中的同名prefix屬性，EPUB製作者不能認爲這些屬性能交互使用。在EPUB內容文件中沒有命名空間的prefix屬性為RDFa屬性。

兩種屬性經常在也指定RDFa表述的EPUB內容文件中同時出現。

<html … prefix="…"
        xmlns:epub="http://www.idpf.org/2007/ops"
        epub:prefix="…">   …
</html>
請注意這是為了嵌入SVG，，字首必須在[html]根html元素中宣告。

為避免衝突，EPUB製作者不得使用prefix屬性宣告已經映射到預設用語集的字首。

EPUB製作者不得宣告字首「_」由於本規格保留該字首供未來與RDFa[rdfa-core]處理之相容性使用。

為了未來包裝文件在替代序列化的相容性，EPUB製作者不得宣告供都柏林核心/elements/1.1/命名空間[dcterms]使用的字首。EPUB製作者必須僅將[dcterms]元素用於包裝文件後設資料中。

D.1.5 保留的字首

警告事項
儘管保留的字首是供製作上便於使用，EPUB製作者應該避免仰賴這字首，以避免產生互通性問題。EPUB符合性檢驗工具經常會拒絕新字首，直到其開發者將工具更新到本規格的最新版本，例如，EPUB製作者應該宣告所有使用的字首以免這樣的問題。

EPUB製作者可以使用保留的字首於屬性中，該屬性有著預期的property值，而不需以prefix屬性宣告。

EPUB製作者不應以prefix屬性複寫保留的字首。

EPUB製作者可以使用的保留的字首依脈絡而定：

包裝文件
EPUB製作者可以在包裝文件屬性中使用以下字首而無需宣告。

字首	URL
a11y	http://www.idpf.org/epub/vocab/package/a11y/#
dcterms	http://purl.org/dc/terms/
marc	http://id.loc.gov/vocabulary/
media	http://www.idpf.org/epub/vocab/overlays/#
onix	http://www.editeur.org/ONIX/book/codelists/current.html#
rendition	http://www.idpf.org/vocab/rendition/#
schema	http://schema.org/
xsd	http://www.w3.org/2001/XMLSchema#
結構語義
EPUB製作者EPUB製作者可以在epub:type屬性中使用以下字首而無需宣告。

字首	URL
msv	http://www.idpf.org/epub/vocab/structure/magazine/#
prism	http://www.prismstandard.org/specifications/3.0/PRISM_CV_Spec_3.0.htm#
D.2 特性欄位定義

用語集定義表格中各欄位有著以下潛在的規則：

允許的值（Allowed Values）
指定使用[xmlschema-2]資料類型需要的類型之值。

適用於（Applies To）
指定何種出版品資源類型EPUB製作者可以指定該特性。

該欄位出現在用於properties屬性中的特性。

基數（Cardinality）
指定EPUB製作者可以在特性中指定的次數，無論用於全域或者附加到另一個元素或特性上。

有最小基數一的特性代表必須要指定一個。

說明（Description）
說明該特性的用途以及指定任何額外EPUB製作者必須跟從的使用限制。

範例（Example）
提供非規範性的使用範例。

延伸（Extends）
指示EPUB製作者可以與哪些特性進行關聯。

本欄位用於定義了主要表述以及次要表述和關係的特性。

名稱（Name）
指定特性的名稱，其必須出現在後設資料中。

D.3 Meta特性用語

本用語集中的特性可用於meta元素的property屬性。

除非另外在其「延伸」欄位中指示，定義在本章節中的特性用於定義次要表述：換句話說，meta元素所乘載定義在本章節中的特性必須有一個refines屬性參照到資源或者要添增的表述上。

參照這些特性的字首URL為http://idpf.org/epub/vocab/package/meta/#。

D.3.1 alternate-script

名稱：	alternate-script
說明：	
alternate-script特性提供了相關聯的特性值，以另外一種語言以及/或者書寫方式的替代表述。alternate-script特性以及其關聯的特性之語言標籤─分別按其表述範圍指定xml:lang屬性─不得相同。


允許的值：	xsd:string
基數：	0或多
延伸：	所有特性。
範例 83: 以英文及日文表述作者姓名
<metadata …>
   …
   <dc:creator id="creator">
      Haruki Murakami
   </dc:creator>
   <meta
       refines="#creator"
       property="alternate-script"
       xml:lang="ja">
      村上春樹
   </meta>
   …
</metadata>
D.3.2 authority

名稱：	authority
說明：	
authority特性用於指出參照元素的值來自和系統或者綱要。
允許的值：	xsd:string
註釋
之前IDPF EPUB 3工作小組維護了一份書籍主題語發行機關的註冊表供本特性使用。本工作小組不再維護該註冊表。

基數：	0或1
延伸：	dc:subject
範例 84: 表達一個BISAC主題標題
<metadata …>
   …
   <dc:subject
      id="subject01">
     FICTION / Occult &amp; Supernatural
   </dc:subject>
   <meta
       refines="#subject01"
       property="authority">
      BISAC
   </meta>
   …
</metadata>
D.3.3 belongs-to-collection

名稱：	belongs-to-collection
說明：	
belongs-to-collection用於識別該EPUB出版品屬於哪一集合（套書）。一本EPUB出版品可以屬於一或多組集合。
也可以利用refines屬性鏈結這些特性，來指示一組集合本身為另一組集合的一部分。

為了讓閱讀系統能夠組織集合，並且避免名稱上的衝突（例如不相關的集合可能共享相同的名稱，或者可能發行不同版本的套書），EPUB製作者應該提供識別碼能夠識別該集合實例的唯一性。必須使用dcterms:identifier特性來乘載該識別碼。

集合可以添加一collection-type特性來更精準地定義其特性。

EPUB出版品在集合中的位置可以透過添加一個group-position特性來提供。

允許的值：	xsd:string
基數：	0或多
延伸：	適用於EPUB出版品並且可以精緻化其他自身的實例。
範例 85: 指示一本出版品屬於一套書
在本範例中，該出版品屬於哈利波特套書。

<metadata>
   …
   <meta
       property="belongs-to-collection"
       id="c02">
      Harry Potter
   </meta>
   <meta
       refines="#c02"
       property="collection-type">
      set
   </meta>
   …
</metadata>
D.3.4 collection-type

名稱：	collection-type
說明：	
collection-type特性用於指示該集合的性質或者形式。
當collection-type的值自一組代碼表或者其他正式的編目時，EPUB製作者應該附加一個scheme屬性來識別其來源。

本規格也定義了以下集合類型，供沒有指定綱要時使用：

series
一系列相關作品可被正式視為一組，一般開放結尾並且可能隨著時間而個別發行。

set
一組完結的作品並且被組合成單一智慧財產單元，一般一併發行並且可以被當作一個單位銷售。

註釋
儘管不要求閱讀系統一定要支援這些值，但指定這些值可以提供選項，來以各種方式把相關EPUB出版品群組化。

允許的值：	xsd:string
基數：	0或1
延伸：	belongs-to-collection
範例 86: 指示一本出版品屬於一套書
在本範例中，出版品屬於The New French Cuisine Masters套書。

<metadata …>
   …
   <meta
       property="belongs-to-collection"
       id="c01">
      The New French Cuisine Masters
   </meta>
   <meta
       refines="#c01"
       property="collection-type">
      series
   </meta>
   …
</metadata>
D.3.5 display-seq

名稱：	display-seq
說明：	
display-seq特性用於指示目前特性與其他相同的後設資料特性在顯示時的順序數字。
本特性僅用於尚未定義排序規則的資料（像是creators的順序基於在文件中出現的順序）。

允許的值：	xsd:unsignedInt
基數：	0或1
延伸：	所有特性。
D.3.6 file-as

名稱：	file-as
說明：	file-as提供相關特性的正規化形式供排序使用。
允許的值：	xsd:string
基數：	0或1
延伸：	所有特性。
範例 87: 表述供排序用的作者名
<metadata …>
   …
   <dc:creator
       id="creator01">
      Lewis Carroll
   </dc:creator>
   <meta
       refines="#creator01"
       property="file-as">
      Carroll, Lewis
   </meta>
   …
</metadata>
D.3.7 group-position

名稱：	group-position
說明：	
group-position特性定義該EPUB出版品與其他位於相同群組作品中的相對順序數字（無論是否全部都是EPUB出版品）。
EPUB製作者可以將group-position特性附加到任何建構群組的後設資料特性，但一般會與belongs-to-collection特性相關聯。

一本EPUB出版品可以屬於多於一個的群組。

允許的值：	單一xsd:unsignedInt或者一系列由小數點區隔的數字（例如1或2.2.1）。
基數：	0或1
延伸：	所有特性。
範例 88: 識別套書中出版品的位置
在本範例中，本出版品為魔戒套書的第二本。

<metadata …>
   …
   <meta property="belongs-to-collection" id="c01">
      The Lord of the Rings
   </meta>
   <meta
       refines="#c01"
       property="collection-type">
      set
   </meta>
   <meta
       refines="#c01"
       property="group-position">
      2
   </meta>
   …
</metadata>
範例 89: 以小數點分隔的值表述位址
在本範例中，在group-position屬性以小數點分隔的值指示該出版品為期刊的98輯第4期。

<metadata …>
   …
   <meta
       property="belongs-to-collection"
       id="cygnus-x-1">
      Physical Review D
   </meta>
   <meta
       refines="#cygnus-x-1"
       property="collection-type">
      series
   </meta>
   <meta
       refines="#cygnus-x-1"
       property="group-position">
      98.4
   </meta>
   …
</metadata>
D.3.8 identifier-type

名稱：	identifier-type
說明：	
identifier-type特性指示identifier的形式或者特性。
當identifier-type的值來自一組代碼表或者其他正式的編目時，EPUB製作者應該附加一個scheme屬性來識別其來源。

允許的值：	xsd:string
基數：	0或1
延伸：	dc:identifier, dc:source
範例 90: 指示識別碼為ISBN
在本範例中，ONIX代碼表5綱要定義了數字值15為ISBN。

<metadata …>
   …
   <dc:identifier
       id="isbn-id">
      urn:isbn:9780101010101
   </dc:identifier>
   <meta
      refines="#isbn-id"
      property="identifier-type"
      scheme="onix:codelist5">
     15
   </meta>
   …
</metadata>
D.3.9 meta-auth （不再推薦）

不再推薦使用該特性。

請參見[epubpublications-30]中對meta-auth特性之定義以獲得更多資訊。

D.3.10 role

名稱：	role
說明：	
role特性說明了creator、contributor或者publisher在創建本EPUB出版品中的角色。
當role值來自一組代碼表或者其他正式的編目時，EPUB製作者應該附加一個scheme屬性來識別其來源。

當為個人或者組織附加多重角色時，角色的重要性應該與包含這些值的meta元素在文件中的順序匹配。（也就是第一個出現的meta元素必須包含最重要的角色）。

允許的值：	xsd:string
基數：	0或多
延伸：	dc:contributor, dc:creator, dc:publisher
範例 91: 細分創作者角色
在本範例中，使用MARC關係者用語集的值來細分作者為該作品的插畫師。

<metadata …>
   …
   <dc:creator
      id="creator01">
     Lewis Carroll
   </dc:creator>
   <meta
       refines="#creator01"
       property="role"
       scheme="marc:relators">
      aut
   </meta>

   <dc:creator
       id="creator02">
      John Tenniel
   </dc:creator>
   <meta
       refines="#creator02"
       property="role"
       scheme="marc:relators">
      ill
   </meta>
   …
</metadata>
範例 92: 指出一位創作者具有多重角色
在本範例中，創作者同時是本作品的作者與插畫師。

<metadata …>
   …
   <dc:creator
       id="creator01">
      Maurice Sendak
   </dc:creator>
   <meta
       refines="#creator01"
       property="role"
       scheme="marc:relators">
      aut
   </meta>
   <meta
       refines="#creator01"
       property="role"
       scheme="marc:relators">
      ill
   </meta>
   …
</metadata>
D.3.11 source-of

名稱：	source-of
說明：	
source-of特性指出一個獨特的面相，為EPUB出版品中所保留的改編來源資源。
本規格定義了值pagination以指示參照的dc:source元素為內容中定義pagebreak特性的來源。

允許的值：	pagination
基數：	0或1
延伸：	dc:source
註釋
請參見[epub-a11y-tech-11]以獲得如何提供無障礙輔助頁面導覽的資訊。
範例 93: 識別出版品的印刷分頁來源
<metadata …>
   …
   <dc:identifier
       id="isbn-id">
      urn:isbn:9780101010101
   </dc:identifier>
   <meta
       refines="#isbn-id"
       property="identifier-type"
       scheme="onix:codelist5">
      15
   </meta>

   <dc:source
       id="src-id">
      urn:isbn:9780375704024
   </dc:source>
   <meta
       refines="#src-id"
       property="identifier-type"
       scheme="onix:codelist5">
      15
   </meta>
   <meta
       refines="#src-id"
       property="source-of">
      pagination
   </meta>
   …
</metadata>
D.3.12 term

名稱：	term
說明：	
term特性提供了一個主題代碼。
允許的值：	xsd:string
基數：	0或1
延伸：	dc:subject
範例 94: 表達一個BISAC主題標題
以下範例呈現一個供主題標題使用的BISAC代碼。

<metadata …>
   …
   <dc:subject
       id="subject01">
      FICTION / Occult &amp; Supernatural
   </dc:subject>
   <meta
       refines="#subject01"
       property="authority">
      BISAC
   </meta>
   <meta
       refines="#subject01"
       property="term">
      FIC024000
   </meta>
   …
</metadata>
D.3.13 title-type

名稱：	title-type
說明：	
title-type指示一個title的特性或者形式。
當title-type值來自一組代碼表或者其他正式的編目時，EPUB製作者應該附加一個scheme屬性來識別其來源。當沒有指定綱要時，閱讀系統應該辨識以下title類型值：main、subtitle、short、collection、edition及expanded。

允許的值：	xsd:string
基數：	0或1
延伸：	dc:title
範例 95: 表述不同的標題類型
<metadata …>
   …
   <dc:title id="t1">
      A Dictionary of Modern English Usage
   </dc:title>
   <meta
       refines="#t1"
       property="title-type">
      main
   </meta>

   <dc:title id="t2">
      First Edition
   </dc:title>
   <meta
       refines="#t2"
       property="title-type">
      edition
   </meta>

   <dc:title id="t3">
      Fowler's
   </dc:title>
   <meta
       refines="#t3"
       property="title-type">
      short
   </meta>
   …
</metadata>
範例 96: 表述複雜標題
本範例呈現如何將標題"The Great Cookbooks of the World: Mon premier guide de cuisson, un Mémoire. The New French Cuisine Masters, Volume Two. Special Anniversary Edition"分類處理。

<metadata …>
   …
   <dc:title
       id="t1"
       xml:lang="fr">
      Mon premier guide de cuisson, un Mémoire
   </dc:title>
   <meta
       refines="#t1"
       property="title-type">
      main
   </meta>
   <meta
       refines="#t1"
       property="display-seq">
      2
   </meta>

   <dc:title id="t2">
      The Great Cookbooks of the World
   </dc:title>
   <meta
       refines="#t2"
       property="title-type">
      collection
   </meta>
   <meta
       refines="#t2"
       property="display-seq">
      1
   </meta>

   <dc:title id="t3">
      The New French Cuisine Masters
   </dc:title>
   <meta
       refines="#t3"
       property="title-type">
      collection
   </meta>
   <meta
       refines="#t3"
       property="display-seq">
      3
   </meta>

   <dc:title id="t4">
      Special Anniversary Edition
   </dc:title>
   <meta
       refines="#t4"
       property="title-type">
      edition
   </meta>
   <meta
       refines="#t4"
       property="display-seq">
      4
   </meta>

   <dc:title id="t5">
      The Great Cookbooks of the World: 
      Mon premier guide de cuisson, un Mémoire. 
      The New French Cuisine Masters, Volume Two. 
      Special Anniversary Edition
   </dc:title>
   <meta
       refines="#t5"
       property="title-type">
      expanded
   </meta>
   …
</metadata>
D.3.14 範例

範例 97: EPUB出版品中常見的精緻化後設資料
<metadata …>

   <dc:identifier id="pub-id">
      urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809
   </dc:identifier>

   <dc:identifier id="isbn-id">
      urn:isbn:9780101010101
   </dc:identifier>
   <meta
       refines="#isbn-id"
       property="identifier-type"
       scheme="onix:codelist5">
      15
   </meta>

   <dc:source id="src-id">
      urn:isbn:9780375704024
   </dc:source>
   <meta
       refines="#src-id"
       property="identifier-type"
       scheme="onix:codelist5">
      15
   </meta>

   <dc:title id="title">
      Norwegian Wood
   </dc:title>
   <meta
       refines="#title"
       property="title-type">
      main
   </meta>

   <dc:language>
      en
   </dc:language>

   <dc:creator
       id="creator">
      Haruki Murakami
   </dc:creator>
   <meta
       refines="#creator"
       property="role"
       scheme="marc:relators"
       id="role">
      aut
   </meta>
   <meta
       refines="#creator"
       property="alternate-script"
       xml:lang="ja">
      村上 春樹
   </meta>
   <meta
       refines="#creator"
       property="file-as">
      Murakami, Haruki
   </meta>

   <meta
       property="dcterms:modified">
      2011-01-01T12:00:00Z
   </meta>

</metadata>
D.4 後設資料連結用語

本用語集中的特性可用於後設資料 link元素的rel以及properties屬性。

參照這些特性的字首URL為http://idpf.org/epub/vocab/package/link/#。

D.4.1 Link關係

以下值可以用於link元素的rel屬性以建立透過href屬性所參照資源間的關係。

D.4.1.1 acquire

名稱：	acquire
說明：	關鍵字acquire用於EPUB預覽以識別何處可以取得EPUB出版品的完整版本。
基數：	0或多
延伸：	僅用於EPUB出版品或者集合。不得在有refines屬性時使用。
範例：	<link rel="acquire" href="http://example.org/book/9781448103706" media-type="text/html"/>
D.4.1.2 alternate

名稱：	alternate
說明：	
關鍵字alternate為HTML供連結使用的alternate關鍵字之子集，其不同之處如下：
不得與其他關鍵字成對並用。
如果在包裝文件後設資料中包含了替代的連結，其指示包裝文件中的替代表現，以在其media-type屬性中所指示的格式提供。
如果在collection元素的後設資料中包含替代的連結，其指示collection中的替代表現，以在其media-type屬性中所指示的格式提供。
閱讀系統不需要為替代連結產生超連結。
基數：	0或多
延伸：	僅適用於EPUB出版品或者集合。不得在有refines屬性時使用。
範例：	<link rel="alternate" href="package.json" media-type="application/json-ld"/>
D.4.1.3 marc21xml-record （不再推薦）

不再推薦使用關鍵字。由media-type 屬性值為「application/marcxml+xml」的關鍵字record所取代。

請參見[epubpublications-30]中的marc21xml-record特性定義以獲得更多資訊。

D.4.1.4 mods-record （不再推薦）

不再推薦使用關鍵mods-record。由media-type屬性值為「application/mods+xml」的關鍵字record所取代。

請參見[epubpublications-30]中的mods-record特性定義以獲得更多資訊。

D.4.1.5 onix-record （不再推薦）

不再推薦使用關鍵字onix-record。由properties屬性值為onix的關鍵字record所取代。

請參見[epubpublications-30]中的onix-record特性定義以獲得更多資訊。

D.4.1.6 record

名稱：	record
說明：	
指示所參照的資源為一份後設資料紀錄。
當指定本關鍵字時，紀錄的媒體類型必須透過media-type屬性進行識別。

請參見EPUB連結後設資料指引，以取得常用連結的後設資料紀錄類型列表。

如果無法從媒體類型識別紀錄類型，可以在properties屬性中指派一個識別碼屬性。

基數：	0或多
延伸：	僅適用於EPUB出版品或者集合。不得在有refines屬性時使用。
範例：	<link rel="record" href="book/52.atom" media-type="application/atom+xml;type=entry;profile=opds-catalog"/>
D.4.1.7 voicing

名稱：	voicing
說明：	
指示參照的音訊檔案提供了資源或者表述的聽覺呈現（一般來說為作者或者書名）透過refines屬性指定。
音訊檔案的媒體類型必須在指定本關鍵字時，使用media-type屬性識別。

基數：	0或多
延伸：	所有特性。當使用本值時，必須使用refines屬性。
範例：	<link refines="#title" rel="voicing" media-type="audio/mpeg" href="title.mp3" />
D.4.1.8 xml-signature （不再推薦）

不再推薦使用關鍵字xml-signature。由其他連結方式所取代。

請參見[epubpublications-30]中的xml-signature特性定義以獲得更多資訊。

D.4.1.9 xmp-record （不再推薦）

不再推薦使用關鍵xmp-record。由properties屬性值為xmp的關鍵字record所取代。

請參見[epubpublications-30]中的xmp-record特性定義以獲得更多資訊。

D.4.2 Link properties

以下值可以用於link元素的properties屬性以建立參照資源所代表的紀錄類型。這些值供紀錄格式所使用而無法透過其媒體類型來識別為獨特。

D.4.2.1 onix

名稱：	onix
說明：	onix特性指示所參照的資源為一份ONIX紀錄[onix]。
範例：	<link rel="record" href="pub/meta/nor-wood-onix.xml" media-type="application/xml" properties="onix"/>
D.4.2.2 xmp

名稱：	xmp
說明：	xmp特性指示所參照的資源為一份XMP紀錄[xmp]。
範例：	<link rel="record" href="pub/meta/nor-wood-xmp.xml" media-type="application/xml" properties="xmp"/>
D.5 包裝處理用語

供參照這些特性使用的字首URL為http://www.idpf.org/vocab/rendition/#。

字首「rendition:」保留供包裝處理特性使用，並且不得在包裝文件中宣告。

註釋
不像本附錄中其他用語集，在包裝處理用語的特性包含特性的組合（在meta元素中表述）以及書脊複寫（透過itemref元素表述）。

使用上的限制也定義在8. 版面處理控制，而不在本附錄中。以下表格提供特性、複寫所定義所在的地圖。

特性	複寫	定義在
rendition:layout	
rendition:layout-pre-paginated
rendition:layout-reflowable
8.2.2.1 版面
rendition:orientation	
rendition:orientation-auto
rendition:orientation-landscape
rendition:orientation-portrait
8.2.2.2 Orientation
頁面方向	
rendition:spread-auto
rendition:spread-both
rendition:spread-landscape
rendition:spread-none
rendition:spread-portrait （不再推薦）
8.2.2.3 同步跨頁
—	
rendition:page-spread-center
rendition:page-spread-left
rendition:page-spread-right
8.2.2.4 跨頁配置
rendition:viewport （不再推薦）	—	8.2.2.5 顯示範圍空間（不再推薦）
rendition:flow	
rendition:flow-paginated
rendition:flow-scrolled-continuous
rendition:flow-scrolled-doc
rendition:flow-auto
8.3.1 rendition:flow特性
—	
rendition:align-x-center
8.3.2 rendition:align-x-center特性
D.5.1 客製化處理特性

閱讀系統開發者可以提供本規格定義之外的功能，以提供閱讀系統對EPUB內容文件的特別處理。

為活用這項實驗性，EPUB製作者可以在不使用rendition:字首的包裝文件中包含客製化特性以及 書脊複寫。

註釋
客製化特性應該僅用於敘述供特定閱讀系統使用的處理特性。本規格應該擴充以提供可讓多個獨立閱讀系統使用的延伸功能。

D.6 Manifest特性用語

本用語集中的特性可以在宣告item元素的properties屬性中使用。

參照這些特性的字首URL為http://idpf.org/epub/vocab/package/item/#。

D.6.1 cover-image

名稱：	cover-image
說明：	cover-image特性指示所描述的出版品資源為EPUB出版品的封面圖片。
適用於：	所有點陣以及向量圖片類型
基數：	0或1
D.6.2 mathml

名稱：	mathml
說明：	mathml特性指示所描述的出版品資源包含一或多個MathML標記實例。
適用於：	EPUB內容文件
基數：	0或多
D.6.3 nav

名稱：	nav
說明：	nav特性指示所描述的出版品資源構成該EPUB出版品的EPUB導覽文件。
適用於：	EPUB導覽文件
基數：	Exactly one
D.6.4 remote-resources

名稱：	remote-resources
說明：	
remote-resources特性指示所描述的出版品資源包含一或多個內部參照指向其他位於EPUB容器外的出版品資源。
請參見3.6 資源位址以獲得更多資訊。

適用於：	所有具備內部參照能力的出版品資源（即為XHTML內容文件、SVG內容文件、CSS樣式表以及媒體層疊文件）。
基數：	0或多
D.6.5 scripted

名稱：	scripted
說明：	scripted特性指示所描述的出版品資源為有腳本的內容文件（也就是包含腳本以及/或[html]form元素）。
適用於：	EPUB內容文件
基數：	0或多
D.6.6 svg

名稱：	svg
說明：	
svg特性指示所描述的出版品資源嵌入一或多個SVG標記實例。
當SVG標記直接包含在資源時，必須要設定這項特性，當SVG從資源參照時（例如，使用[html]img、object或iframe元素），可以設定這項特性。

適用於：	XHTML內容文件；該值包含在SVG內容文件中。
基數：	0或多
D.6.7 switch

名稱：	switch
說明：	
switch特性指示所描述的出版品資源包含一或多個不再推薦的epub:switch元素實例。
適用於：	XHTML內容文件。
基數：	0或多
D.7 Spine特性用語

本用語集中的特性可以在書脊itemref元素的properties屬性中使用。

參照這些特性的字首URL為http://idpf.org/epub/vocab/package/itemref/#。

D.7.1 page-spread-left

名稱：	page-spread-left
說明：	
page-spread-left特性指示相關聯item元素之EPUB內容文件的第一頁需要在兩頁跨頁的左手側呈現。
rendition:page-spread-left特性為本特性的別名。請參見8.2.2.4 跨頁配置以獲得與其用途相關的資訊。

D.7.2 page-spread-right

名稱：	page-spread-right
說明：	
page-spread-right特性指示相關聯item元素之EPUB內容文件的第一頁需要在兩頁跨頁的右手側呈現。
rendition:page-spread-right特性為本特性的別名。請參見8.2.2.4 跨頁配置以獲得與其用途相關的資訊。

D.7.3 範例

範例 98: 識別書脊中的兩頁跨頁
<spine>
<itemref
    idref="title"/>
<itemref
    idref="ps-1-l"
    properties="page-spread-left"/>
<itemref
    idref="ps-1-r"
    properties="page-spread-right"/>
<itemref
    idref="toc"/>
…
</spine>
D.8 媒體層疊用語

本用語集中的特性可以在meta元素的property屬性中使用。

參照這些特性的字首URL為http://www.idpf.org/epub/vocab/overlays/#。

字首「media:」保留供本用語集中的特性使用，並且不得在包裝文件中宣告。

D.8.1 active-class

名稱：	active-class
說明：	EPUB製作者定義的CSS Class名稱，會套用在目前播放的EPUB內容文件元素上。
允許的值：	xsd:string
基數：	0或1
範例：	<meta property="media:active-class">-epub-media-overlay-active</meta>
D.8.2 duration

名稱：	duration
說明：	所有表現或者指定媒體層疊文件的長度。指定的長度為製作時所知道的音訊片段長度，所以排除由外部資源而來的直播串流以及語音合成。
允許的值：	
必須為一個[smil3]時鐘值。
基數：	對整分EPUB出版品以及每一分媒體層疊文件而言為唯一。
範例：	<meta property="media:duration">1:36:20</meta>
D.8.3 narrator

名稱：	narrator
說明：	旁白者的姓名。
允許的值：	xsd:string
基數：	0或多
範例：	<meta property="media:narrator">Joe Speaker</meta>
D.8.4 playback-active-class

名稱：	playback-active-class
說明：	作者定義的CSS Class名稱，在播放啟動時會套用到EPUB內容文件的文件元素上。
允許的值：	xsd:string
基數：	0或1
範例：	<meta property="media:playback-active-class">-epub-media-overlay-playing</meta>
E. 有字首的CSS特性

本附錄描述了EPUB支援的有字首的CSS特性。

註釋
字首定義不再與其對應的CSS同步。在某些狀況下，這些特性無字首的版本現在支援額外的值。閱讀系統可能不再對有字首的特性支援新的語法，所以建議EPUB製作者使用無字首的版本來利用新的特性。
E.1 CSS writing modes



E.1.1 -epub-text-orientation特性

本特性為text-orientation特性[css-writing-modes-3]有字首的版本。

名稱：	-epub-text-orientation
值：	mixed | upright | sideways | sideways-right
為了相容既有的內容，-epub-text-orientation特性也支援不再推薦的關鍵字vertical-right、rotate-right、以及rotate-normal。以下表格指定了使用時所擁有的效果。

不再支援的值	該使用的值
vertical-right	mixed
rotate-right	sideways
rotate-normal	sideways
E.1.2 -epub-writing-mode特性

本特性為writing-mode特性[css-writing-modes-3]有字首的版本，其語法與行為相同。

名稱：	-epub-writing-mode
值：	horizontal-tb | vertical-rl | vertical-lr
E.1.3 -epub-text-combine-horizontal與-epub-text-combine特性

本特性為text-combine-upright特性[css-writing-modes-3]有字首的版本，但不再推薦-epub-text-combine。

名稱：	-epub-text-combine-horizontal
值：	none | all
名稱：	-epub-text-combine （不再推薦）
值：	none | horizontal | horizontal <number>
為了相容既有的內容，-epub-text-combine-horizontal以及-epub-text-combine特性也支援不少不再推薦的關鍵字。以下表格指定了使用時所擁有的效果。

有字首的版本	CSS同等項
-epub-text-combine-horizontal: none	text-combine-upright: none
-epub-text-combine-horizontal: all	text-combine-upright: all
-epub-text-combine: none	text-combine-upright: none
-epub-text-combine: horizontal	text-combine-upright: all
-epub-text-combine: horizontal <number>	no equivalent
E.2 CSS text level 3

本章節描述-epub-字首特性（以及一個有字首的值）以對應[css-text-3]。

E.2.1 -epub-hyphens特性

本特性為hyphens特性[css-text-3]有字首的版本。

名稱：	-epub-hyphens
值：	none | manual | auto | all
為了相容既有的內容，-epub-hyphens特性也支援不再推薦的all關鍵字。該值在CSS中不再支援，目前也沒有對等的項目。

E.2.2 -epub-line-break特性

本特性為line-break特性[css-text-3]有字首的版本。

名稱：	-epub-line-break
值：	auto | loose | normal | strict
E.2.3 -epub-text-align-last特性

本特性為text-align-last特性[css-text-3]有字首的版本。

名稱：	-epub-text-align-last
值：	auto | start | end | left | right | center | justify
E.2.4 -epub-word-break特性

本特性為word-break特性[css-text-3]有字首的版本。

名稱：	-epub-word-break
值：	normal | keep-all | break-all
E.2.5 text-transform特性

本特性為text-transform特性[css-text-3]有字首的版本。 This property is a prefixed value for the property [css-text-3].

名稱：	text-transform
值：	-epub-fullwidth
為了相容既有的內容，text-transform特性也支援不再推薦的-epub-fullwidth關鍵字。當指定時，其擁有與text-transform: full-width相同的效果。

E.3 CSS text decoration level 3

本章節描述-epub-字首特性以對應[css-text-decor-3]。

E.3.1 -epub-text-emphasis-color特性

本特性為text-emphasis-color特性[css-text-decor-3]有字首的版本。

名稱：	-epub-text-emphasis-color
值：	<color>
E.3.2 -epub-text-emphasis-position 特性

本特性為text-emphasis-position特性[css-text-decor-3]有字首的版本。

名稱：	-epub-text-emphasis-position
值：	[ over | under ] && [ right | left ]
E.3.3 -epub-text-emphasis-style特性

text-emphasis-style特性[css-text-decor-3]有字首的版本。
名稱：	-epub-text-emphasis-style
值：	none | [ [ filled | open ] || [ dot | circle | double-circle | triangle | sesame ] ] | <string>
E.3.4 -epub-text-underline-position 特性

本特性為text-underline-position特性[css-text-decor-3]有字首的版本。

名稱：	-epub-text-underline-position
值：	auto | [ under || [ left | right ] ] | alphabetic
為了相容既有的內容，-epub-text-underline-position特性也支援不再推薦的值alphabetic關鍵字。當指定時，其擁有與text-underline-position: auto相同的效果。

F. viewport meta標籤

F.1 介紹

本節不具規範性。

由於Safari HTML定義了viewport meta標籤，所以用於EPUB 3的較早版本，但並非官方認知的標準，本規格定義了基本語法以讓EPUB製作者來表述寬與高空間供處理固定版面文件使用。

本文法中的語法也影響到供viewport meta標籤使用的演算法所影響，其定義在[css-viewport-1]。

本語法意圖盡可能地留白，僅列出一般用語，因為定義所有可能的特性與值並非本規格之目標。僅定義了定義特性與值匹配的基本規定，以及在表述間可能的區隔符。

F.2 語法

對固定版面文件而言，viewport meta標籤[html]必須擁有name與content屬性符合以下定義：

name
name屬性[html]的值在經過空白正規化[xml]後必須為viewport。
content
content屬性[html]的值在經過空白正規化[xml]後必須為以下形式：

(EBNF productions ISO/IEC 14977)
所有終端符號都位於Unicode區塊 'Basic Latin' (U+0000至U+007F)。
viewport	=	property, { sep, property } ;
property	=	name, [ assign, value ] ;
name	=	? character data ? ;
value	=	? character data ? ;
sep	=	sep-char, { sep-char } ;
sep-char	=	( ";" | "," | space ) ;
assign	=	[ space ], "=", [ space ] ;
space	=	#x20 ;
對names以及values特性names and 值的唯一限制為不得包含區隔符號字元或者指派字元。

本章節的製作規定適用於空白正規化[xml]後的結果（也就是在閱讀系統除去開頭與結尾的白空間，並且壓縮屬性中的多個白空間為單一空白後的結果）。EPUB製作者可以在製作的標籤中包含任何合規的ascii空白[infra]，而其結果會合乎本定義。

根據[html]文法，對於meta元素允許使用的任何其他屬性，沒有限制。

註釋
要獲得更多關於指定必要的height與width特性，以及其必須的值，請參照8.2.2.6 內容文件空間。

雖然viewport meta標籤允許EPUB製作者使height與width以外的特性，以及不再這些特性中包含值，但強烈不推薦以這種方式使用。處理固定版面文件時，設定其他的特性可能會造成非預期的結果。

G. 綱要

本節不具規範性。

G.1 包裝文件綱要

供包裝文件使用的綱要可由以下網址取得： https://github.com/w3c/epubcheck/tree/master/src/main/resources/com/adobe/epubcheck/schema/30/package-30.nvdl 。

使用本綱要進行檢驗，需要支援[nvdl]、[relaxng-schema]、[isoschematron]以及[xmlschema-2]的處理器。

註釋
NVDL綱要層可以被multi-pass驗證取代，其使用嵌入RELAX NG以及ISO Schematron綱要。

註釋
這些綱要可能會在本規格正式改版外更新及更正。結論上來說，它們會隨時都可能更動。

G.2 OCF綱要

G.2.1 container.xml用的綱要

供container.xml檔案使用的綱要可由以下網址取得： https://github.com/w3c/epubcheck/tree/master/src/main/resources/com/adobe/epubcheck/schema/30/ocf-container-30.nvdl。

使用本綱要進行檢驗，需要支援[relaxng-schema]以及[xmlschema-2]的處理器。

G.2.2 encryption.xml用的綱要

供encryption.xml檔案使用的綱要包含在[xmlsec-rngschema-20130411]裡。

G.2.3 signatures.xml用的綱要

供signatures.xml檔案使用的綱要包含在[xmlsec-rngschema-20130411]裡。

G.3 媒體層疊綱要

供媒體層疊文件使用的綱要可由以下網址取得： https://github.com/w3c/epubcheck/tree/main/src/master/resources/com/adobe/epubcheck/schema/30/media-overlay-30.nvdl。

使用本綱要進行檢驗，需要支援[nvdl]、[relaxng-schema]、[isoschematron]以及[xmlschema-2]的處理器。

註釋
NVDL綱要層可以被multi-pass驗證取代，其使用嵌入RELAX NG以及ISO Schematron綱要。

H. 完整範例

本節不具規範性。

H.1 資源

分析以下從一份包裝文件以及一份XHTML內容文件摘出的內容：

<package …>
    <metadata …>
        …
        <link rel="record" 
            href="meta/data.xml" 
            media-type="application/marc"/>
        <link rel="record" 
            href="https://www.example.org/meta/data2.xml" 
            media-type="application/marc"/>
        …
    </metadata>
    <manifest>
        …
        <item id="page"
            href="page.xhtml"
            media-type="application/xhtml+xml"/>
        <item id="nav"
            href="nav.xhtml"
            media-type="application/xhtml+xml"
            properties="nav"/>
        <item id="style"        
            href="style.css"
            media-type="text/css"/>
        <item id="font_otf"
            href="fonts/font-file.otf"
            media-type="font/otf"/>
        <item id="font_otf_remote"
            href="https://www.example.org/fonts/font-file2.otf"
            media-type="font/otf"/>
        <item id="font_cff"
            href="fonts/font-file.cff"
            media-type="font/sfnt"/>
        <item id="pls"
            href="speech/cmn.pls"
            media-type="application/pls+xml"/>
        <item id="image_1"
            href="media/image_1.png"
            media-type="image/png"/>
        <item id="image_2"
            href="media/image_2.png"
            media-type="image/png"
            fallback="image_desc"/>
        <item id="image_desc"
            href="image_desc.xhtml"
            media-type="application/xhtml+xml"/>
        <item id="image_3_heic"
            href="media/image_3.heic"
            media-type="image/heic"/>
        <item id="image_3_png"
            href="media/image_3.png"
            media-type="image/png"/>
        <item id="widget"
            href="widget.xhtml"
            media-type="application/xhtml+xml"/>
        …
    </manifest>
    <spine>
        …
        <itemref idref="page_001"/>
        <itemref idref="image_2"/>
        …
    </spine>
</package>
	
<html …>
    <head …>
        …
        <link rel="stylesheet" type="text/css" href="style.css"/>
        <link rel="pronunciation" type="application/pls+xml" href="speech/cmn.pls"/>
        …
    </head>
    <body>
        <img src="media/image1_png"/>
        …
        <a href="media/image_2.png">…</a>
        …
        <picture>
            <source srcset="media/image_3.heic" type="image/heic"/>
            <img src="media/image_3.png"/>
        </picture>
        …        
        <iframe src="widget.xhtml"></iframe>
        …
        <a href="https://www.example.org/some_content">…</a>
    </body>
</html>
EPUB出版品中的各種資源可以按以下方式分類。（請參照3. 出版品資源以獲得關於這些分類的更多資訊。）

meta/data.xml
該資源為一份後設資料紀錄，儲存在EPUB容器中。透過一個包裝文件後設資料中的link元素所連結。所以在宣告層，這是一個連結的資源（也就是未在宣告中表列）。其不屬於其他層。

https://www.example.org/meta/data2.xml
該資源為一份後設資料紀錄，儲存在遠端。透過一個包裝文件後設資料中的link元素所連結。所以在宣告層，這是一個連結的資源（也就是未在宣告中表列）。其不屬於其他層。

page.xhtml
該資源為一份XHTML文件。其列於EPUB書脊中。在宣告層，這是一個出版品資源、一個 容器資源，在書脊層是一份EPUB內容文件，並不出現在內容層。無需回退。

nav.xhtml
該資源為一份EPUB導覽文件。並未列於書脊中。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層或內容層。無需回退。

style.css
該資源為一個CSS檔案。並未列於書脊中，但透過一個[html]link元素參照。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個核心媒體類型資源。無需回退。

font/font-file.otf
該資源為一個TrueType字型檔案。並未列於書脊中，但由一個CSS檔案所參照。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個核心媒體類型資源。無需回退。

https://www.example.org/fonts/font-file2.otf
該資源為一個TrueType字型檔案。並未列於書脊中，但由一個CSS檔案所參照。在宣告層，這是一個出版品資源、一個遠端資源，並不出現在書脊層，在內容層是一個核心媒體類型資源。無需回退。

font/font-file.cff
該資源為一個緊湊字型格式的字型檔案。並未列於書脊中，但由一個CSS檔案所參照。其媒體類型並未列於 核心媒體類型中。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個豁免資源。無需回退。

speech/cmn.pls
該資源為一個發音辭典檔案。並未列於書脊中，但透過一個[html]link元素參照。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個豁免資源。無需回退。

image/image_1.png
該資源為一個PNG圖片檔案。並未列於書脊中，但透過一個[html]img元素參照。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個核心媒體類型資源。無需回退。

image/image_2.png
該資源為一個PNG圖片檔案。透過一個[html]a元素參照。因為其透過一個超連結所參照，其必須被列於書脊中。在宣告層，這是一個出版品資源、一個容器資源，在書脊層這是一份外圍內容文件，在內容層是一個核心媒體類型資源。作為外圍內容文件，回退為必要，其利用宣告回退提供。

image_desc.xhtml
該資源為一份XHTML文件。其為宣告回退的「標的」，所以並非明確地列於書脊（但在需要時他會被既有的書脊項目所「取代」）。在宣告層，這是一個出版品資源、一個容器資源，在書脊層這是一份EPUB內容文件，並不出現在內容層。無需回退。

image/image_3.heic
該資源為一個高效（HEIC）圖片檔案。並未列於書脊中，但透過一個[htmlsource元素參照。其媒體類型並未列於核心媒體類型中。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個外圍資源，回退為必要，其利用[html]picture元素中相鄰的[html]img元素提供。

image/image_3.png
該資源為一個PNG圖片檔案。並未列於書脊中，但透過一個[html]img元素參照，被作為[html] picture元素的固有回退所使用。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，在內容層是一個核心媒體類型資源。無需回退。

widget.xhtml
該資源為一份XHTML文件。並未列於書脊中，但透過一個[html]iframe元素參照。在宣告層，這是一個出版品資源、一個容器資源，並不出現在書脊層，以及，因為其在處理其他EPUB內容文件時被「使用」，在內容層是一個核心媒體類型資源。無需回退。

https://www.example.org/some_content
該資源透過一個[html]a元素所參照，並未儲存在EPUB容器中。閱讀系統可以透過另外的瀏覽器實例來開啟該連結。其並不在本規格定義的任何平面中。

不同類型資源使用狀況的額外範例可在5.6.2.2 範例中找到。

H.2 腳本脈絡

分析以下範例包裝文件：

<package …>
    …
    <manifest>
        …
        <item id="chap01" 
            href="scripted01.xhtml" 
            media-type="application/xhtml+xml"
            properties="scripted"/>
        <item id="inset01" 
            href="scripted02.xhtml" 
            media-type="application/xhtml+xml"
            properties="scripted"/>
        <item id="slideshowjs" 
            href="slideshow.js" 
            media-type="text/javascript"/>
    </manifest>
    
    <spine …>
        <itemref idref="chap01"/>
        …
    </spine>
    …
</package>
以及以下檔案scripted01.xhtml：

<html …>
    <head>
        …
        <script type="text/javascript">
            alert("Reading system name: " + navigator.epubReadingSystem.name);
        </script>
    </head>
    <body>
        …
        <iframe src="scripted02.xhtml" … />
        …
    </body>
</html>
以及以下檔案scripted02.xhtml：

<html …>
    <head>
        …
        <script type="text/javascript" href="slideshow.js"></script>
    </head>
    <body>
        …
    </body>
</html>
這些範本中，以下敘述為真：

在scripted01.xhtml的head中script元素的代碼為書脊層級腳本，因為該文件在書脊中被參照；以及

在scripted02.xhtml的script元素中的代碼為一個容器限制的腳本，因為所在的XHTML文件透過iframe元素包含在scripted01.xhtml中。

H.3 包裝化EPUB

本範例展示使用OCF格式來以一個OCF ZIP容器包含一個簽署以及加密的EPUB出版品。

OCF ZIP容器中檔案的排序列表：

mimetype
META-INF/container.xml
META-INF/signatures.xml
META-INF/encryption.xml
EPUB/As_You_Like_It.opf
EPUB/book.html
EPUB/nav.html
EPUB/images/cover.png
mimetype檔案的內容

application/epub+zip
META-INF/container.xml檔案的內容

<?xml version="1.0"?>
<container
    version="1.0"
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <rootfiles>
      <rootfile
          full-path="EPUB/As_You_Like_It.opf"
          media-type="application/oebps-package+xml"/>
   </rootfiles>
</container>
META-INF/signatures.xml檔案的內容

<signatures
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
   <Signature
       Id="AsYouLikeItSignature"
       xmlns="http://www.w3.org/2000/09/xmldsig#">
        
      <!--
           SignedInfo is the information that is actually signed.
           In this case, the SHA-1 algorithm is used to sign the 
           canonical form of the XML documents enumerated in the
           Object element below.
      -->
      
      <SignedInfo>
         <CanonicalizationMethod
             Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
         <SignatureMethod
             Algorithm="http://www.w3.org/2000/09/xmldsig#dsa-sha1"/>
         <Reference
             URI="#AsYouLikeIt">
            <DigestMethod
                Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue>
               …
            </DigestValue>
         </Reference>
      </SignedInfo>
      
      <!--
           The signed value of the digest above, using the DSA 
           algorithm
      -->
      <SignatureValue>
         …
      </SignatureValue>
      
      <!--
           The key used to validate the signature
      -->
      <KeyInfo>
         <KeyValue>
            <DSAKeyValue>
               <P>…</P>
               <Q>…</Q>
               <G>…</G>
               <Y>…</Y>
            </DSAKeyValue>
         </KeyValue>
      </KeyInfo>
      
      <!--
           The list of resources to sign (note that the canonical
           form of XML documents is signed, while the binary form
           of all other resources is used)
      -->
      <Object>
         <Manifest
             Id="AsYouLikeIt">
            <Reference
                URI="EPUB/As_You_Like_It.opf">
               <Transforms>
                  <Transform
                      Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
               </Transforms>
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>
               </DigestValue>
            </Reference>
            
            <Reference URI="EPUB/book.html">
               <Transforms>
                  <Transform
                      Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
               </Transforms>
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>
               </DigestValue>
            </Reference>
            
            <Reference
                URI="EPUB/images/cover.png">
               <DigestMethod
                   Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
               <DigestValue>
               </DigestValue>
            </Reference>
         </Manifest>
      </Object>
   </Signature>
</signatures>
META-INF/encryption.xml檔案的內容

<?xml version="1.0"?>
<encryption
    xmlns="urn:oasis:names:tc:opendocument:xmlns:container"
    xmlns:enc="http://www.w3.org/2001/04/xmlenc#"
    xmlns:ds="http://www.w3.org/2000/09/xmldsig#">

   <!--
        The RSA-encrypted AES-128 symmetric key used to encrypt
        data enumerated in EncryptedData blocks below
   -->
   <enc:EncryptedKey
       Id="EK">
      <enc:EncryptionMethod
          Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-1_5"/>
      <ds:KeyInfo>
         <ds:KeyName>
            John Smith
         </ds:KeyName>
      </ds:KeyInfo>
      <enc:CipherData>
         <enc:CipherValue>
            xyzabc…
         </enc:CipherValue>
      </enc:CipherData>
   </enc:EncryptedKey>

   <!--
        Each EncryptedData block identifies a single resource
        that has been encrypted using the AES-128 algorithm.
        The data remains stored, in its encrypted form, in the
        original file within the container.
   -->
   <enc:EncryptedData Id="ED1">
      <enc:EncryptionMethod
          Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
      <ds:KeyInfo>
         <ds:RetrievalMethod
             URI="#EK"
             Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
      </ds:KeyInfo>
      <enc:CipherData>
         <enc:CipherReference
             URI="EPUB/book.html"/>
      </enc:CipherData>
   </enc:EncryptedData>

   <enc:EncryptedData Id="ED2">
      <enc:EncryptionMethod
          Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
      <ds:KeyInfo>
         <ds:RetrievalMethod
             URI="#EK" Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
      </ds:KeyInfo>
      <enc:CipherData>
         <enc:CipherReference
             URI="EPUB/images/cover.png"/>
      </enc:CipherData>
   </enc:EncryptedData>
</encryption>
EPUB/As_You_Like_It.opf檔案的內容

<?xml version="1.0"?>
<package
    version="3.0"
    xml:lang="en"
    xmlns="http://www.idpf.org/2007/opf"
    unique-identifier="pub-id">
    
   <metadata
       xmlns:dc="http://purl.org/dc/elements/1.1/">
      
      <dc:identifier
          id="pub-id">
         urn:uuid:B9B412F2-CAAD-4A44-B91F-A375068478A0
      </dc:identifier>
      
      <dc:language>
         en
      </dc:language>
      
      <dc:title>
         As You Like It
      </dc:title>
       
      <dc:creator
          id="creator">
         William Shakespeare
      </dc:creator>
      
      <meta
          property="dcterms:modified">
         2000-03-24T00:00:00Z
      </meta>
      
      <dc:publisher>
         Project Gutenberg
      </dc:publisher>
      
      <dc:date>
         2000-03-24
      </dc:date>
      
      <meta
          property="dcterms:dateCopyrighted">
         9999-01-01
      </meta>
      
      <dc:identifier
          id="isbn13">
         urn:isbn:9780741014559
      </dc:identifier>
      
      <dc:identifier
          id="isbn10">
         0-7410-1455-6
      </dc:identifier>
      
      <link
          rel="xml-signature"
          href="../META-INF/signatures.xml#AsYouLikeItSignature"/>
   </metadata>
    
   <manifest>
      <item id="r4915" 
          href="book.html" 
          media-type="application/xhtml+xml"/>
      <item id="r7184" 
          href="images/cover.png" 
          media-type="image/png"/>
      <item id="nav" 
          href="nav.html" 
          media-type="application/xhtml+xml" 
          properties="nav"/>
   </manifest>
   
   <spine>
      <itemref
          idref="r4915"/>
   </spine>
</package>
H.4 時鐘值

以下為允許使用時鐘值的範例：

5:34:31.396 = 5 小時, 34 分鐘, 31 秒, 以及 396 微秒

124:59:36 = 124 小時, 59 分鐘, 以及 36 秒

0:05:01.2 = 5 分鐘, 1 秒, 以及 200 微秒

0:00:04 = 4 秒

09:58 = 9 分鐘 以及 58 秒

00:56.78 = 56 秒 以及 780 微秒

76.2s = 76.2 秒 = 76 秒 以及 200 微秒

7.75h = 7.75 小時 = 7 小時 以及 45 分鐘

13min = 13 分鐘

2345ms = 2345 微秒

12.345 = 12 秒 以及 345 微秒

I. 媒體類型註冊

I.1 application/oebps-package+xml媒體類型

本附錄註冊了媒體類型application/oebps-package+xml供EPUB包裝文件使用。本註冊取代了RFC4839（請見https://www.rfc-editor.org/rfc/rfc4839）。

包裝文件為一個XML檔案其描述了一本EPUB出版品。用於識別EPUB出版品中的資源，以及提供後設資料資訊。包裝文件以及其相關規格由World Wide Web Consortium（W3C）所維護以及定義。

MIME媒體類型名稱：
application

MIME子類型名稱：
oebps-package+xml

必須的參數：
無。

選擇性參數：
無。

編碼考量：
UTF-8時為8位元；UTF-16時為二進位。

包裝文件採XML，可由UTF-8或UTF-16表現。當包裝文件以UTF-8書寫時，該檔案為8位元相容。當由UTF-16書寫時，則必須使用二進位「內容傳輸編碼（content-transfer-encoding）」。請見[rfc7303]以獲得更多細節。

安全性考量：
包裝文件包含形式完整的XML合乎XML 1.0規格。

明確而言，有可能製作製作惡意檔案，例如包含畸形的資料。多數XML解析器可以透過嚴格執行符合性來保護自身免於這樣的攻擊。

所有讀取內容文件的處理器應該嚴格檢查尺寸並且驗證取得的資料有效性。

EPUB 3規格中目前對包裝文件格式內的加密、簽署或者驗證沒有規定。

互通性考量：
無。

已發表規格：
本媒體類型註冊供EPUB包裝文件使用，如EPUB 3規格所描述，位於https://www.w3.org/TR/epub-33/。

EPUB 3規格取代了開放包裝格式2.0.1規格，其位於https://idpf.org/epub/20/spec/OPF_2.0.1_draft.htm，並且也使用application/oepbs-package+xml媒體類型。

使用本媒體類型的應用程式：
本媒體類型廣泛用於EPUB格式電子書的配布。

附加資訊：
魔術號碼：
無

副檔名：
.opf

麥金塔檔案類型代碼：
TEXT

斷片識別碼：
EPUB規格化斷片識別碼為客製化的斷片識別碼，專定義為EPUB出版品使用。其可以用於參照定義供出版品使用之出版品資源中任意內容。該識別碼定義在https://idpf.org/epub/linking/cfi/。

進一步資訊聯絡人的名稱與email：
EPUB 3工作小組 (public-epub-wg@w3.org)

預期用途：
一般

World Wide Web Consortium (W3C)

I.2 application/epub+zip媒體類型

本附錄註冊了媒體類型application/epub+zip供EPUB開放容器格式（OCF）使用。

OCF ZIP容器，或者EPUB容器，檔案為一個基於ZIP封存格式技術的容器（請見https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT）。其用於封裝EPUB出版品。OCF以及其相關規格由World Wide Web Consortium（W3C）所維護以及定義。

MIME媒體類型名稱：
application

MIME子類型名稱：
epub+zip

必須的參數：
無。

選擇性參數：
無。

編碼考量：
OCF ZIP容器檔案為以 application/zip媒體類型編碼的二進位檔案。

安全性考量：
A所有讀取OCF ZIP容器檔案的處理器應該嚴格檢查尺寸並且驗證取得的資料有效性。

此外，由於OCF ZIP容器檔案內可以嵌入各種內容類型application/epub+zip可以用於描述的內容，其面對的安全問題超越這裡所描述。然而，只有在處理器識別以及處理額外內容，或者進一步將內容派交給其他處理器時，才會面對潛在的安全問題。在這些狀況下，安全問題落在本註冊文件所管轄之外。

適用於application/zip的安全考量也可適用於OCF ZIP容器檔案。

互通性考量：
無。

已發表規格：
本媒體類型註冊供EPUB開放容器格式（OCF）使用，如EPUB 3規格所描述，位於https://www.w3.org/TR/epub-33/。

EPUB 3規格同時取代了RFC 4839以及開放容器格式2.0.1規格，其位於https://idpf.org/epub/20/spec/OCF_2.0.1_draft.doc，並且也使用application/epub+zip媒體類型。

使用本媒體類型的應用程式：
本媒體類型廣泛用於EPUB格式電子書的配布。

附加資訊：
魔術號碼：
0: PK 0x03 0x04, 30: mimetype, 38: application/epub+zip

副檔名：
OCF ZIP容器檔案通常使用副檔名.epub以識別。

麥金塔檔案類型代碼：
ZIP

斷片識別碼：
EPUB規格化斷片識別碼為客製化的斷片識別碼，專定義為EPUB出版品使用。其可以用於參照定義供出版品使用之出版品資源中任意內容。該識別碼定義在https://idpf.org/epub/linking/cfi/。

進一步資訊聯絡人的名稱與email：
EPUB 3工作小組 (public-epub-wg@w3.org)

預期用途：
一般

作者/變更控制者：
World Wide Web Consortium (W3C)

J. 索引

J.1 本規格定義的術語

audio
body
codec
collection
Compression
container
container resource
container root URL
content plane
content URL
core media type resource
dc:contributor
dc:creator
dc:date
dc:identifier
dc:language
dc:subject
dc:title
dc:type
dcterms:modified
EncryptedData
EncryptedKey
encryption
EPUB conformance checker
EPUB container
EPUB content document
EPUB creator
EPUB manifest
EPUB navigation document
EPUB publication
EPUB reading system
EPUB spine
epub:type
exempt resource
file name
file path
fixed-layout document
foreign content document
foreign resource
head
item
itemref
link
linked resource
links
manifest
manifest fallback chain
manifest plane
media overlay document
meta
metadata
non-codec
OCF abstract container
OCF ZIP container
package
package document
par
publication resource
remote resource
root directory
rootfile
rootfiles
scripted content document
seq
signatures
smil
spine
spine plane
SVG content document
synthetic spread
text
top-level content document
unique identifier
valid-relative-ocf-URL-with-fragment string
value
viewport
XHTML content document
J.2 參考資料定義的術語

[BCP47]定義以下術語：
well-formed language tag
[BIDI]定義以下術語：
base direction
[CHARMOD-NORM]定義以下術語：
Unicode Canonical Case Fold Normalization Step
[CSS-TEXT-3]定義以下術語：
hyphens property
line-break property
text-align-last property
text-transform property
word-break property
[CSS-TEXT-DECOR-3]定義以下術語：
text-emphasis-color property
text-emphasis-position property
text-emphasis-style property
text-underline-position property
[CSS-WRITING-MODES-3]定義以下術語：
direction property
text-combine-upright property
text-orientation property
unicode-bidi property
writing-mode property
[DOM]定義以下術語：
child text content
[EPUB-A11Y-11]定義以下術語：
EPUB Accessibility
[EPUB-MULTI-REND-11]定義以下術語：
creating multiple renditions
[EPUB-OVERVIEW-33]定義以下術語：
EPUB 3 Overview
Rendering and CSS
[EPUB-RS-33]定義以下術語：
Core media types
EPUB 3 Reading Systems
epubReadingSystem object
fixed-layout documents
Navigation document processing
processes linked records
processing
reading system support requirements for fonts
reflowable documents set to scroll
Scripting
security and privacy section
table reading mode
unique origin requirement
virtual in nature
[EPUB-SSV-11]定義以下術語：
aside
bodymatter
endnote
figure
footnote
list
pagebreak term
table
toc
[EPUB-TTS-10]定義以下術語：
EPUB 3 Text-to-Speech Support
[HTML]定義以下術語：
a element
area element
audio
base element
bdo element
body
canvas element
content attribute (for meta element)
cookies
data blocks
dir attribute (for html-global element)
div element
document base URL
embed element
embedded content
flow content
form element
h1-h6
head
hidden attribute (for html-global element)
href attribute (for a element)
html element
HTML alternate keyword
HTML standard
iframe element
img element
li element
link
media element
meta
metadata content
microdata attributes
name attribute (for meta element)
nav element
object type
ol element
origin
palpable content
phrasing content
picture element
restrictions on SVG
role attribute
rp element
script element
source element
span element
src attribute (for source element)
src attribute (for img element)
srcset attribute (for source element)
srcset attribute (for img element)
top-level browsing context
track element
type attribute (for source element)
vendor-neutral extensions
video element
video
web storage
XML syntax
[INFRA]定義以下術語：
ascii whitespace
concatenation
HTML namespace
list
prepend (for list)
scalar value strings
strip and collapse ascii whitespace
strip leading and trailing ascii whitespace
[INTERNATIONAL-SPECS]定義以下術語：
"Truncating or limiting the length of strings"
[JSON-LD11]定義以下術語：
linked data
[MATHML3]定義以下術語：
Content MathML
Presentation MathML
[RFC2397]定義以下術語：
data: URL scheme
[RFC8089]定義以下術語：
file: URL scheme
[SMIL3]定義以下術語：
clock value
[SVG]定義以下術語：
svg element
title element
[UAAG20]定義以下術語：
Guideline 1.4 - Provide text configuration
[URL]定義以下術語：
absolute-url string
absolute-url-with-fragment string
base
domain
double-dot path segments
path-relative-scheme-less-url string
percent encoded
relative-url string
relative-URL-with-fragment strings
URL
url parser
URL Serializer
url-fragment string
valid URL string
[XML]定義以下術語：
2.12 Language Identification
document type declaration
external entity
external identifier
ID
IDREF
public
root element
section 2.3 of the XML 1.0 specification
system identifiers
whitespace normalization
[XML-NAMES]定義以下術語：
Conformance of Documents
prefixed
[XMLDSIG-CORE]定義以下術語：
Section 6.6.4
[XMLDSIG-CORE1]定義以下術語：
Section 2
[XMLENC-CORE1]定義以下術語：
Section 2.2.1
K. 變更日誌

本節不具規範性。

請注意本變更日誌僅列出自EPUB 3.2以來的顯著變更─這些變更會影響EPUB出版品的符合性或有同等的重要性。

若要取得在改版過程中所有議題的列表，請參考工作小組的議題追蹤器。

K.1 由推薦候選以來的主要變更

29-Nov-2022: 釐清資料URL並非獨特的出版品資源，也不允許用於包裝文件，但是回退規定的對象。請見issue 2485.
29-Nov-2022: 釐清epub:type屬性不允許用於head元素以及XHTML內容文件的後設資料內容中。請見issue 2486.
17-Nov-2022: 更新檔案路徑與名稱以識別其為OCF抽象容器中的scalar值字串，不分大小寫。請見issue 2461.
11-Nov-2022: 新增警示，在導覽文件元素中，閱讀系統不會保留基於HTML元素的處理步驟。請見issue 2477.
02-Nov-2022: 移除對標籤以及變相選擇器補充中不再推薦使用字元的限制，以一般註釋來避免使用這些已經在Unicode標準中不再推薦使用的字元，該列表會隨時間改變。請見issue 2469.
20-Oct-2022: 移除在以UTF-8格式的抽象容器中編碼檔案名稱的限制，因為不可能又在ZIP容器規格範圍內，又為抽象。請見issue 2461.
17-Oct-2022: 增加在檔案路徑與名稱內使用空白的建議事項。請見issue 2458.
15-Oct-2022: 允許在viewport meta標籤定義中使用沒有值的特性。請見pull request 2457.
11-Oct-2022: 新增額外的規定，viewport meta height與width不得被多次宣告。請見issue 2442.
21-Sept-2022: 讓宣告特性字首的規定更明確。請見issue 2438.
19-Sept-2022: 移除epub:type屬性用途定義的小矛盾。請見issue 2434.
14-Sept-2022: 將遺存功能章節合併到包裝文件定義。請見issue 2423.
14-Sept-2022: 釐清包裝文件中的href屬性不得被用於參照其他內容文件元素（也就是得間接地透過其宣告或者書脊資料來參照資源）。請見issue 2420.
14-Sept-2022: 重新建立空白參照以及特性值不合規定，以確保後設資料特性不會僅包含字首。請見issue 2417.
14-Sept-2022: 新增一章節來表達所有主要導覽文件內容的規定。請見issue 2421.
7-Sept-2022: 新增規定上釐清：宣告僅能條列出版品資源。請見issue 2413.
28-Aug-2022: 新增一註釋，關於使用嵌入時序媒體時，媒體層疊text元素的定義。請見issue 2397.
02-Aug-2022: 更新媒體類型註冊，遵從IANA的正式審查意見以更新之前的註冊。請見issue 1398.
28-July-2022: 更明確限制epub:type可以使用在哪些元素上。請見issue 2377.
18-July-2022: 正式定義在固定版面文件中指定初始包含邊界的viewport meta元素。請見issue 2292.
14-July-2022: 釐清SVG title元素中的標記限制使用HTML元素。請見issue 2355.
10-June-2022: 釐清資料區塊豁免於回退規定。請見issue 2331.
07-June-2022: 駁回檔案URL的用途。請見issue 2324.
07-June-2022: 媒體類型註冊章節現在為規範性。請見issue 2313.
07-June-2022: 更新隱私與安全推薦事項，使用規範性語言。請見pull request 2297.
27-May-2022: 新增建議事項，僅能透過https參照遠端資源。請見issue 2263.
20-May-2022: issue 2264.
17-May-2022: 新增術語索引。請見issue 2260.
K.2 由EPUB 3.2以來的主要變更

12-Apr-2022: 新增註釋，關於從巢狀可跳出結構中跳出的複雜性，以及更新可供跳出的語義列表以符合指引。請見issue 2221.
6-Apr-2022: 移除對authority特性之值的限制，並且新增註釋參照舊的IDPF註冊表。請見issue 2200.
31-Mar-2022: 移除對不再推薦MathML功能的限制，以及新增一般性警告任何技術都會變化並且造成EPUB出版品不合規定。請見issue 2118.
31-Mar-2022: 重新構成客製化屬性為內容製作上的功能，並且新增一章節說明客製化處理特性。請見issue 2134.
25-Mar-2022: 修復陳述上的衝突，關於媒體層疊文件中的語義規定以及釐清可跳過性與可跳出性的規定。請見issue 2066.
22-Mar-2022: 移除推薦事項，閱讀系統辨識內建的collection-type值，並且以註釋取代，關於如何增進對相關內容的處理。請見issue 2071.
21-Mar-2022: 新增對個別媒體覆蓋文件加總對應總長度一秒的誤差。請見issue 2093.
17-Mar-2022: 不再推薦創建新的集合類型。請見issue 2060.
17-Mar-2022: 移除使用epub:type取代對等ARIA roles之有日期的規定。請見issue 2070.
16-Mar-2022: 新增EPUB符合性檢驗工具對符合性檢查與定義的章節。請見pull request 2025.
14-Mar-2022: 更改術語名稱「valid-relative-container-URL-with-fragment」為「valid-relative-ocf-URL-with-fragment string」。請見issue 2076.
09-Mar-2022: 恢復對「valid-relative-container-URL-with-fragment」字串的規定，以在OCF抽象容器中解析到資源。請見issue 2024.
09-Mar-2022: 新增NCX doctype以允許外部識別碼。請見issue 2045.
08-Mar-2022: 要求使用本規格定義的固定版面特性值。請見issue 2039.
08-Mar-2022: 釐清refines屬性不得用於宣告全域固定版面特性。請見issue 2036.
07-Mar-2022: 整合對宣告特性的用途規定到新的資源特性章節。請見issue 2030.
05-Mar-2022: 不允許在精緻化鏈中循環參照或者參照自身。請見issue 2031.
19-Feb-2022: 釐清audio元素的定義並且作為選擇性，且描述在該元素不存在時，可使用本規格的text取代的狀況。請見issue 1986.
04-Feb-2022: 擴充安全與隱私章節以包含新章節說明EPUB出版品的威脅模型，以及額外的推薦事項以確保安全與隱私。請見issue 1871, issue 1872, issue 1875 and issue 1876.
21-Jan-2022: 術語「風險」用於不支援功能的分類，改名為「實作不足」。請見工作小組決議。
08-Dec-2021: page-spread-center特性現在為spread-none的別名。請見issue 1929.
03-Dec-2021: 新增一個新的風險分類供不支援的功能。請見issue 1944.
03-Dec-2021: 移除遠端資源基於元素的限制。請見issue 1913.
01-Dec-2021: 不再推薦使用page-spread-center。目前為spread-none的別名。請見issue 1929.
26-Nov-2021: 在本規格內加入偵測外於容器URL的規定與演算法。請見issue 1912.
18-Nov-2021: 變更僅不允許在標籤以及變相選擇器補充中使用不再推薦的字元。請見issue 1885.
12-Nov-2021: 變更推薦事項，將使用SHA-1加密模糊化密鑰作為規定。請見issue 1873.
12-Nov-2021: 限制模糊化演算法僅能用於字型，並且添加警告建議能用就用更好的保護手段。請見issue 1873.
12-Nov-2021: 移除對rights.xml的描述，保留為未來DRM資訊的標準化使用。請見issue 1874.
10-Nov-2021: 調整對內容URL以及處理相對URL的定義。請見issue 1374 and issue 1888
29-Oct-2021: 推薦EPUB製作者不要使用「絕對-路徑-位址（path-absolute-URL）」字串來參照資源，因為沒有穩定的根目錄。請見issue 1681.
18-Oct-2021: 釐清遠端資源可能被參照的脈絡。請見issue 1857.
12-Oct-2021: 結構語義用語集被移到獨立的工作小組備忘。請見issue 1763.
27-Aug-2021: 新增包含地標的釐清，像是限制數量，推薦已知的語義，以及確保標籤為人類可讀。也新增推薦事項不要包含巢狀列表以符合頁面列表。請見issue 1761.
22-July-2021: 釐清在媒體層疊中TTS對圖片的處理。請見issue 1745.
09-July-2021: 回復客製化屬性章節，因為有已知的使用狀態，但沒有參照的屬性註冊表。請見issue 1602.
09-July-2021: 新增「與URL的關係」章節以解釋在本文件中使用URL標準術語，相對於不參照的資源格式。請見issue 1726.
05-July-2021: 移除XHTML限制中使用私用區字元的章節。實際問題比描述還複雜並且並非EPUB定義的目的。請見issue 1732.
28-June-2021: 新增註釋以避免EPUB製作者參照外於包含包裝文件之資料夾外的資源，以避免互通性問題。請見issue 1687
23-June-2021: 新增base元素到不鼓勵使用XHTML架構的列表中。請見issue 1699.
18-June-2021: 移動製作SSML、PLS辭典以及CSS 3 Speech的規定到EPUB文字轉換語音增強機制備忘。在EPUB 3出版品中使用者些技術的能力依然不變。請見issue 1690.
16-June-2021: 有file綱要的絕對URL不應被用於宣告項目。請見issue 1688.
31-May-2021: 對檔案名稱獨特性匹配時要求使用Unicode正規化與全大寫轉換（按此順序）。請見issue 1631以及pull request 1648.
31-May-2021: 確認SVG內容文件不必要合乎SVG規格，僅需要符合目前參照的形式完整性以及ID需求，以及本規格附加的限制。請見issue 1323.
12-May-2021: 釐清宣告項目不得包含斷片識別碼。請見issue 1303.
12-May-2021: 將所有對URIs/IRIs的參照改為URLs，並且將對RFCs 3986以及3987的參照改為URL標準。請見issue 808.
08-May-2021: 新增釐清文字，link元素可以被用於連結其他替代格式的獨立後設資料特性。請見issue 1666.
06-May-2021: 加上備註，工作小組不再維護出版品類型與集合角色的註冊表，並且移除對後者的依賴，用於驗證集合類型（依然限制使用NMToken值以展延規格）。權威代碼的註冊表現在與特性定義整合。請見pull request 1664.
06-May-2021: 新application/ecmascript作為腳本使用的核心媒體類型。請見issue 1353.
06-May-2021: 新增章節說明媒體層疊使用的斷片識別碼，現在推薦使用參照HTML標的元素以及SVG斷片識別碼，取代要求合乎不相容的XPointer縮寫語法。請見issue 1586.
28-Apr-2021: 捨棄對參照資源的規定，從HTML link元素改到需有核心媒體類型回退。請見issue 1312.
22-Apr-2021: 變更將UTF-16用於CSS與XML的用途，UTF-8為推薦編碼。請見issue 1628.
19-Apr-2021: 不再支援於EPUB內容文件中使用客製化屬性。請見issue 1602.
13-Apr-2021: 在OCF中必要的路徑名稱也該為UTF-8編碼。請見issue 1630.
12-Apr-2021: 在6.3.1.2 CSS規定中新增對SVG direction屬性的參照。請見issue 1614.
09-Apr-2021: 新增一章節專為EPUB出版品可及性。
04-May-2021: 移除對SVG requiredExtensions屬性的規定。請見issue 1087.
26-Mar-2021: 移除對頁面列表順序的規定，以反映內容中換頁的順序。請見issue 1500.
26-Mar-2021: 允許dc:creator與dc:contributor元素擁有多個roles以及允許將roles用於publisher。請見issue 1129 and issue 1583
23-Mar-2021: 釐清在EPUB出版品中使用資料URL的規定。請見issue 1564.
17-Mar-2021: 將補充平面末的非字母列於禁止用於檔案名稱的字元列表中。請見issue 1538.
15-Mar-2021: 移除XML綱要的規範性依存，並且新增供container.xml、encryption.xml及signatures.xml檔案使用的元素與屬性定義。所有綱要都該被視為非規範性。請見issue 1566.
10-Mar-2021: 規定EPUB出版品參照的資源不能位於META-INF資料夾。請見issue 1205.
08-Mar-2021: 修改20-Jan-2021的issue 1322，其中提到EPUB內容文件有長度，正確應為媒體層疊文件。
08-Mar-2021: 新增推薦項目，refines使用斷片識別碼來參照出版品資源。請見issue 1361.
08-Mar-2021: 變更對媒體層疊文件par以及seq順序需要符合預設閱讀順序做為指引的規定。請見issue 1458
05-Mar-2021: 釐清在metadata元素值中的空白需要以[infra]規格定義來分解。請見issue 1528.
26-Feb-2021: 創建新章節以描述一般性後設資料的值之規定，特別是空白處理。請見issue 1528.
17-Feb-2020: 移除推薦副檔名（會影響到包裝文件、XHTML內容文件、媒體層疊文件）。請見issue 1294.
15-Feb-2021: 釐清nav元素沒有epub:type屬性並非EPUB導覽文件內容模型限制的對象。請見issue 976.
10-Feb-2021: 新增安全與隱私章節的初次發表草稿。
04-Feb-2021: 釐清dc:language元素的值必須為形式完整的語言標籤。請見issue 1325.
02-Feb-2021: 新增dir屬性的auto值以及釐清該屬性的優先權。請見issue 1491以及issue 1494.
02-Feb-2021: 為link元素新增hreflang屬性以識別連結資源使用的語言。請見issue 1488.
20-Jan-2021: 釐清使用者定義的媒體層疊樣式表必須在包裝文件後設資料中宣告。請見issue 1319.
20-Jan-2021: 新增推薦項目，每一份EPUB內容文件中媒體層疊長度的加總必須與EPUB出版品中指定的總長度匹配。請見issue 1322.
20-Jan-2021: 澄清epub:type屬性不能增進出版品的可及性。新增對role屬性以及DPUB-ARIA用語集的指向來供可及性使用。
13-Jan-2021: 對書脊層級腳本採用漸進式增強的規定改為推薦，頂層內容文件在不能使用腳本時依然要能被消費。請見issue 1444.
24-Dec-2020: 本規格不再使用發布識別碼，但為了向後相容性，依然規定要包含一個最後修改日期。請見issue 1440.
16-Dec-2020: 與EPUB出版品「renditions」相關的術語與規定都被簡化，以增進本規格的易讀性（也就是和一般對EPUB出版品概念的理解對齊，通常僅有單一內容文件來做單一處理）。這些變化不會影響到包含多重內容釋義的能力，其完整包含於[epub-multi-rend-11]。請見issue 1436.
14-Nov-2020: 術語「semantic inflection」不再用於描述為元素增添結構語義的程序。該術語在EPUB之外不廣受理解並且非必要地複雜。本規格現在簡化為「表述（expressing）」或者「增添（adding）」結構語義。
09-Nov-2020: toc nav必須與書脊中EPUB內容文件、以及檔案中的元素順序匹配之規定被降低成推薦。請見issue 1283.
06-Nov-2020: 釐清HTML script元素中包含資料區塊並非腳本實例。請見issue 1352.
06-Nov-2020: 新增WebP為圖片核心媒體類型。請見issue 1344.
06-Nov-2020: 一組受限制的外部識別碼現在允許用於出版品資源，然而透過內部DTD子集參照外部實體依然受到限制。請見issue 1338.
12-Oct-2020: 新增OPUS為聲音核心媒體類型，並警告目前仍需檢查對Mac/iOS的支援。請見issue 645.
30-Sept-2020:簡化EPUB核心規格的結構以易於理解和取得資訊。本規格現在整合了製作上的規定，EPUB 3.2規格，包括包裝、內容文件、OCF與媒體層疊規格。另有一份獨立的文件EPUB閱讀系統3.3整合了這些文件對閱讀系統的規定。
L. 致謝

本節不具規範性。

規格，就像藝術，就像人類創作。沒有人對EPUB的貢獻多於Garth Conboy，他參與了規格發展的每一步，從最早1999年的OEB 1.0到現在的EPUB 3.3。若沒有Garth的遠見、知識，以及超常的善良本性，這一切都不會成真。我們將EPUB 3.3版貢獻於對他的紀念，Garth，我們永遠欠你一筆。

以下EPUB 3工作小組的成員對本文件的產製有所貢獻：

Will AWAD (Newgen Knowledgeworks)
Sofia Bautista (Legible Media Inc.)
Laura Brady (Legible Media Inc.)
Leah Brochu (National Network for Equitable Library Service)
Matthew C. Chan (House of Anansi Press)
Yu-Wei Chang (Taiwan Digital Publishing Forum)
Fred Chasen (Scribd)
Juan Corona (Legible Media Inc.)
Dave Cramer (W3C Invited Expert, chair)
Romain Deltour (DAISY Consortium)
Marisa DeMeglio (DAISY Consortium)
Brady Duga (Google LLC)
Reinaldo Ferraz (NIC.br - Brazilian Network Information Center)
John Foliot (W3C Invited Expert)
Teenya Franklin (Pearson plc)
Hadrien Gardeur (EDRLab)
Matt Garrish (DAISY Consortium)
Jen Goulden (Crawford Technologies)
Ivan Herman (W3C, staff contact)
Tetsu Hoshino (Kodansha, Publishers, Ltd.)
Norikazu Ishizu (Kadokawa Corporation)
Norihito IYENAGA (Kodansha, Publishers, Ltd.)
Rick Johnson (VitalSource Technologies)
Ken Jones (Circular Software)
Antonio Kamiya (Dentsu Group Inc.)
Deborah Kaplan (W3C Invited Expert)
Bill Kasdorf (Book Industry Study Group)
George Kerscher (DAISY Consortium)
Kazuhito Kidachi (Mitsue-Links Co., Ltd.)
Masakazu Kitahara (Voyager Japan, Inc.)
Toshiaki Koike (Voyager Japan, Inc.)
Ryo Kuroda (ACCESS CO., LTD.)
Charles LaPierre (Benetech)
Dan Lazin (Google LLC)
Laurent Le Meur (EDRLab)
Victoria Lee (Apple, Inc.)
Farrah Little (National Network for Equitable Library Service)
Victor Lopes (Apple, Inc.)
Karan Malhotra (Newgen Knowledgeworks)
Makoto Murata (DAISY Consortium)
Cristina Mussinelli (Fondazione LIA)
Yoichiro Nagao (Kodansha, Publishers, Ltd.)
Theresa O'Connor (Apple, Inc.)
Yoshinori Ohmura (SHUEISHA Inc.)
Rachel Osolen (National Network for Equitable Library Service)
Gregorio Pellegrino (Fondazione LIA)
Vijaya Gowri Perumal (Newgen Knowledgeworks)
Wendy Reid (Rakuten Group, Inc., chair)
John Roque (Apple, Inc.)
Leonard Rosenthol (Adobe)
Shinobu Sato (Kadokawa Corporation)
Ben Schroeter (Pearson plc)
Daihei Shiohama (MEDIA DO Co., Ltd.)
Tzviya Siegman (Wiley)
Avneesh Singh (DAISY Consortium)
MOTOI SUZUKI (SHUEISHA Inc.)
Yutaka Suzuki (Kadokawa Corporation)
Kyrce Swenson (Pearson plc)
Shinya Takami (Kadokawa Corporation, chair)
Mateus Teixeira (W. W. Norton & Company)
Yukio Tomikura (Kodansha, Publishers, Ltd.)
Aimee Ubbink (Crawford Technologies)
Daniel Weck (DAISY Consortium)
Zheng Xu (Gardenia Corp)
Fuqiao Xue (W3C)
Evan Yamanishi (W. W. Norton & Company)
Osamu Yoshiba (Kodansha, Publishers, Ltd.)
Junichi Yoshii (Kodansha, Publishers, Ltd.)
Naomi Yoshizawa (W3C)
Laurence Zaysser (EDRLab)
此外，工作小組想要在此對EPUB 3規格與概要的前任編輯者致特別的感謝：Garth Conboy、Marisa DeMeglio、Elika J. Etemad、Markus Gylling、William McCoy、MURATA Makoto、James Pritchett、Tzviya Siegman、以及Daniel Weck。

M. 參考資料

M.1 參考性資料

[bcp47]
Tags for Identifying Languages. A. Phillips, Ed.; M. Davis, Ed.. IETF. September 2009. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc5646
[bidi]
Unicode Bidirectional Algorithm. Mark Davis; Ken Whistler. Unicode Consortium. 16 August 2022. Unicode Standard Annex #9. URL: https://www.unicode.org/reports/tr9/tr9-46.html
[charmod-norm]
Character Model for the World Wide Web: String Matching. Addison Phillips et al. W3C. 11 August 2021. W3C Working Group Note. URL: https://www.w3.org/TR/charmod-norm/
[css-text-3]
CSS Text Module Level 3. Elika Etemad; Koji Ishii; Florian Rivoal. W3C. 5 May 2022. W3C Candidate Recommendation. URL: https://www.w3.org/TR/css-text-3/
[css-text-decor-3]
CSS Text Decoration Module Level 3. Elika Etemad; Koji Ishii. W3C. 5 May 2022. W3C Candidate Recommendation. URL: https://www.w3.org/TR/css-text-decor-3/
[css-writing-modes-3]
CSS Writing Modes Level 3. Elika Etemad; Koji Ishii. W3C. 10 December 2019. W3C Recommendation. URL: https://www.w3.org/TR/css-writing-modes-3/
[css2]
Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification. Bert Bos; Tantek Çelik; Ian Hickson; Håkon Wium Lie. W3C. 7 June 2011. W3C Recommendation. URL: https://www.w3.org/TR/CSS21/
[csssnapshot]
CSS Snapshot. URL: https://www.w3.org/TR/CSS/
[datetime]
Date and Time Formats. W3C. 27 August 1998. W3C Working Group Note. URL: https://www.w3.org/TR/NOTE-datetime
[dcterms]
DCMI Metadata Terms. DCMI Usage Board. DCMI. 20 January 2020. DCMI Recommendation. URL: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
[dom]
DOM Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://dom.spec.whatwg.org/
[ecmascript]
ECMAScript Language Specification. Ecma International. URL: https://tc39.es/ecma262/multipage/
[epub-a11y-11]
EPUB Accessibility 1.1. Matt Garrish; George Kerscher; Charles LaPierre; Gregorio Pellegrino; Avneesh Singh. W3C. 24 November 2022. W3C Candidate Recommendation. URL: https://www.w3.org/TR/epub-a11y-11/
[epub-rs-33]
EPUB Reading Systems 3.3. Matt Garrish; Ivan Herman; Dave Cramer. W3C. 6 December 2022. W3C Candidate Recommendation. URL: https://www.w3.org/TR/epub-rs-33/
[epub-ssv-11]
EPUB 3 Structural Semantics Vocabulary 1.1. Ivan Herman; Matt Garrish. W3C. 10 August 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-ssv-11/
[epubcontentdocs-301]
EPUB Content Documents 3.0.1. Markus Gylling; William McCoy; Elika J. Etimad; Matt Garrish. IDPF. 26 June 2014. URL: https://idpf.org/epub/301/spec/epub-contentdocs-20140626.html
[epubpackages-32]
EPUB Packages 3.2. Matt Garrish; Dave Cramer. EPUB 3 Community Group. 08 May 2019. URL: https://www.w3.org/publishing/epub32/epub-packages.html
[epubpublications-30]
EPUB Publications 3.0. Markus Gylling; William McCoy; Matt Garrish. IDPF. 11 October 2011. URL: https://idpf.org/epub/30/spec/epub30-publications-20111011.html
[epubpublications-301]
EPUB Publications 3.0.1. Markus Gylling; William McCoy; Matt Garrish. IDPF. 26 June 2014. URL: https://idpf.org/epub/301/spec/epub-publications-20140626.html
[fips-180-4]
FIPS PUB 180-4 Secure Hash Standard. U.S. Department of Commerce/National Institute of Standards and Technology. URL: https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf
[geolocation]
Geolocation API. Marcos Caceres; Reilly Grant. W3C. 1 September 2022. W3C Recommendation. URL: https://www.w3.org/TR/geolocation/
[gif]
Graphics Interchange Format. CompuServe Incorporated. 31 July 1990. URL: https://www.w3.org/Graphics/GIF/spec-gif89a.txt
[html]
HTML Standard. Anne van Kesteren; Domenic Denicola; Ian Hickson; Philip Jägenstedt; Simon Pieters. WHATWG. Living Standard. URL: https://html.spec.whatwg.org/multipage/
[html-rdfa]
HTML+RDFa 1.1 - Second Edition. Manu Sporny. W3C. 17 March 2015. W3C Recommendation. URL: https://www.w3.org/TR/html-rdfa/
[infra]
Infra Standard. Anne van Kesteren; Domenic Denicola. WHATWG. Living Standard. URL: https://infra.spec.whatwg.org/
[iso8601]
Representation of dates and times. ISO 8601:2004.. International Organization for Standardization (ISO). 2004. ISO 8601:2004. URL: http://www.iso.org/iso/catalogue_detail?csnumber=40874
[jpeg]
JPEG File Interchange Format. Eric Hamilton. C-Cube Microsystems. Milpitas, CA, USA. September 1992. URL: https://www.w3.org/Graphics/JPEG/jfif3.pdf
[mathml3]
Mathematical Markup Language (MathML) Version 3.0 2nd Edition. David Carlisle; Patrick D F Ion; Robert R Miner. W3C. 10 April 2014. W3C Recommendation. URL: https://www.w3.org/TR/MathML3/
[mp3]
Information technology — Coding of moving pictures and associated audio for digital storage media at up to about 1,5 Mbit/s — Part 3: Audio. ISO/IEC. August 1993. Published. URL: https://www.iso.org/standard/22412.html
[mp4]
Information technology — Coding of audio-visual objects — Part 14: MP4 file format. ISO/IEC. January 2020. Published. URL: https://www.iso.org/standard/79110.html
[mpeg4-audio]
Information technology — Coding of audio-visual objects — Part 3: Audio. ISO/IEC. December 2019. Published. URL: https://www.iso.org/standard/76383.html
[onix]
ONIX for Books 3.0. URL: https://www.editeur.org/8/ONIX/
[opentype]
OpenType specification. Microsoft. URL: http://www.microsoft.com/typography/otspec/default.htm
[opf-201]
Open Packaging Format 2.0.1. IDPF. 04 September 2010. URL: https://idpf.org/epub/20/spec/OPF_2.0.1_draft.htm
[png]
Portable Network Graphics (PNG) Specification (Second Edition). Tom Lane. W3C. 10 November 2003. W3C Recommendation. URL: https://www.w3.org/TR/PNG/
[push-api]
Push API. Peter Beverloo; Martin Thomson; Marcos Caceres. W3C. 30 June 2022. W3C Working Draft. URL: https://www.w3.org/TR/push-api/
[rdfa-core]
RDFa Core 1.1 - Third Edition. Ben Adida; Mark Birbeck; Shane McCarron; Ivan Herman et al. W3C. 17 March 2015. W3C Recommendation. URL: https://www.w3.org/TR/rdfa-core/
[rfc2046]
Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types. N. Freed; N. Borenstein. IETF. November 1996. Draft Standard. URL: https://www.rfc-editor.org/rfc/rfc2046
[RFC2119]
Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc2119
[rfc2397]
The "data" URL scheme. L. Masinter. IETF. August 1998. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc2397
[rfc4329]
Scripting Media Types. B. Hoehrmann. IETF. April 2006. Informational. URL: https://www.rfc-editor.org/rfc/rfc4329
[rfc7303]
XML Media Types. H. Thompson; C. Lilley. IETF. July 2014. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc7303
[rfc7845]
Ogg Encapsulation for the Opus Audio Codec. T. Terriberry; R. Lee; R. Giles. IETF. April 2016. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc7845
[rfc8089]
The "file" URI Scheme. M. Kerwin. IETF. February 2017. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc8089
[RFC8174]
Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words. B. Leiba. IETF. May 2017. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc8174
[smil3]
Synchronized Multimedia Integration Language (SMIL 3.0). Dick Bulterman. W3C. 1 December 2008. W3C Recommendation. URL: https://www.w3.org/TR/SMIL3/
[svg]
SVG. W3C. URL: https://www.w3.org/TR/SVG/
[truetype]
TrueType™ Reference Manual. Apple, Inc. URL: https://developer.apple.com/fonts/TrueType-Reference-Manual/
[uax15]
Unicode Normalization Forms. Ken Whistler. Unicode Consortium. 17 August 2022. Unicode Standard Annex #15. URL: https://www.unicode.org/reports/tr15/tr15-53.html
[unicode]
The Unicode Standard. Unicode Consortium. URL: https://www.unicode.org/versions/latest/
[url]
URL Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://url.spec.whatwg.org/
[us-ascii]
"Coded Character Set - 7-bit American Standard Code for Information Interchange", ANSI X3.4, 1986..
[wai-aria]
Accessible Rich Internet Applications (WAI-ARIA). W3C. URL: https://www.w3.org/TR/wai-aria/
[webp-container]
WebP Container Specification. URL: https://developers.google.com/speed/webp/docs/riff_container
[webp-lb]
WebP Lossless Bitstream Specification. URL: https://developers.google.com/speed/webp/docs/webp_lossless_bitstream_specification
[woff]
WOFF File Format 1.0. Jonathan Kew; Tal Leming; Erik van Blokland. W3C. 13 December 2012. W3C Recommendation. URL: https://www.w3.org/TR/WOFF/
[woff2]
WOFF File Format 2.0. Vladimir Levantovsky; Raph Levien. W3C. 10 March 2022. W3C Recommendation. URL: https://www.w3.org/TR/WOFF2/
[xinclude]
XML Inclusions (XInclude) Version 1.0 (Second Edition). Jonathan Marsh; David Orchard; Daniel Veillard. W3C. 15 November 2006. W3C Recommendation. URL: https://www.w3.org/TR/xinclude/
[xml]
Extensible Markup Language (XML) 1.0 (Fifth Edition). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/
[xml-names]
Namespaces in XML 1.0 (Third Edition). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/
[xmldsig-core]
XML Signature Syntax and Processing (Second Edition). Donald Eastlake; Joseph Reagle; David Solo; Frederick Hirsch; Thomas Roessler et al. W3C. 10 June 2008. W3C Recommendation. URL: https://www.w3.org/TR/xmldsig-core/
[xmldsig-core1]
XML Signature Syntax and Processing Version 1.1. Donald Eastlake; Joseph Reagle; David Solo; Frederick Hirsch; Magnus Nyström; Thomas Roessler; Kelvin Yiu. W3C. 11 April 2013. W3C Recommendation. URL: https://www.w3.org/TR/xmldsig-core1/
[xmlenc-core1]
XML Encryption Syntax and Processing Version 1.1. Donald Eastlake; Joseph Reagle; Frederick Hirsch; Thomas Roessler. W3C. 11 April 2013. W3C Recommendation. URL: https://www.w3.org/TR/xmlenc-core1/
[xmlenc-decrypt]
Decryption Transform for XML Signature. Merlin Hughes; Takeshi Imamura; Hiroshi Maruyama. W3C. 10 December 2002. W3C Recommendation. URL: https://www.w3.org/TR/xmlenc-decrypt/
[xmlschema-2]
XML Schema Part 2: Datatypes Second Edition. Paul V. Biron; Ashok Malhotra. W3C. 28 October 2004. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema-2/
[xmp]
Extensible metadata platform (XMP) specification -- Part 1. Adobe Systems Incorporated. ISO/IEC. 15 February 2012. URL: http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=57421
[zip]
.ZIP File Format Specification. 15 July 2020. Final. URL: https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT
M.2 規範性資料

[audiobooks]
Audiobooks. Wendy Reid; Matt Garrish. W3C. 10 November 2020. W3C Recommendation. URL: https://www.w3.org/TR/audiobooks/
[css-viewport-1]
CSS Viewport Module Level 1. W3C. URL: https://drafts.csswg.org/css-viewport/
[dpub-aria]
Digital Publishing WAI-ARIA Module. W3C. URL: https://www.w3.org/TR/dpub-aria/
[epub-a11y-tech-11]
EPUB Accessibility Techniques 1.1. Matt Garrish; George Kerscher; Charles LaPierre; Gregorio Pellegrino; Avneesh Singh. W3C. 13 September 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-a11y-tech-11/
[epub-multi-rend-11]
EPUB 3 Multiple-Rendition Publications 1.1. Matt Garrish. W3C. 10 August 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-multi-rend-11/
[epub-overview-33]
EPUB 3 Overview. Matt Garrish; Ivan Herman. W3C. 10 August 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-overview-33/
[epub-tts-10]
EPUB 3 Text-to-Speech Enhancements 1.0. Matt Garrish. W3C. 10 August 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-tts-10/
[fetch]
Fetch Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://fetch.spec.whatwg.org/
[h264]
H.264 : Advanced video coding for generic audiovisual services. 2017-04-13. URL: https://www.itu.int/ITU-T/recommendations/rec.aspx?rec=13189
[international-specs]
Internationalization Best Practices for Spec Developers. Richard Ishida; Addison Phillips. W3C. 23 September 2022. W3C Working Group Note. URL: https://www.w3.org/TR/international-specs/
[iso22424]
ISO/IEC TS 22424-1:2020 — Digital publishing — EPUB3 preservation. 2020-01. URL: https://www.iso.org/standard/73163.html
[isoschematron]
ISO/IEC 19757-3: Rule-based validation — Schematron. 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c040833_ISO_IEC_19757-3_2006(E).zip
[json-ld11]
JSON-LD 1.1. Gregg Kellogg; Pierre-Antoine Champin; Dave Longley. W3C. 16 July 2020. W3C Recommendation. URL: https://www.w3.org/TR/json-ld11/
[mediaqueries-3]
Media Queries Level 3. Florian Rivoal. W3C. 5 April 2022. W3C Recommendation. URL: https://www.w3.org/TR/mediaqueries-3/
[nvdl]
ISO/IEC 19757-4: NVDL (Namespace-based Validation Dispatching Language). 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c038615_ISO_IEC_19757-4_2006(E).zip
[odf]
Open Document Format for Office Applications (OpenDocument) v1.0. 1 May 2005. URL: https://www.oasis-open.org/committees/download.php/12572/OpenDocument-v1.0-os.pdf
[relaxng-schema]
Information technology -- Document Schema Definition Language (DSDL) -- Part 2: Regular-grammar-based validation -- RELAX NG. ISO/IEC. 2008. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip
[rfc3986]
Uniform Resource Identifier (URI): Generic Syntax. T. Berners-Lee; R. Fielding; L. Masinter. IETF. January 2005. Internet Standard. URL: https://www.rfc-editor.org/rfc/rfc3986
[rfc4839]
Media Type Registrations for the Open eBook Publication Structure (OEBPS) Package File (OPF). G. Conboy; J. Rivlin; J. Ferraiolo. IETF. April 2007. Informational. URL: https://www.rfc-editor.org/rfc/rfc4839
[rfc6386]
VP8 Data Format and Decoding Guide. J. Bankoski; J. Koleszar; L. Quillio; J. Salonen; P. Wilkins; Y. Xu. IETF. November 2011. Informational. URL: https://www.rfc-editor.org/rfc/rfc6386
[uaag20]
User Agent Accessibility Guidelines (UAAG) 2.0. James Allan; Greg Lowney; Kimberly Patch; Jeanne F Spellman. W3C. 15 December 2015. W3C Working Group Note. URL: https://www.w3.org/TR/UAAG20/
[uax44]
Unicode Character Database. Ken Whistler. Unicode Consortium. 2 September 2022. Unicode Standard Annex #44. URL: https://www.unicode.org/reports/tr44/tr44-30.html
[wcag2]
Web Content Accessibility Guidelines (WCAG) 2. W3C. URL: https://www.w3.org/TR/WCAG2/
[webvtt]
WebVTT: The Web Video Text Tracks Format. Silvia Pfeiffer. W3C. 4 April 2019. W3C Candidate Recommendation. URL: https://www.w3.org/TR/webvtt1/
[xhr]
XMLHttpRequest Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://xhr.spec.whatwg.org/
[xmlbase]
XML Base (Second Edition). Jonathan Marsh; Richard Tobin. W3C. 28 January 2009. W3C Recommendation. URL: https://www.w3.org/TR/xmlbase/
[xmlsec-rngschema-20130411]
XML Security RELAX NG Schemas. Murata Makoto; Frederick Hirsch. W3C. 11 April 2013. W3C Working Group Note. URL: https://www.w3.org/TR/2013/NOTE-xmlsec-rngschema-20130411/
↑