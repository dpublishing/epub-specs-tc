↑
→
W3C
EPUB 閱讀系統 3.3
W3C編輯草稿 12 January 2023

更多關於此份文件的細節
本版本：
https://w3c.github.io/epub-specs/epub33/rs/
最新發佈版本：
https://www.w3.org/TR/epub-rs-33/
最新編輯草稿：
https://w3c.github.io/epub-specs/epub33/rs/
歷史：
https://www.w3.org/standards/history/epub-rs-33
Commit history
測試套件：
https://w3c.github.io/epub-tests/index.html
實作報告：
https://w3c.github.io/epub-specs/epub33/reports/
編輯者：
Matt Garrish (DAISY Consortium)
Ivan Herman (W3C)
Dave Cramer (Invited Expert)
提出回饋：
GitHub w3c/epub-specs （提交請求, 新主題, 開放主題）
以郵件主旨[epub-rs-33] … 主題資訊 …寄到 public-epub-wg@w3.org(存檔)
Copyright © 1999-2023 World Wide Web Consortium. W3C® liability, trademark and permissive document license rules apply.

摘要

EPUB® 3定義了供數位出版品及文件用於配布及交換的格式。EPUB格式提供表現、包裝，以及將結構化和增強語義的網頁內容──包括HTML、CSS、SVG以及其他資源──進行編碼，以單一檔案容器形式供配布使用的方法。

本規格定義了處理EPUB出版品的使用者代理：EPUB 3閱讀系統之符合性規定。

本文件狀態

本章節描述了本文件在其發表時的狀態。目前W3C出版品及此技術報告的最新改版之列表皆列於W3C技術報告索引，網址為：https://www.w3.org/TR/

本文件由EPUB 3工作小組發布為編輯草稿。

文件在以工作草稿發表階段，不代表受到所有W3C會員所支持。

本文件為草稿，而且可能會隨時會被其他文件更新、取代、淘汰。編輯作業尚未完成前，不適宜引用本文件。

本文件由基於W3C專利政策下運作的一個小組所製作。W3C維護了一份與該小組交付成果有關的任何專利披露公開清單，該頁面也包含了專利披露的說明。任何人若實際擁有某項專利知識並相信其包含該專利之主要申請範圍，則必須依照W3C專利政策第六節之規定揭露該訊息。

本文件受2021年11月2日W3C流程文件所規範。

目次

摘要
本文件狀態
1. 介紹
1.1 概要
1.2 術語
1.3 符合性
1.4 與其他規格之關係
1.4.1 與HTML的關係
1.4.2 與SVG的關係
2. 閱讀系統符合性
2.1 規定
2.2 錯誤處理
2.3 錯誤回報
3. 出版品資源處理
3.1 核心媒體類別
3.2 外圍資源
3.3 資源位址
3.4 資料URLs
3.5 檔案URLs
3.6 XML處理
3.7 國際化
3.8 網路存取
3.9 外部連結
4. 開放容器格式（Open Container Format, OCF）處理
4.1 OCF抽象容器
4.1.1 根目錄的URL
4.1.2 檔案名稱
4.1.3 META-INF目錄
4.2 OCF ZIP容器
4.3 字型模糊化
5. 包裝文件處理
5.1 基礎行文方向
5.2 唯一識別碼
5.3 後設資料
5.4 宣告
5.5 書脊
5.5.1 書脊覆寫
5.6 集合（Collections）
5.7 遺存（Legacy）功能
6. EPUB內容文件處理
6.1 XHTML內容文件
6.1.1 HTML延伸
6.1.1.1 RDFa
6.1.1.2 內容切換（不再推薦）
6.1.1.3 The epub:trigger元素（不再推薦）
6.1.1.4 客製化屬性
6.1.2 HTML歧異與限制
6.1.2.1 Microdata
6.1.2.2 MathML
6.1.2.3 嵌入SVG
6.1.2.3.1 嵌入SVG與CSS
6.1.2.4 表單遞送
6.2 SVG內容文件
6.3 層疊樣式表（CSS）
6.4 腳本
6.4.1 本地儲存
6.4.2 事件模型
6.4.3 安全考量
7. 導覽文件處理
8. 版面排版控制處理
8.1 固定版面文件
8.1.1 固定版面特性
8.1.1.1 rendition:layout特性
8.1.1.2 rendition:orientation特性
8.1.1.3 rendition:spread特性
8.1.1.4 rendition:page-spread-*特性
8.1.2 初始包含塊尺寸
8.1.3 顯示區域處理
8.2 流動內容版面
8.2.1 rendition:flow特性
8.2.2 rendition:align-x-center特性
8.3 viewport meta標籤
8.4 客製化特性
9. 媒體層疊處理
9.1 載入媒體層疊
9.2 基本播放
9.2.1 對時與同步
9.2.2 處理音訊
9.2.3 處理EPUB內容文件元素
9.3 與EPUB內容文件互動
9.3.1 導覽
9.3.2 嵌入影音（不再推薦）
9.3.3 文字轉換語音
9.4 可跳過性與可跳出性
9.4.1 可跳過性（Skippability）
9.4.2 可跳出性(Escapability)
10. 處理結構語義
11. 處理property值
12. 向後相容性
13. 向前相容性
14. 近用性
15. 安全與隱私
15.1 概要
15.2 威脅模型
15.3 推薦事項
A. 不支援的功能
B. epubReadingSystem物件
B.1 介面定義
B.2 描述
B.3 特性
B.4 方法
B.4.1 hasFeature
B.4.1.1 描述
B.4.1.2 功能
C. 索引
C.1 本規格定義的術語
C.2 參考資料定義的術語
D. 變更紀錄
D.1 由推薦候選以來的主要變更
D.2 由EPUB 3.2以來的主要變更
E. 致謝
F. 參考
F.1 規範性參考文件
F.2 參考性參考文件
1. 介紹

1.1 概要

本章節為非規範性。

EPUB 3標準切分為兩項不同的考量：製作EPUB出版品定義在核心規格中[epub-33]，而本規格仔細說明EPUB閱讀系統處理EPUB出版品的規定。

EPUB閱讀系統可採多種形式打造。舉個例子，可能擁有可視顯示區域來將內容排版呈現給讀者，或者只提供內容聲音播放。因此，沒有一套規則可以適用於所有閱讀系統。所以本規格將處理上的規定拆分，供閱讀系統各自所能達到的程度以及支援的規格使用。

此外，本規格提供了開發者大幅彈性來打造獨特的使用者介面，並且意圖將如後設資料處理等事物的規定降到最小限度，來提供這樣的彈性。

所以，儘管本規格提出了供閱讀系統使用的正式規定，但不可能僅靠本文件就能理解其內容。開發者也應該熟悉EPUB出版品的完整內容結構，以對提供的資訊能有完整範圍的理解。

注意事項
合乎規定的閱讀系統不必要為單一專門的程式或者裝置，而可能以配布系統的方式存在。

1.2 術語

本規格使用定義在EPUB 3.3[epub-33]中的術語。

也定義了以下術語：

content display area（內容呈現區域）
顯示範圍（viewport）中的區域，專門用於呈現EPUB內容文件。內容呈現區域排除任何邊框、邊界、頁首、頁腳，或者其他EPUB閱讀系統可能插進顯示範圍中的裝飾。

在同步跨頁的狀況中，顯示範圍包含了兩個內容呈現區域。

注意事項
每一章節中只有術語第一次出現時會連結到其定義。

1.3 符合性

本規格中被標註為非規範性的章節，以及所有製作準則、圖表、範例以及注意事項都為非規範性。本規格其他部分皆為規範性。

關鍵字：可以（MAY）、必須（MUST）、不得（MUST NOT）、選擇性（OPTIONAL）、推薦（RECOMMENDED）、應該（SHOULD）、不應（SHOULD NOT）在本文件中以如上粗體加底線格式出現時， BCP 14[RFC2119][RFC8174]中的敘述解釋。

所有演算法的說明皆為非規範性。

1.4 與其他規格之關係

本章節為非規範性。

1.4.1 與HTML的關係

[html]標準不斷演進──也就是不再有編號版本發佈。該標準持續參照各項不斷演進的技術，例如MathML、SVG、CSS與JavaScript。

閱讀系統開發者必須持續追蹤HTML以及所參照的技術之變革，以確保其系統跟得上時代。

本規格不要求EPUB閱讀系統支援腳本、表單遞送或者HTML DOM[dom]。合乎本規格的閱讀系統僅預期能夠處理合規的EPUB內容文件。支援腳本以及表單遞送並非必須，合規的閱讀系統不一定要是全合規的HTML使用者代理。

1.4.2 與SVG的關係

本規格並不參照特定版本的[svg]，相對之下使用無日期的參照。當所參照的版本產生歧義時，最新的推薦版本為權威性參考文件。

這種作法確保EPUB可以一直跟隨SVG標準演進的腳步前進。然而，閱讀系統開發者必須持續追蹤SVG標準的變化，以確保製作處理跟上時代。

2. 閱讀系統符合性

2.1 規定

無論閱讀系統是否支援在本章開頭提及的功能。為了合乎本規格，閱讀系統必須支援所有規定的功能，以及所有在特定條件下，可使用的功能（例如，如果閱讀系統具有顯示範圍，就要支援圖片處理），分別定義在各章節中。

注意事項
因為閱讀系統並不一定是單一應用程式，而可能存在於配布系統中，所以將EPUB出版品處理呈現給讀者的應用程式，並不一定都能符合閱讀系統規定。例如一個閱讀系統僅用於管控內容容器（像是書店或者圖書館系統）。在這案例中，要是閱讀系統開發者能證明規定不適用於應用程式（像是有著重複itemref項目[epub-33]的EPUB出版品不能進入該系統），該閱讀系統整體依然可被視為合規。
當支援推薦以及選擇性功能時，閱讀系統必須符合所有規範性規定，分別定義在各章節中。

當閱讀系統開發者選擇不支援推薦以及選擇性功能時，並非總是意味著該章節中可適用的規範性規定都不適用。在某些狀況中，當不實作一項功能時，可能會有替代的規定（例如當不支援腳本時，需要處理回退）。閱讀系統必須在不支援功能時，符合這些替代的規定。

注意事項
EPUB出版品經常包含對本規格而言並非必要的資訊（像是包裝文件後設資料）。閱讀系統可以為任何目的使用這些額外的資訊（例如用於改善使用者介面）。

2.2 錯誤處理

閱讀系統在EPUB出版品，或者其中的資訊違反內容製作或者處理規定時，不要求一定要載入。

2.3 錯誤回報

本章節為非規範性。

儘管不要求閱讀系統在解析以及處理EPUB出版品時得回報錯誤（像是推測固定版面文件的尺寸），但強烈鼓勵其可以提供存取這些資訊的手段。可類比的範例為網頁瀏覽器的開發者工具，可供除去HTML網頁以及應用程式的臭蟲使用。

舉個例子，EPUB製作者若能存取這些解析資訊，可以得到極大的助益（像是能有效地除去EPUB出版品中的臭蟲）。為了讓最大限度地除去這些臭蟲，建議閱讀系統不僅回報直接遇到的問題，也可以回報其所使用的應用程式所回報的問題（像是由用於處理內容的瀏覽器核心回報的HTML、CSS以及JavaScript錯誤，或者由EPUBCheck回報的驗證問題）。

不希望回報錯誤時產生突兀的體驗，而影響到使用時的閱讀體驗。因此，舉個例子，回報資訊可以選擇性地由設定選單中開啟，而不會對使用者造成非必要的干擾。

3. 出版品資源處理

閱讀系統必須處理出版品資源[epub-33]。

3.1 核心媒體類別

如果閱讀系統有顯示範圍，其必須支援圖片核心媒體類別資源[epub-33]。

如果閱讀系統有處理預錄音訊的能力，其必須支援聲音核心媒體類別資源[epub-33]。

注意事項
推薦閱讀系統至少支援H.264[h264]與VP8[rfc6386]影片編碼其一，但這並非符合性規定──閱讀系統可以支援任何影片編碼，或者全不支援。閱讀系統開發者在決定支援何種影片格式時，應該考量各項因素，像是是否受到廣泛採用、播放品質以及技術授權費。
3.2 外圍資源

閱讀系統可以支援外圍資源類別的任意組合，以及當不支援一種外圍資源時，必須按照外圍資源[epub-33]中的定義來處理回退。

3.3 資源位址

閱讀系統應該支援遠端資源，如資源位址[epub-33]中的定義。

為了限制網路攻擊造成的風險，閱讀系統應該僅載入透過https URI綱要[rfc7230]所參照的遠端資源。

3.4 資料URLs

閱讀系統必須避免從頂層瀏覽脈絡[html]開啟的資料URL[rfc2397]，除非透過閱讀系統提供的功能，像是脈絡選單所啟動。如果閱讀系統不使用供頂層內容文件的頂層瀏覽脈絡，例如頂層內容文件為SVG，其必須防止將資料URL以頂層內容文件的方式開啟。

3.5 檔案URLs

閱讀系統必須避免存取透過檔案URL[rfc8089]參照的資源。

3.6 XML處理

閱讀系統必須使用非驗證的XML處理器[xml]其：

不讀取外部DTD子集[xml]；
合規於[xml-names]。
3.7 國際化

作為處理出版品資源的一部分，閱讀系統需要處理XHTML內容文件或者SVG內容文件中，設置語言以及基礎行文方向的屬性，以及所有XML文件的xml:lang屬性（像是包裝文件以及媒體層疊文件）。

更進一步，閱讀系統必須處理在包裝文件中處理dir屬性[epub-33]，透過dir指定的基礎行文方向適用於其指定的元素，以及內容中的所有元素，除非使用另外一個dir實例來覆寫（也請見5.1 基礎行文方向以了解更近一步的細節。）

在出版品資源中缺少這項資訊時，閱讀系統不得從包裝文件中表述的資訊來推測語言或者基礎行文方向（也就是透過xml:lang以及dir屬性，link元素中的hreflang屬性，或者從dc:language元素[epub-33]）。參照資源的正式規格以獲得在缺少明確的語言以及行文資訊時該如何處理。

3.8 網路存取

閱讀系統可以支援網路存取，以獲得遠端資源並且允許有腳本的內容文件與位於網頁上的API溝通以取得資源。

然而，提供網路存取會增加對閱讀系統的安全風險，以及對使用者的安全與隱私風險。這些風險經常特定於閱讀系統以及其所運作的平台──大多數閱讀系統建構於其上的瀏覽器核心，其不提供與網頁瀏覽器相同的安全與隱私控制。結果使開發者需要在允許網路存取時，需要格外小心，需要更多徹底的測試其閱讀系統，使其能不受到攻擊。更多關於這些風險的資訊提供在15. 安全與隱私。

如果閱讀系統開發者允許網路存取，推薦以下兩者方式：

通知使用者有網路活動；以及
讓使用者阻斷網路存取（例如關閉閱讀系統全域或者針對特定EPUB出版品的網路存取）。
3.9 外部連結

當一個連結有http或https綱要[url]時，閱讀系統：

應該在開啟連結前取得使用者同意。
應該在新的瀏覽器實例中開啟連結，以確保瀏覽器的安全與隱私控制可供使用者使用。
對於需要輔助應用程式（helper application）才能載入的有綱要連結，閱讀系統應該取得使用者的同意，並且遵從平台指引來開啟輔助應用程式。

注意事項
外部連結不只會在EPUB內容文件中出現。例如，閱讀系統可以提供包裝文件後設資料中，對外部連結記錄[epub-33]的存取。

注意事項
更多關於外部連結的安全與隱私問題資訊，請見15.2 威脅模型。

4. 開放容器格式（Open Container Format, OCF）處理

閱讀系統必須處理EPUB容器[epub-33]。

注意事項
處理EPUB容器的應用程式不需為功能完整的閱讀系統（例如，一個應用程式可能只會解壓縮容器中的內容，或者檢查包裝內容是否合規）。在這些狀況下，應用程式的開發者可以忽略定義在本章節中對閱讀系統的規定。

4.1 OCF抽象容器

4.1.1 根目錄的URL

閱讀系統必須指派一個URL[url]作為OCF抽象容器的根目錄。該URL稱為容器根URL。由實作自行決定作法，但實作上必須有以下特性：

解析a>的結果[url]「/」加上容器根URL為容器根URL的base。
解析的結果[url]「..」加上容器根URL為容器根URL的base。
容器根URL的來源（origin）[url]在閱讀系統中對每一個使用者指定的EPUB出版品實例都為獨特。
注意事項
閱讀系統中每一個使用者指定的EPUB出版品實例之來源[html]獨特性意味著，如果兩個不同使用者取得相同的EPUB出版品，就算使用相同的閱讀系統，兩位使用者各自擁有的副本，其來源該不同。
注意事項
容器根URL的特性為，合規的閱讀系統會將任何相對URL字串解析為一個內容URL。換句話說，相對連結不會「溢位」到容器內容之外，這是一項重要的安全功能。

實務上，容器根URL的行為類於定義如下的URL：

URL元件	值
綱要	http或https
主機	localhost
埠	一個動態的埠，唯一指派給該EPUB實例
例如：

容器檔案	檔案路徑	URL
根目錄	empty string	http://localhost:49152/
包裝文件	EPUB/package.opf	http://localhost:49152/EPUB/package.opf
EPUB內容文件	HTML/file name.xhtml	http://localhost:49152/HTML/file%20name.xhtml
URL字串
（可在在內容文件中發現作為範例）	內容URL
../HTML/file%20name.xhtml	http://localhost:49152/HTML/file%20name.xhtml
/Media/img.png	http://localhost:49152/Media/img.png
../../../Media/img.png	http://localhost:49152/Media/img.png
請注意，後兩個連結禁止在EPUB出版品使用，以確保對不合規以及遺存閱讀系統和工具鏈的互通性。

注意事項
有些語言規範參考了之前的意見徵求書（Requests For Comments,RFC）[url]，在這樣的案例中，特定語言適用較早的RFC。

注意事項
不像大多數的語言規範，閱讀系統必須使用容器根URL作為base URL[url]供META-INF目錄中的所有檔案使用。請見[epub-33]中解析META-INF目錄中的URL章節。

4.1.2 檔案名稱

儘管EPUB製作者需要遵從各種檔案名稱與檔案路徑的限制[epub-33]以獲得最大的互通性，閱讀系統應該嘗試處理不符合這些規定的檔案名稱與路徑。不合規的檔案名稱與路徑可能只會在某些作業系統上產生問題。

本規格不指定無法顯示OCF檔案名稱與路徑的閱讀系統，該如何處理不相容問題。

4.1.3 META-INF目錄

容器檔案（container.xml）
閱讀系統預設上必須使用第一個rootfile元素所參照的包裝文件[epub-33]來處理EPUB出版品。如果閱讀系統能提供方法從其他可以取得的選項中挑選，其可以選擇更為適切的包裝文件。

後設資料檔案（metadata.xml）
閱讀系統應該忽略具備無法識別跟元素的metadata.xml檔案[epub-33]。

宣告檔案（manifest.xml）
閱讀系統不得使用ZIP封存檔或者manifest.xml檔案a>中的補充性宣告資訊[epub-33]來處理EPUB出版品。

簽章檔案（signatures.xml）
在估算摘要用於驗證signatures.xml檔案[epub-33]中的簽章前，閱讀系統必須解密在簽署後加密的檔案──在簽署前加密的檔案不得被解密。

請參照供XML簽章使用的解密轉換（Decryption Transform）[xmlenc-decrypt]以獲得更多關於識別簽章後資料解密的識別方式。

其他檔案
閱讀系統不得在META-INF目錄中遇到未列於保留的檔案的設定檔時出現問題[epub-33]。

4.2 OCF ZIP容器

一個閱讀系統:

必須將任何把內容分割成斷片[zip]的OCF ZIP容器視為錯誤。

必須將任何使用Deflate[rfc1951]以外壓縮技術的OCF ZIP容器視為錯誤。

必須支援定義為「Version 1」的ZIP 64延伸[zip]。

必須將使用[zip]加密功能的OCF ZIP容器視為錯誤。

如果要解壓縮內容，可以產生一個物理目錄作為OCF抽象容器的根目錄。

不需要保存OCF ZIP容器透過載入與儲存操作時，外於OCF抽象容器脈絡的資訊。詳細而言，閱讀系統不需保存CRC值、comment欄位或者其他保有對應到特定作業系統之檔案系統資訊的欄位（例如外部檔案屬性以及額外的欄位）。

關於OCF ZIP容器封存檔中的特定欄位，閱讀系統：

必須將treat version needed to extract，其在本地檔案檔頭表格[zip]若不為10、20或者45的話，視為錯誤。

必須將compression方法的欄位值，其在本地檔案檔頭表格[zip]若不為0或8的話，視為錯誤。

必須將有Archive decryption header，或者Archive extra data record[zip]的OCF ZIP容器視為錯誤。

4.3 字型模糊化

閱讀系統應該支援字體解模糊化，如[epub-33]中字體模糊化所定義。

為了恢復原始資料，閱讀系統應該單純地將程序反過來進行：來源檔案變成模糊化資料，以及目標檔案包含原始資料。

注意事項
EPUB 3早在EPUB 3.0.1就允許字型模糊化，但並未指定模糊化與壓縮的順序。就結果來說，閱讀系統可能在解壓縮與解模糊化後遇到不合規的字體。在這樣的實例中，在解壓縮前解模糊化可以得到合規的字體。閱讀系統不必支援這種補償的手段，但是開發者應該在支援EPUB 3內容時考慮加入。

5. 包裝文件處理

閱讀系統必須處理包裝文件[epub-33]。

5.1 基礎行文方向

如果有設定dir屬性[epub-33]，並且指示基礎行文方向為ltr或rtl，閱讀系統必須以定義在[bidi]中更高階的協定來覆寫bidi演算法，如果基礎行文方向為ltr，將段落嵌入層級設定為0，或基礎行文方向為rtl時，為1。

如果基礎行文方向為auto，在這樣的狀況下，閱讀系統必須利用Unicode bidi演算法來決定文字方向，由[bidi]的規則P2開始。

注意事項
儘管在[epub-33]中，於包裝文件後設資料中設定文字方向被標記為實作不足，閱讀系統若有全球性的使用者，或者宣稱能支援各種語言的內容，強烈推薦在將後設資料公開給讀者時實作這項功能。忽略文字方向會造成易讀性問題。

如果閱讀系統的支援達到必要的基準，實作不足的標記會由[epub-33]中移除。

5.2 唯一識別碼

閱讀系統不應依賴唯一識別碼（unique identifier），認為獨特的識別碼會用於唯一一本的EPUB出版品上。判斷兩本有著相同唯一識別碼的EPUB出版品為同一出版品的不同版本，或者不同的出版品，可能需要檢視其他後設資料，像是最後修改日期、書名以及作者。

5.3 後設資料

空白
閱讀系統必須在處理都柏林核心[dcterms]與meta元素值[epub-33]前，剝去並且壓縮ASCII空白[infra]。

dc:identifier元素
為了判斷dc:identifier元素的值[epub-33]是否符合既有的系統，或者受到發行機關所承認，閱讀系統應該檢查identifier-type特性[epub-33]。

dc:title元素
閱讀系統必須識別文件順序中第一個dc:title元素[epub-33]作為EPUB出版品的主要標題，並且在其他title元素之前優先呈現給使用者。

本規格不定義如何處理額外的dc:title元素。

dc:language元素
在dc:language元素中指定該EPUB出版品的語言為資訊性質。此資訊有一些用途包括：

透過閱讀系統的使用者介面呈現給使用者
用於強化書架的功能性（例如按照語言排序）
用於最佳化閱讀介面（例如預先載入文字轉換語音語言）
請見3.7 國際化以獲得更多關於如何決定出版品資源語言的細節。

dc:creator元素
當決定顯示順序時，閱讀系統必須使用metadata區塊中dc:creator元素[epub-33]的文件順序，第一個出現的creator元素即為主要創作者。如果閱讀系統要將創作者後設資料呈現給使用者，其應該在可能時，將所有列於metadata 區塊中的創作者一併列出（基於顯示上的考量，而不限制何時）。

meta元素
閱讀系統應該忽略所有無法辨識property屬性，[epub-33]定義表述的meta元素。閱讀系統不得遇到未知的表述時出現問題。

如果閱讀系統無法辨識scheme屬性[epub-33]值，其應該將該元素的值視為字串。

link元素
取得與支援連結的資源為選擇性。

在hreflang[EPUB-33]屬性中指定的語言純粹只是建議性質。在資源中表述的語言資訊決定解析與處理目的使用的語言，定義在國際化需求中。

5.4 宣告

閱讀系統必須忽略無法辨識的properties屬性[epub-33]值。

閱讀系統在處理EPUB出版品時不應使用連結的資源，因為具備限制以及涉及風險（例如，缺少關於資源的資訊以及如何處理，遠端託管資源的安全性風險，缺少回退等。）。

閱讀系統遇到出版品資源為不支援的MIME媒體類型[rfc2046]時，必須穿越宣告回退鍊[epub-33]直到識別支援的出版品資源，用來取代不支援的資源。如果閱讀系統支援回退鍊中多個出版品資源，其可以基於資源的 properties屬性[epub-33]值來選擇資源，否則其應該尊重EPUB製作者偏好的回退順序。如果閱讀系統不支援回退鍊中的任何資源，其必須警告使用者內容無法顯示。

當宣告回退[epub-33]提供給頂層內容文件使用時，閱讀系統可以從可用的選項中挑出最適宜的版本來處理該內容（也就是檢查每一個的properties屬性）。

閱讀系統必須在遇到其已經遇過的第一個參照時終止回退鍊。

5.5 書脊

閱讀系統必須提供按照定義在spine元素[epub-33]中的方法來處理EPUB出版品，包括：

識別第一個主要（線性）itemref[epub-33]作爲預設閱讀順序的起點；以及，
依序處理spine中給予的接續主要項目。
當使用者按照定義在spine元素中的預設閱讀順序閱讀時，閱讀系統可以自動跳過非線性的itemref元素[epub-33]。當使用者啟動超連結到非線性資源時，這時閱讀系統必須處理參照的資源或者指定的回退。閱讀系統也可以提供選項供使用者決定要跳過預設的非線性內容或者不跳過。

如果EPUB製作者未指定page-progression-direction屬性[epub-33]，閱讀系統必須推測其default的值，當page-progression-direction值為default，閱讀系統可以選擇處理方向。

如果page-progression-direction有default以外的值，閱讀系統必須忽略任何從pre-paginated XHTML內容文件中計算出的方向性。

閱讀系統必須忽略書脊中itemref properties屬性[EPUB-33]中無法辨識的所有值。

閱讀系統在處理線性閱讀順序時，不得跳過對重複宣告項目[EPUB-33]的參照。閱讀系統必須為了使用者介面（UI）目的，將這些視為有區別的項目（例如同一頁面每次出現都可以被獨立被加上書籤或者註解）。當閱讀系統跟從超連結到書脊中重複受參照的資源時，閱讀系統必須導覽到線性閱讀順序中在文件第一次出現的位置。

5.5.1 書脊覆寫

當書脊itemref元素的properties屬性覆寫掉全域處理特性[epub-33]時，閱讀系統必須跟從覆寫全域值以顯示書脊項目的規定。

例如，一個書脊項目包含了layout-pre-paginated覆寫[epub-33]，在處理上就該跟從全域pre-paginated值的規定。

如果在properties屬性中有多於一個的覆寫擁有相同特性時，閱讀系統必須只使用第一個值。

5.6 集合（Collections）

在本規格的脈絡下，閱讀系統對集合[epub-33]的支援為選擇性。閱讀系統必須忽略定義了無法辨識角色的collection元素。

5.7 遺存（Legacy）功能

閱讀系統不得支援合乎本EPUB版本[epub-33]內容中的遺存功能。

6. EPUB內容文件處理

EPUB內容文件[epub-33]的定義包含各種製作上的限制以對內容的跨界相容性進行最佳化（例如禁止以CSS設定語言與方向[epub-33]）。除非在本規格另有陳述，閱讀系統可以支援這些受限制的功能。

6.1 XHTML內容文件

閱讀系統必須處理XHTML內容文件[epub-33]。

除非在本章節中明確定義為覆寫，閱讀系統必須使用定義在[html]中的語義來處理XHTML內容文件，並且尊重任何在之中描述的使用者代理符合性限制。

6.1.1 HTML延伸

6.1.1.1 RDFa

閱讀系統對屬性處理模型[rdfa-core]的支援為選擇性。

6.1.1.2 內容切換（不再推薦）

不再推薦使用switch元素[epub-33]。請參見在[epubcontentdocs-301]中的定以獲得實作資訊。

6.1.1.3 epub:trigger元素（不再推薦）

不再推薦使用trigger元素epub-33]。請參見在[epubcontentdocs-301]中的定以獲得實作資訊。

6.1.1.4 客製化屬性

閱讀系統可以在客製化屬性不變更本規格規定的前提下，支援該屬性。

6.1.2 HTML歧異與限制

6.1.2.1 Microdata

閱讀系統對屬性處理模型的支援為選擇性，與json的轉換相同[html]。

6.1.2.2 MathML

為了支援嵌入於XHTML內容文件的MathML[mathml3]，閱讀系統需：

必須為一個顯示用MathML的遵從輸入處理器，如[mathml3]規格所定義。

如果有顯示區域必須支援顯示用MathML的視覺處理。

可以支援在annotation-xml元素[mathml3]中發現的內容MathML處理。

注意事項
閱讀系統可以選擇使用第三方函式庫，像是
6.1.2.3 嵌入SVG

閱讀系統必須處理嵌入於XHTML內容文件中的SVG，如6.2 SVG內容文件所定義。

6.1.2.3.1 嵌入SVG與CSS

對參照方式，為嵌入在XHTML內容文件中的SVG添加樣式之目的，閱讀系統不得套用包含文件中的CSS樣式規則到參照的SVG文件。

對以包含方式在XHTML內容文件中嵌入SVG添加樣式，閱讀系統必須套用包含文件中可適用的CSS規則到包含的SVG元素中。

注意事項
透過參照包含的SVG以分別的文件進行處理，其包含自己的CSS樣式規則，比照SVG內容文件。請注意在[html]object元素中參照一份外部[html]元素時，狀況相同。

6.1.2.4 表單遞送

閱讀系統對[html]form元素的遞送支援為選擇性。例如，閱讀系統可以透過限制網路存取避免表單遞送。

6.2 SVG內容文件

閱讀系統必須處理SVG內容文件[epub-33]。

為了處理SVG內容文件以及嵌入在XHTML內容文件中的SVG，閱讀系統需：

必須使用定義在[svg]中的語義來處理SVG內容文件，並且尊重任何其中描述的使用者代理符合性限制。除非在本章節中明確定義為覆寫。

必須符合定義在6.4 腳本中的符合性標準。

如果有顯示區域則必須支援使用定義在樣式[svg]中的CSS進行SVG的視覺處理。並且其應該所有定義在特性索引[svg]中的特性。對嵌入SVG的狀況而言，閱讀系統也必須符合定義在6.1.2.3.1 嵌入SVG與CSS中的規定。

6.3 層疊樣式表（CSS）

如果閱讀系統有顯示區域，其必須支援XHTML內容文件加上CSS[epub-33]的視覺處理。

為了支援CSS，閱讀系統：

必須支援在[csssnapshot]中描述的正式CSS定義。

應該支援在[csssnapshot]中可適用的模組，其至少達到推薦候選（Candidate Recommendation）狀態[w3cprocess]（並且受到廣泛實作）。

必須支援[truetype]、[opentype]、[woff]、以及[woff2]字型資源，透過@font-face規則[css-fonts-4]所參照。

應該支援所有定義在CSS樣式表─有字首的特性[epub-33]中所有有字首的特性。

應該適用寫在EPUB內容文件中的 EPUB製作者定義的樣式表。

SHOULD NOT覆寫EPUB製作者的樣式表，但應該在必要時以方法保存層疊：透過使用者代理的樣式表、getOverrideStyle方法[dom-level-2-style]，或者[html]style屬性。

可以因使用者互動覆寫部分EPUB製作者的樣式表。

除了支援以上定義的CSS特性外，閱讀系統的使用者代理樣式表應該支援[html]推薦的預設處理。

閱讀系統開發者應該實作CSS支援，達到主要瀏覽器的等級，並且公開其使用者代理樣式表，以及如何與EPUB製作者的樣式表互動。

6.4 腳本

閱讀系統應該支援腳本[epub-33]。

閱讀系統對腳本的支援依靠其使用脈絡：

閱讀系統應該在流動內容的EPUB內容文件中，支援容器限制腳本[epub-33]。

閱讀系統應該在固定版面文件[epub-33]中支援書脊層級腳本[epub-33]。

閱讀系統應該在使用rendition:flow特性「"scrolled-doc」或「scrolled-continuous」[epub-33]顯示模式的流動內容EPUB內容文件中，支援書脊層級腳本。同樣的，如果在流動內容EPUB內容文件中支援書脊層級腳本，其必須實作「scrolled-doc」顯示模式，以及應該實作「scrolled-continuous」顯示模式。

閱讀系統可以支援其他脈絡的腳本，但是本規格並不陳述這樣的腳本。結論而言，在其他脈絡下對腳本的使用可能在跨閱讀系統時不穩定。

如果閱讀系統支援腳本：

其可以按照[html]中互動、有腳本的使用者代理，來處理有腳本的內容文件。

其必須指派一個唯一來源[html]，由EPUB出版品中所有書脊層級腳本所共享。來源[html]必須對閱讀系統中每一個使用者特定的EPUB出版品實例而言為唯一。

其不得允許容器限制的腳本變更主EPUB內容文件的[dom]或者其他EPUB出版品中的內容。以及不得允許操動包含四方形的尺寸。（注意，儘管腳本並非容器限制，閱讀系統可能對內容變更給予限制。請見dom-manipulation功能）。

其可以在執行時，對腳本能力做出附加的限制（例如限制網路存取）。

其必須定義在B. epubReadingSystem物件中的epubReadingSystem介面，來延伸導覽物件[html]。其也必須在容器限制腳本脈絡中，支援定義在B.4.1.2 Features中的dom-manipulation以及layout-change。

如果閱讀系統不支援腳本，其必須按照Fallbacks for scripted content documents [epub-33]供有腳本內容文件回退之定義，處理有腳本的內容的回退。

6.4.1 本地儲存

閱讀系統可以阻斷腳本透過cookies以及網頁儲存[html]來儲存持久性資料。

允許本地儲存[html]的閱讀系統應該提供讓使用者能檢視或者刪除資料的手段。

6.4.2 事件模型

閱讀系統應該在腳本環境中跟從[html]中的DOM事件模型，並且跳過UI事件，在執行任何與這些事件相關的動作前為之。

閱讀系統開發者必須確保腳本不能關閉關鍵功能（像是導覽）以限制可能的惡意腳本對閱讀系統產生影響的可能性。結果而論，儘管腳本環境應該能夠取消任何事件的預設動作，而有些事件可能無法被跳過，或者無法取消。

6.4.3 安全考量

本章節為非規範性。

支援腳本的閱讀系統開發者必須注意到閱讀系統執行有腳本內容時產生的安全問題。由於閱讀系統部署的腳本模型與瀏覽器相同，開發者必須將在網頁脈絡中會遇到的相同種類問題納入考量。

每一個閱讀系統必須確認是否特定文件中的腳本能被信任。閱讀系統應該將所有腳本視為不受信任（以及潛在惡意），開發者應該檢查各種維度的攻擊並且建立保護。詳細來說，開發者應該考量以下各點：

對於runtime環境的攻擊（例如，從使用者硬碟竊取檔案）；

對於閱讀系統自身的攻擊（例如，竊取使用者的書單或者造成非預期的行為）；

從一份EPUB內容文件對另一份文件進行攻擊（例如，竊取其他文件產生出的資料）；

透過未加密的腳本攻擊文件中加密的部分（例如，注入惡意腳本來抽取保護的內容）；

對區域網路進行攻擊（例如，竊取防火牆後伺服器中的資料）。

為了限制不受信任腳本造成的可能傷害，本規格推薦閱讀系統分派給每一本EPUB出版品一個獨特來源[html]（請見4.1.1 根目錄URL）。指派獨特來源可以確保書脊層級腳本[epub-33]能與其他EPUB出版品分離區隔，並且限制cookies[html]、網頁儲存[html]等的存取。

網頁API的範例也與「來源（origin）」的概念相繫，包含網頁儲存[html]以及IndexedDB[indexeddb]，EPUB內容文件可以透過腳本與其互動。閱讀系統允許使用者從其管理的資料庫（他們的「書架」）新增/移除出版品，可以在出版品一時移除及重新輸入內容資料庫時，維持出版品的獨特來源。相反地，閱讀系統可以為每次新增的出版品建立新的獨特來源。

本規格也推薦受容器限制的腳本[epub-33]不得調整主EPUB內容文件的DOM，以及/或者操弄包含的四邊形（請見6.4 腳本）。

請注意符合這些推薦事項並不保證能夠對以上列出的可能攻擊有所保護；開發者必須檢查每一項在其閱讀系統脈絡中潛在的脆弱性。

7. 導覽文件處理

閱讀系統必須處理EPUB導覽文件[epub-33]。

為了處理EPUB導覽文件，閱讀系統需：

必須讓使用者存取toc nav元素[epub-33]中的連結與標題。

應該在產生非基於HTML的導覽工具時，以其替代文字取代標題與標籤中不支援的非文字元素[epub-33]。如果元素裡兼具alt以及title屬性，應該偏好使用alt屬性。如果兩者都不具備，閱讀系統可以自行提供文字或者忽略該元素。

應該在具備page-list nav元素[epub-33]時，提供導覽到所列出分頁的方法。

可以讓使用者存取landmarks nav元素[epub-33]中的連結，以及可以使用連結啟動應用程式的功能。

可以提供存取未指定epub:type屬性或者宣告未知值[epub-33]的nav元素。

必須在觸發連結到出版品資源的連結時，從現在的閱讀位置移到目標位置。

當在書脊以外呈現時，不得列出nav元素的列表項目編號，無論是否支援CSS，列表項目的預設顯示樣式等同於list-style: none特性[csssnapshot]。

無論EPUB導覽文件是否為書脊的一部分，閱讀系統必須尊重以上規定。

8. 版面排版控制處理

8.1 固定版面文件

閱讀系統必須支援對固定版面文件[epub-33]的處理。

8.1.1 固定版面特性

8.1.1.1 rendition:layout特性

如果在包裝文件後設資料[epub-33]中沒有任何meta元素包含rendition:layout特性時，閱讀系統必須推定預設值reflowable為全域值。

當rendition:layout特性設定為pre-paginated，閱讀系統不得在處理同步跨頁時，在相鄰的內容槽中加入空白。

rendition:layout特性值有著以下處理規定：

reflowable
閱讀系統在處理時可以應用動態分頁。

pre-paginated
閱讀系統在處理時，必須將每一個書脊itemref[epub-33]製作成單一頁面。

8.1.1.2 rendition:orientation特性

如果在包裝文件後設資料[epub-33]中沒有任何meta元素包含rendition:orientation特性時，閱讀系統必須推定預設值auto為全域值。

rendition:orientation特性值有著以下處理規定：

auto
閱讀系統判斷該以何種方向處理EPUB內容文件。

landscape
支援多重頁面方向的閱讀系統應該將EPUB內容文件以landscape（橫寬直窄）方向處理。

portrait
支援多重頁面方向的閱讀系統應該將EPUB內容文件以portrait（直寬橫窄）方向處理。

以何種方式傳達其意圖以實作而定。

8.1.1.3 rendition:spread特性

如果在包裝文件後設資料＜[epub-33]中沒有任何meta元素包含rendition:spread特性時，閱讀系統必須推定預設值auto為全域值。

rendition:spread特性值有著以下處理規定：

none
閱讀系統不得將書脊項目組合成同步跨頁。閱讀系統應該在螢幕中央建立單一顯示範圍。

landscape
閱讀系統應該僅在裝置於landscape方向時將書脊項目處理成同步跨頁。

portrait（不再推薦）
閱讀系統應該將值「portrait」當作「both」的同義詞，並且無論方向都建立同步跨頁。

both
閱讀系統應該無論裝置方向都處理同步跨頁。

auto
閱讀系統可以在特定或者所有裝置方向使用同步跨頁，作為最佳化利用內容顯示區域的程序。

8.1.1.4 rendition:page-spread-* 特性

rendition:page-spread-left特性[epub-33]指示書脊項目應該被處理到跨頁的左手側槽中。 rendition:page-spread-right特性[epub-33]指示書脊項目應該被處理到跨頁的右手側槽中。

rendition:page-spread-left以及rendition:page-spread-right特性適用於預分頁及流動內容內容，並且僅在閱讀系統創建同步跨頁時套用。

rendition:page-spread-*必須優先於XHTML內容文件中設定page-break-before特性的任何值[csssnapshot]。

當流動內容的書脊項目跟在預分頁的項目之後，當其缺少rendition:page-spread-*特性值時，流動內容的項目應該由下一頁起──如[epub-33]中page-progression-direction屬性所定義。

閱讀系統必須尊重reflowable與pre-paginated書脊項目中的rendition:page-spread-*特性（例如透過加入空白頁）。

當預分頁的書脊項目跟在流動內容的書脊項目之後，當其缺少rendition:page-spread-*特性值時，預分頁的項目應該由下一頁起（如page-progression-direction屬性所定義）。

當閱讀系統遇到兩個書脊項目呈現真正的跨頁（也就是兩個相鄰的書脊項目有著rendition:page-spread-left與rendition:page-spread-right特性），其應該建立相鄰頁面間沒有空白的跨頁。

8.1.2 初始包含塊尺寸

XHTML
閱讀系統必須使用宣告於viewport meta標籤中表述的寬與高，為XHTML內容文件創建初始包含塊（initial containing block, ICB)，如[epub-33]. HTML中表述所定義。其必須裁去位置外於ICB的內容。

如果viewport meta標籤中的寬與高值包含非數字字元，但由數字開始（例如值包含長度單位宣告，如「500px」），該數字字首應該被當作像素值，之外的值必須被當作不合規。

就算語法不合規，閱讀系統應該嘗試從viewport meta標籤中取出width與height的值。

閱讀系統必須使用viewport meta標籤中第一個宣告的width及height特性（也就是忽略重複的宣告）。

如果viewport meta不包含width或者height值，或者這些值不合規定，閱讀系統可以補填值。例如，閱讀系統可以：

考量這些值分別為device-width與device-height；或者
尋找書脊中前一份內容文件，如果可適用，就使用所定義的ICB值；或者
考量將內容文件整體視為錯誤的XHTML內容。
如果一份XHTML內容文件包含多於一個的viewport meta標籤，閱讀系統必須使用文件順序中第一個以取得寬與高的尺寸。後來的宣告必須被忽略。

當ICB的長寬比與閱讀系統內容呈現區域的長寬比不匹配時，閱讀系統可以將ICB置放在使用者介面可容納的區域中；換句話說，可以在內容的任一邊（或者兩邊）加上黑邊（letter-boxing）。

SVG
閱讀系統必須使用在[epub-33]中在SVG中表述ICB的定義，以其尺寸建立初始包含塊（ICB）以處理SVG內容文件。

注意事項
當ICB的長寬比與閱讀系統內容呈現區域的長寬比不匹配時，閱讀系統應該跟從定義在[SVG]中供viewBox以及preserveAspectRatio屬性使用的規則。
8.1.3 顯示區域處理

當處理固定版面文件時，預設的意圖為內容呈現區域應該盡可能地佔據可使用的顯示範圍。閱讀系統不應在顯示範圍插入額外的內容，像是邊框、邊界、頁首、頁腳。

注意事項
本規格不定義如何在閱讀系統的內容呈現區域置放初始包含塊[css2]。

注意事項
將閱讀系統的控制工具呈現給使用者由實作端決定，也不包含在以上的預期行為中。

8.2 流動內容版面

閱讀系統應該解析流動內容的版面特性[epub-33]。

8.2.1 rendition:flow特性

如果閱讀系統閱讀系統支援指定的處理方式，其應該使用控制溢流內容的方法，但可以提供選項供使用者來覆寫要求的處理方式。

如果在metadata區塊[epub-33]中沒有任何meta元素包含此特性，閱讀系統必須推定預設值auto為全域值。閱讀系統可以僅支援此預設值。

rendition:flow特性值有著以下處理規定：

paginated
閱讀系統應該動態分頁所有溢流內容。

scrolled-continuous
閱讀系統應該將所有EPUB內容文件中可以溢流的內容處理成可捲動，以及應該將整份EPUB出版品處裡成一個連續的捲軸，從一個書脊項目到另一個書脊項目（除了區域覆寫[epub-33]）。

scrolled-doc
閱讀系統應該將所有EPUB內容文件處理成使用者可捲動的溢流內容，以及應該將每一份書脊項目處理成切分開的可捲動文件。

auto
閱讀系統可以使用其預設方式處理溢流內容，或者按照可以適用的使用者偏好方式來處理。

對rendition:flow-scrolled-continuous特性而言，捲動方向必須由itemref元素[epub-33]所參照的XHTML內容文件其根元素的區塊流動方向相對定義。如果區塊流動方向向下（由上而下），捲動方向必須為垂直。如果區塊流動方向是向右（由左而右）或者向左（由右而左）就必須為水平。

閱讀系統必須在處理預分頁書脊項目[epub-33]時，忽略rendition:flow特性及其覆寫。

注意事項
閱讀系統開發者可以決定不理會此項限制，並且接受rendition:flow的scrolled-continuous值作為開關，來將每一份預分頁的書脊項目呈現為一個垂直的長條（使其易於在智慧型手機或者電腦上閱讀）。這種呈現類型常被稱為「Webtoons」。有些出版社已經使用這種可能性。經過更多實驗以及孵化，本規格的未來版本可能將這種作法作為固定版面文件的標準功能。請參見github issue 2412。
8.2.2 rendition:align-x-center特性

當書脊項目設定rendition:align-x-center特性時，若可行，閱讀系統應該將內容在顯示範圍或者跨頁中處理成水平置中。這項特性不會影響到對書脊項目的處理，結果只會影響內容盒中置放位置。

對流動內容的內容，支援本特性的閱讀系統必須將每一份虛擬頁面置中。

本規格不定義當閱讀系統不支援這項特性，或者EPUB製作者不指定時的預設處理行為。閱讀系統可以自己的設計處理書脊項目。

8.3 viewport meta標籤

除了為固定版面文件取得初始包含塊的尺寸外，閱讀系統必須忽略在viewport meta宣告中的處理程序。

本限制適用於固定版面與流動內容文件。

8.4 客製化特性

閱讀系統可以在與定義在包裝處理用語集中的特性行為產生衝突的狀況下，支援客製化特性[epub-33]。

9. 媒體層疊處理

具備處理預錄音訊能力的閱讀系統應該支援媒體層疊[epub-33]。

如果閱讀系統不支援媒體層疊，其必須忽略以下兩項：

在宣告 item元素中的media-overlay屬性[epub-33]；以及
media-type屬性值為application/smil+xml的item元素。
9.1 載入媒體層疊

當閱讀系統載入包裝文件時，其必須參照宣告item元素[epub-33]的media-overlay屬性以找到EPUB內容文件所對應的媒體層疊。

閱讀系統必須支援XHTML內容文件的播放，以及可以支援SVG內容文件。

播放必須開始於媒體層疊元素想要對應到EPUB內容文件上的開始點。請注意EPUB內容文件的開始點可能對應到媒體層疊開始或者中間的元素。 當媒體層疊文件結束播放時，閱讀系統應該載入下一個EPUB內容文件（如在包裝文件書脊中所指定）也載入對應的媒體層疊文件。

9.2 基本播放

9.2.1 對時與同步

閱讀系統必須按照序列處理body元素[epub-33] 下接的子元素。seq元素[epub-33]的子項必須被按照序列處理，當最後一個子元素結束播放時完成播放過程。閱讀系統必須平行處理par元素[epub-33]的子項，當所有的子項結束播放時完成播放過程。當body元素的最後一個子項結束播放時，閱讀系統完成媒體層疊文件的播放過程。

9.2.2 處理音訊

當有媒體層疊audio元素[EPUB-33]時，閱讀系統必須播放src屬性所參照的聲音資源，由clipBegin屬性所提供的片段偏移時間開始，並且到clipEnd屬性[epub-33]所提供的片段偏移時間結束。

此外：

如果EPUB製作者沒有指定clipBegin屬性，閱讀系統必須推定其值為「0」。

如果EPUB製作者沒有指定clipEnd屬性，閱讀系統必須推定該值為物理媒體的完整長度。

如果clipEnd的值超過物理媒體的完整長度，閱讀系統必須推定其值為物理媒體的完整長度。

使用者可以控制音訊播放的選項應該包含時長調整（timescale modification），這樣使用者可以更改播放速率而不會讓聲調變形。推薦的範圍為一半速度到兩倍速。

9.2.3 處理EPUB內容文件元素

當呈現媒體層疊text元素[epub-33]時，其src屬性包含一個URL-斷片（URL-fragment）字串參照到EPUB內容文件的特定部分，閱讀系統應該確保參照的位置可以在顯示範圍內可見。在[html]元素ID與SVG斷片識別碼[svg]之外，閱讀系統可以支援其他斷片識別碼綱要。

在媒體層疊播放時，具備顯示範圍的閱讀系統應該添加後設資料特性active-class以及playback-active-class[epub-33]給予的class名稱到EPUB內容文件中適切的元素上，如果有該特性的話。反過來說該class名稱應該在播放狀態改變時移除，如[epub-33]中關聯樣式資訊所描述。

active-class與playback-active-class後設資料特性為選擇性，如果忽略，閱讀系統行為交由實作端決定。

當斷片識別碼[epub-33]不參照元素時，閱讀系統行為也交由實作端決定。

9.3 與EPUB內容文件互動

注意事項
本規格先前的版本包含一些關於嵌入音訊以及影片[epubmediaoverlays-32]的資訊。這項功能不再推薦使用。
9.3.1 導覽

由於媒體層疊與EPUB內容文件緊密連結，閱讀系統可以非常容易地基於目前媒體層疊播放的當下位置找到EPUB內容文件中的座標。如果使用者停止同步播放，並且導覽到EPUB出版品的另一個部分，同步播放必須從該點繼續播放。例如，如果EPUB內容文件中指定的頁碼為想要去的位置，那麼就從媒體層疊中找到相同的點並且開始由此播放。

這做法也適用於當使用者選擇EPUB導覽文件中的導覽點時同步播放媒體層疊播放。閱讀系統載入該檔案的媒體層疊，以及基於導覽點目標的ID尋找正確的播放開始點。

注意事項
EPUB製作者可以直接讓媒體層疊文件與EPUB導覽文件連結，以提供內容的同步播放，無論該XHTML內容文件是否位於書脊中。請見[epub-33]中的EPUB導覽文件以獲得更多資訊。

注意事項
EEPUB製作者可以將媒體層疊文件元素與EPUB內容文件結構，像是表格，相關聯。閱讀系統應該確保媒體層疊播放在使用者導覽表格列與格時保持同步。閱讀系統也可以在處理內容格時播放呼應的表格標題。

9.3.2 嵌入影音（不再推薦）

指引到嵌入音訊與影片的自動播放現在不再推薦。請參照在[epubmediaoverlays-32]中的定義以獲得更多資訊。

9.3.3 文字轉換語音

當媒體層疊text元素沒有對應的audio[epub-33]元素，參照到目標EPUB內容文件的文字時，具備文字轉換語音（text-to-speech, TTS）能力的閱讀系統應該使用TTS處理參照的文字。

閱讀系統應該使用目標EPUB內容文件中提供與語音相關的資訊，來播放聲音流作為媒體層疊處理的一部分。

注意事項
請見[epub-tts-10]中的EPUB 3文字轉換語音支援以獲得更多關於在EPUB出版品中支援TTS科技的資訊。

媒體層疊text元素生命週期對應到關聯語音合成的處理時間。text元素的長度因此不明確（以及透過母par元素推斷）需要由文字轉換語音引擎的執行來決定，所以無法在製作時知悉（像是朗讀速度、暫停以及其他音律參數等因素都會影響到音訊輸出）。這也意味著閱讀系統在使用包裝文件中的duration特性值時應該將其視為近似值。

9.4 可跳過性與可跳出性

9.4.1 可跳過性（Skippability）

閱讀系統應該使用媒體層疊元素中epub:type屬性所提供的語義資訊，來提供使用者跳過內容的選項。

當啟動跳過內容時，閱讀系統必須停止任何epub:type屬性包含符合可跳過結構的語義 之par以及seq元素的播放。

9.4.2 可跳出性(Escapability)

當播放媒體層疊時，閱讀系統應該提供使用者選項以離開（「跳出」）可跳出的結構[epub-33]，其由epub:type屬性[epub-33]，其值是否來自可跳出的結構清單以進行判斷。如果使用者要從可跳出的結構中跳出，閱讀系統必須從結構之後下一個接續的元素開始播放。

10. 處理結構語義

閱讀系統可以支援EPUB內容文件中的結構語義[epub-33]。

當處理epub:type屬性時，閱讀系統需：

可以為每個值取得展開的URL。

必須忽略用於元素中的術語，其用途不符合epub:type的定義[epub-33]。

可以與預設用語集[epub-33]所定義的無、部分、所有術語進行行為關聯。

可以與其他用語集的術語進行行為關聯。

11. 處理property值

閱讀系統可以支援用語關聯機制，供處理property資料類別值[epub-33]。

本章節定義了一個演算法，供從property資料類別值中取得展開的URL使用。其僅適用於支援[epub-33]用語關聯機制的閱讀系統。

不支援[epub-33]用語關聯機制的閱讀系統可以將property值處理成純字串值[infra]。不需要支援將值展開為URL，並基於其存在添加閱讀系統行為。

本演算法描述了使用定義在[infra]中術語以及資料類別的處理程序，以及，如果成功，回傳具備展開URL的字串值。對於不合規的特性回傳null值。

本演算法採用以下參數：

value: 處理的property值。
attr: 包含value的屬性名稱。
elem: attr所添附的的元素名稱。
doc: 處理的文件（例如，包裝文件、媒體層疊文件、EPUB內容文件）。
為了取得展開的URL，適用以下步驟：

讓baseURL、expandedURL、propertyPrefix以及propertyReference為空白字串

說明

在本演算法中：

baseURL
expandedURL將會擁有最終的URL，結合了基底URL以及特性參照。
propertyPrefix將會擁有該特性的字首[epub-33]（也就是冒號前的值）。從預設用語集而來的特性不會有字首，但其他都會。
propertyReference將會擁有特性的參照[epub-33]（也就是字首之後的值）。所有合規的特性都需要參照。

按照以下方式取得propertyPrefix以及propertyReference的值：

如果value不包含冒號（U+003A），將propertyReference設為value。

由冒號開始的值不合規，因為代表著沒有設置字首。

如果一個property值不包含冒號，就沒有字首。在這狀況下，該值由預設用語集而來，如本演算法的下一步驟說明。

說明
此外，如果value由冒號開始，則該值不合規，回傳null。

說明
以外的狀況，以第一個冒號將value切分，冒號前的字串設定到propertyPrefix，並且將冒號後的字串設定到propertyReference。

如果propertyReference不是合規的相對-路徑-無-綱要-位址（path-relative-scheme-less-URL）字串，如property資料類別定義[epub-33]所要求，該值不合規，回傳null。


例如，參照不得以位址-綱要（URL-scheme）字串開始，後接冒號。這項限制意味著以下字串並非合規的property值，因為第二個冒號可能代表一個綱要，如：foo:bar:baz/qux。

此外還限制字元必須使用百分比編號編碼。

說明
以以下方式取得baseURL的值：

如果propertyPrefix為空白字串：

如果attr是epub:type[epub-33]，將baseURL設定為
http://idpf.org/epub/vocab/structure/#
此外，如果elem為一個包裝文件的meta元素[epub-33]以及attr為scheme，該特性值不合規，回傳null。
此外，如果elem為一個包裝文件的meta元素[epub-33]，將baseURL設定為
http://idpf.org/epub/vocab/package/meta/#
此外，如果elem為一個包裝文件的link元素[epub-33]，將baseURL設定為
http://idpf.org/epub/vocab/package/link/#
此外，如果elem為一個包裝文件的item元素[epub-33]，將baseURL設定為
http://idpf.org/epub/vocab/package/item/#
此外，如果elem為一個包裝文件的itemref元素 [epub-33]，將baseURL設定為
http://idpf.org/epub/vocab/package/itemref/#
說明

如果property值沒有字首，那麼此步驟就將這些屬性或者元素所歸屬的預設用語集的URL分別指派。當一個包裝文件中的元素擁有多於一個的屬性都擁有property資料類別時，其屬性共享相同的預設用語集。因此，不需要同時檢查元素與屬性以決定要指派哪一個URL。

EPUB 3中有一個屬性不具備預設用語集，其為scheme屬性[epub-33]。沒有字首的scheme值不合規。

此外：

如果在doc的文件元素宣告了一個prefix屬性，以及該屬性包含的字首能與propertyPrefix匹配，就將baseURL設定到該字首宣告關聯的URL。

此外，如果propertyPrefix匹配到doc所保留的字首[epub-33]，就將baseURL設定到保留的字首所關聯的URL。

說明

當一個property值有字首時，第一個要檢查的地方就是文件元素中的prefix屬性宣告之基底URL。

如果作者沒有為字首指派URL，下一步就是檢查該字首是否與保留的字首相匹配。

請注意作者指派的字首URL會覆寫保留的字首的URL。

如果baseURL為空白字串，該property值不合規，回傳null。

說明

如果基底URL經過以上處理程序還是為空白，就是代表字首沒被保留或者映射，或者該元素或屬性經過處理後不是[epub-33]所定義可以接受的property資料類別。

缺少基底URL，就無法產生展開的URL，所以該值不合規。

將expandedURL設定為baseURL與propertyReference結合後的值。當結合這些值時，不要添加分隔符。
如果expandedURL不是合規的URL字串，該值不合規。回傳null。

此外，回傳expandedURL。

說明
注意事項
閱讀系統不必解析結果URL[url]或者試圖取得展開後URL的資料。展開一個property資料類別值為完整URL僅確保閱讀系統遇到預期的值（也就是因為不同的EPUB製作者可以為相同的字首指派不同的URL，兩個值直到展開為止看起來都相同）。

12. 向後相容性

閱讀系統必須嘗試解析包裝文件version屬性[epub-33]的值小於「3.0」的EPUB出版品。

EPUB出版品有較舊的版本編號不總是會如預期一般被處理，除非使用各自的規格進行解析。閱讀系統應該以其規格的定義支援這樣的EPUB出版品。

13. 向前相容性

閱讀系統應該嘗試解析包裝文件version屬性[epub-33]的值大於「3.0」的EPUB出版品。

14. 近用性

本章節為非規範性。

儘管本規格的主要關注點為如何解析以及處理EPUB出版品，而不強制要求所有的閱讀系統都必須提供特定的使用者介面。但依然有共同的近用性問題，所有的閱讀系統開發者都必須注意，或者發現避免在其應用程式中出現。

W3C的使用者代理無障礙指引（User Agent Accessibility Guidelines）[uaag20]提供了許多有用的實踐，開發者應該採用以增進閱讀系統。因為許多瀏覽器會遇到的近用性問題，在專為EPUB的使用者代理上都會平行出現。

以下列表概要指出許多一些額外專屬於EPUB的領域，這些領域若缺少近用性，會影響到使用者的閱讀體驗：

書架──確保在存取以及開啟使用者的內容之過程具備無障礙輔助。例如，不能僅依賴視覺顯示，像是封面圖片。呈現標題、作者的文字表述，以及其所使用的語言，都能讓輔助技術能正確地唸出內容。
使用者介面控制──確保所有控制項（例如，搜尋欄位、註記控制、以及載入功能，如目次，的按鍵）都能讓輔助技術取用，而其動作不依賴指定的模式（例如僅能透過觸控或者滑鼠操作）。
搜尋──對所有EPUB內容文件進行全文內容搜尋存取，對於確保使用者能夠輕易掌握資訊而言為必要。
顯示控制──提供使用者方法以調整內容樣式為他們偏好的狀況（例如，變更或者放大字級，增加行距及字句，套用替代的對比）。
放大（Zoom）──允許使用者放大內容到他們所需要的更好的尺寸，特別對固定版面文件而言。
閱讀控制──確保從頁到頁以及文件到文件間的閱讀能力不依賴物理互動（也就是輔助科技的使用者可以閱讀該內容而不會困在頁或文件的結束處）。
API整合──確保近用性樹，包含對role、states以及properties[wai-aria-11]的支援，能夠被作業系統的近用性API所取得，如此一來使用者在使用輔助科技時，得以與內容做完整互動。
文件物件模型（Document Object Model, DOM）──提供對EPUB內容文件之[dom]的存取，如此一來使用者可以研究來源中所表述的語義與結構。
目次──確保使用者可以存取連結文字，包含視覺內容的替代文字。應該能夠使用不同的輸入方式觸動目次連結。
DAISY Consortium維護了一份近用性測試套件以評量這些以及更多要點。

15. 安全與隱私

15.1 概要

本章節為非規範性。

EPUB出版品的特質在於其結構。EPUB格式提供了表現、包裝以及將一組有結構並在語義上強化的網頁內容─包括HTML、CSS、SVG、JavaScript以及其他資源─編碼以單一檔案容器配布的手段。

對閱讀系統而言，該手段意味著安全與隱私問題主要與這些格式的特質相連結，並且近乎要面對所有網頁內容的威脅。

閱讀系統開發者也需要負擔雙向的責任，一方確保應用程式的安全與隱私，並且協助限制使用者受到內容在處理時受到的威脅。本章節剩下的部分將發掘EPUB 3的風險模型，用意為協助開發者認識並且移除這些風險。

注意事項
對於製作EPUB出版品相關的風險，請參照[epub-33]中的安全與隱私章節。

15.2 威脅模型

本章節為非規範性。

對使用者而言最大的威脅來自於其閱讀的內容[epub-33]，而站在第一線防衛這些攻擊的就是他們所使用的閱讀系統。使用者期盼閱讀系統能作為保鑣抵抗這些惡意內容，也經常沒意識到EPUB出版品會面對與網站相同的安全風險。

但儘管仰賴閱讀系統來保障安全與隱私，閱讀系統按照資訊被處理的方式，也會面對對使用者的非預期威脅。例如，追蹤使用者資訊以最佳化經驗為常見的需求，但在沒有使用者同意之下為之，閱讀系統就會衝撞到法律對隱私的規定。

本章節勾勒一些閱讀系統開發者必須考量的關鍵威脅，並在接下來的章節說明細節以及推薦事項。

腳本
惡意腳本呈現多種對閱讀系統攻擊的維度。例如，如果本地儲存不安全，腳本就可能試圖取得使用者的資料。若與網路存取一併提供，就可能試圖在不同意的狀況下蒐集使用者資料。

更多對這些議題的討論細節，以及如何移除這些威脅，提供在6.4.3 安全考量中。

惡意內容
EPUB出版品可以包含針對閱讀系統或者其運行的作業系統之安全漏洞所設計的資源。攻擊者可能也會透過檔案重新導向技巧，試圖存取遠端資源，像是符號連結或者檔案捷徑。

缺少對EPUB出版品簽署的標準方式意味著閱讀系統無法驗證內容從製作端到載入設備的過程是否受到竄改。

遠端資源
遠端資源讓EPUB出版品從不受信任的來源載入時，面對相同的風險。儘管EPUB出版品的出版社可以信任，遠端資源可能不是那麼一回事。

呼叫遠端資源也可能會被用來追蹤使用者資訊（例如透過伺服器紀錄）。閱讀系統應該限制透過HTTP要求時暴露的資訊，僅能提供取得資源必要的資訊。

EPUB的來源對EPUB製作者以及對每一種閱讀系統實作來說都為未知。結論上，如果EPUB製作者在自己控制的網頁伺服器上託管遠端資源，該伺服器實際上不能使用需要制定允許來源的的安全功能，像是供CORS的檔頭、Content-Security-Policy，或者X-Frame-Options。

外部連結
就像遠端資源，外部連結可以用於欺騙不知情的使用者開啟網站上的惡意資源，攻擊作業系統或者閱讀系統的漏洞。

同樣的，閱讀系統應該也要在開啟連結時，避免暴露潛在的使用者識別資訊（例如，不使用可追蹤的識別碼，或者透露非必要的使用者環境資訊）。

使用者生成的內容
使用者生成的內容屬於閱讀體驗的一環，例如從文字區域到其他互動元件，可能在內容安全性不足時，讓閱讀程式的安全或者使用者隱私面對威脅。更多關於腳本安全性的細節於6.4.3 安全考量中提供。

蒐集使用者資料
在未得到使用者的同意的情形下，蒐集關於使用者以及其閱讀習慣的資訊違反其隱私權，儘管該資訊僅供內部使用。

嘗試基於使用者的閱讀習慣或者其出版品的後設資料（例如無障礙偏好）來側寫使用者，會讓使用者暴露在非預期的危險之下。

此外，適用於[xml]以及[zip]檔案的安全考量也分別適用於包裝文件以及開放容器格式，請參見application/oebps-package+xml以及application/epub+zip格式媒體類別註冊中的「安全考量」以獲得近一步的細節。

15.3 推薦事項

閱讀系統開發者可以採用對隱私最強的措施就是，指出所意圖蒐集與使用，關於使用者及/或其閱讀行為的資料，並且獲得使用者同意以取得。他們應該也允許對這些資訊進行個人化和管控。

如果閱讀系統允許使用者儲存持久性資料，特別是個人識別資訊，其應該將資料視為敏感，並且不准讓第三方存取。

可以理解蒐集一些使用者資料供銷售、配發、以及EPUB出版品的運作為必須，特別是對銷售EPUB出版品平台而言，閱讀書的方法與其相連。在這些案例中，閱讀系統應該識別所搜集的資料、如何被使用，並且允許使用者退出（然而零售商可以選擇透過其他方式告知使用者，像是在使用者在網站上創建帳號時）。推薦將蒐集的資料匿名化以保障使用者以及閱讀系統的安全及隱私。

也可以理解使用者資料對於一些閱讀系統的功能而言為必要或者有用。在這些案例中，也推薦匿名化。閱讀系統也應該告知使用者需要哪些資料，以及會被作為何用，並且提供退出的方法。

內容處理器──定義為處理接受EPUB內容供配布、顯示或者銷售的實體──也需要注意接受書檔時的潛在風險。建議內容處理器在接受書檔時，除了常態的驗證步驟外，也須檢查內容是否含有惡意內容。這些步驟能包含運行病毒掃描、驗證外部連結以及遠端資源和其他預警事項。


當處理XML文件時，閱讀系統不應解析DOCTYPE、ENTITY以及NOTATION宣告[xml]中的外部識別碼。閱讀系統也應該考量與內部或者外部XML實體相關的安全風險，例如，已知的DoS攻擊如「十億笑聲（Billion laughs attacks）」或者「XML外部實體攻擊」。

注意事項
額外供外部連結、網路存取以及腳本的安全建議可以分別於3.9 外部連結、3.8 網路存取以及6.4.3 安全性考量取得。

A. 不支援的功能

閱讀系統可以支援不再推薦的功能[epub-33]。

注意事項
開發者應該在新增對不再推薦的功能支援前，將不大可能會遇到這些內容納入考量。

B. epubReadingSystem物件

注意事項
閱讀系統作為EPUB出版品的核心處理引擎，並且提供基於[dom]規格的腳本環境。所以儘管這裡的介面定義使用了[webidl]標記法供閱讀系統實作，網頁瀏覽器一般不需要實作這些物件。
B.1 介面定義

本規格延伸Navigator物件[html]如下。

WebIDL
[Exposed=(Window)]
interface EpubReadingSystem {
    boolean hasFeature(DOMString feature, optional DOMString version);
};

partial interface Navigator {
    [LegacyUnforgeable, SameObject] readonly attribute EpubReadingSystem epubReadingSystem;
};
注意事項
本規格不定義epubReadingSystem的特性延伸供WorkerNavigator物件[html]使用。因此閱讀系統不需要將epubReadingSystem物件在Worker腳本脈絡中透露，以及EPUB製作者不能仰賴其存在。

B.2 描述

Navigator.epubReadingSystem物件透過有腳本的內容文件可以提供介面以查詢使用者的閱讀系統資訊。

閱讀系統必須將epubReadingSystem物件在所有載入的有腳本內容文件之navigator物件中顯露，包含任何巢狀容器限制腳本脈絡[epub-33]。閱讀系統必須確保epubReadingSystem不晚於DOMContentLoaded事件被觸發前可以使用[html]。

注意事項
閱讀系統實作上可以因技術彈性原因，在有腳本的內容文件中創建複製的epubReadingSystem物件實例。在這狀況下，閱讀系統必須確保能穩定維護物件的狀態──能夠對特性以及方法反映其值──在所有複製的實例中。

B.3 特性

本規格用於定義name、version、以及layoutStyle特性，但這些現在已經不再推薦[epub-33]。要獲得更多資訊，請參照其在[epubcontentdocs-32]（供name以及version）以及[epubcontentdocs-301]（供layoutStyle）中的定義。

B.4 方法

B.4.1 hasFeature

B.4.1.1 描述

hasFeature方法回傳布林值以指示是否閱讀系統支援任何指定功能的版本，或者當閱讀系統無法辨識指定功能時，回傳undefined。

選擇性的version參數能讓EPUB製作者查詢客制功能，其可能隨著時間變得不相容。所回傳的值只是僅對特定版本的功能支援。

定義在本規格中的功能沒有版本號。如果閱讀系統支援本規格定義的功能，其 必須忽略任何提供的version參數並且回傳true值。

範例 1: JavaScript功能供顯示支援腳本操弄DOM
var feature = "dom-manipulation";

var conformTest = navigator.epubReadingSystem.hasFeature(feature);

alert("Feature " + feature + " supported?: " + conformTest);
B.4.1.2 功能

以下表格列出支援epubReadingSystem物件的閱讀系統必須辨識的一系列功能。當功能使用hasFeature方法查詢時，閱讀系統必須回傳布林值以指示支援狀態。

名稱	描述
dom-manipulation	腳本可以對文件的DOM進行結構變更（僅適用於書脊層級腳本[epub-33]）。
layout-changes	腳本可以變更CSS樣式的屬性而影響內容排版（僅適用於書脊層級腳本[epub-33]）。
touch-events	該設備支援觸控事件，以及閱讀系統將觸控事件傳給內容。
mouse-events	該設備支援滑鼠事件，以及閱讀系統將滑鼠事件傳給內容。
keyboard-events	該設備支援鍵盤事件，以及閱讀系統將鍵盤事件傳給內容。
spine-scripting	指示是否閱讀系統支援書脊層級腳本[epub-33]（例如，這樣容器限制腳本[epub-33]可以判斷動作能不能依靠頂層內容文件的腳本支援，在嘗試動作之前了解成功的機會）。
閱讀系統開發者可以添加額外的功能，但是本規格的未來版本可能會延伸此列表，所以可能會與客製化添加的功能產生衝突或者不相容。

C. 索引

C.1 本規格定義的術語

content display area
epubReadingSystem
EpubReadingSystem介面
供EpubReadingSystem使用的 hasFeature方法
供Navigator使用的 Navigator.epubReadingSystem屬性
obtain an expanded URL
C.2 參考資料定義的術語

[BIDI]定義以下術語：
Rule P2
the higher-level protocols
[CSS-FONTS-4]定義以下術語：
@font-face rules
[DOM-LEVEL-2-STYLE]定義以下術語：
getOverrideStyle
[EPUB-33]定義以下術語：
"scrolled-continuous"
"scrolled-doc"
active-class
alternative text
application/epub+zip
application/oebps-package+xml
Associating style information
audio element
audio core media type resources
body element
clipBegin
clipEnd
collections
container root URL
container-constrained scripting
content they read
content URL
core specification
CSS Style Sheets — Prefixed properties
dc:creator element
dc:identifier element
dc:language element
dc:title element
declare an unknown value
definition of epub:type
deprecated
dir
disallowed
duration
EPUB container
EPUB content documents
EPUB content documents
EPUB creators
EPUB manifest
EPUB navigation document
EPUB navigation document
EPUB navigation documents
EPUB publications
EPUB reading system
EPUB spine
epub:type attribute
escapable structures
Expressing in HTML
Expressing the ICB in SVG
Fallbacks for scripted content documents
file name and file path restrictions
fixed-layout document
fixed-layout documents
Font obfuscation
foreign resource
foreign resources
fragment identifier
global rendering property
hreflang attributes
identifier-type property
image core media type resources
item element
itemref element
landmarks nav element
layout-pre-paginated override
legacy features
link element
linked records
linked resources
links and headings
locally overridden
manifest fallback chain
manifest items
manifest.xml file
media overlay documents
media overlays
media-overlay attribute
meta element
metadata.xml files
OCF abstract container
OCF ZIP container
package document
package document
package document metadata
page-list nav element
page-progression-direction attribute
par element
Parsing URLs in the META-INF directory
playback-active-class
prefix
primary (linear) itemref
prohibiting CSS for setting language and direction
properties attribute
properties attribute
properties attributes
property attributes
property data type values
publication resources
publication resources
reference
reflowable layout properties
remote resources
rendition:layout property
rendition:orientation property
rendition:page-spread-left property
rendition:page-spread-right property
rendition:spread
Reserved files
reserved prefix
Resource locations
root directory
rootfile element
scheme attribute
scripted content documents
scripting
security and privacy section
seq element
signatures.xml file
spine element
spine-level scripting
structural semantics
SVG content documents
SVG content documents
synthetic spreads
terminology defined in EPUB 3.3
text element
text alternatives for visual content
this version of EPUB
toc nav element
top-level content documents
under-implemented
unique identifier
values
viewport
viewport meta declarations
visual rendering of XHTML content documents via CSS
vocabulary association mechanisms
XHTML content documents
XHTML content documents
xml:lang
[EPUB-TTS-10]定義以下術語：
EPUB 3 Text-to-Speech Support
[HTML]定義以下術語：
attribute processing model
conversion to JSON
cookies
DOMContentLoaded event is triggered
form element
local storage
Navigator interface
navigator object
object type
origin
style attribute (for html-global element)
suggested default rendering
top-level browsing contexts
web storage
WorkerNavigator interface
[INFRA]定義以下術語：
null
string
strip and collapse ASCII whitespace
[MATHML3]定義以下術語：
annotation-xml elements
Content MathML
input-compliant processor
Presentation MathML
[RDFA-CORE]定義以下術語：
attribute processing model
[URL]定義以下術語：
base
origin
path-relative-scheme-less-URL string
scheme
url parser
URL-fragment string
URL-scheme string
valid URL string
[WEBIDL]定義以下術語：
boolean type
DOMString interface
[Exposed] extended attribute
[LegacyUnforgeable] extended attribute
[SameObject] extended attribute
[XML]定義以下術語：
external
external identifiers
internal
xml:lang attribute
D. 變更紀錄

本章節為非規範性。

請注意本變更日誌僅列出自EPUB 3.2以來的顯著變更─這些變更會影響閱讀系統的符合性或有同等的重要性。

若要取得在改版過程中所有議題的列表，請參考工作小組的議題追蹤器。

D.1 由推薦候選以來的主要變更

11-Jan-2023: 新增注意事項建議閱讀系統開發者支援包裝文件的行文方向，儘管對製作端標記為實作不足。請見pull request 2515。
11-Jan-2023: 移除對實作不足功能的支援描述。請見pull request 2515。
06-Jan-2023: 降低對支援有字首CSS特性的規定到推薦。請見pull request 2514。
06-Jan-2023: 降低對導覽文件中非文字元素使用替代文字的規定到推薦，因為兩方都缺少支援。請見pull request 2513。
05-Jan-2023: 移除對連結記錄的處理規定。請見pull request 2512。
11-Nov-2022: 新增當生成非HTML的導覽工具時，以替代文字取代不支援的非文字元素之規定。請見issue 2477。
13-Oct-2022: 新增章節以說明對處理錯誤與回報的期待。請見issue 2454。
11-Oct-2023: 新增文字快速描述在遇到錯誤ICB設定時的閱讀系統行為。請見issue 2442。
06-10-2022: 將XML外部識別碼的限制從XML符合性敘述移到安全與隱私章節，新增額外的注意事項說明內部或外部實體的安全風險。請見issue 2433 以及issue 2477.
23-Sep-2023: 新增注意事項說明未來可能的功能rendition:flow的值可能用於控制如webtoon出版品。請見issue 2412。
19-Sept-2022: 將ARIA延伸章節從HTML規格中移除，因為已經包含了支援ARIA的規定。請見issue 2431。
14-Sept-2022: 整合閱讀系統對還在EPUB 3.3規格中不支援功能的支援規定。請見issue 2424。
28-Aug-2022: 不再推薦在媒體層疊中處理嵌入時序媒體的指引。請見issue 2397。
28-July-2022: 重構語義關聯機制章節，提供演算法已取得展開的URL。請見issue 2378。
22-July-2022: 不再推epubReadingSystem物件的name與version特性。請見issue 1872。
19-July-2022: 不允許ZIP容器將內容分割成斷片。請見issue 2360.
24-June-2022: 移除對不得使用hreflang值作為處理目的的重複規定。請見pull request 2343。
17-June-2022: 新增推薦事項以在開啟有綱要的URL前警告使用者，以及釐清外部連結章節不僅用於處理網頁綱要。請見issue 2320。
17-June-2022: 釐清對語義關聯機制的支援為選擇性。請見issue 2317。
07-June-2022: 不允許使用檔案URL。請見issue 2324。
07-June-2022: 提醒未受簽署的EPUB出版品可能有安全風險，以及新增推薦事項將側載未簽署的出版品視為不受信任。請見issue 2265。
07-June-2022: 更新隱私與安全推薦事項，使用規範性語言。
27-May-2022: 新增閱讀系統符合性章節。請見issue 2271。
27-May-2022: 新增推薦事項僅能透過https協定載入參照的遠端資源。請見issue 2263。
20-May-2022: 移除推薦事項以避免「不相關的文件」對持久性儲存的存取。此推薦事項與本改版中的獨特來源規定衝突並且顯得多餘。請見issue 2264。
17-May-2022: 新增用語索引。請見issue 2260。
D.2 由EPUB 3.2以來的主要變更

31-Mar-2022: 將客製化屬性製作規定移到製作規格中。新增閱讀系統對客製化特性的處理。請見issue 2134。
17-Mar-2022: 新增在媒體層疊文件中，抑制可跳過元素播放的規定。請見issue 2066。
11-Feb-2022: 修正媒體層疊中矛盾的支援描述。推薦能支援處理預錄音訊的就應該支援，如同之前EPUB 3版本。請見issue 1991。
04-Feb-2022: 更改非規範性的安全考量，控制網路存取、開啟外部連結，以及管理本地儲存為規範性推薦。請見issue 1957。
04-Feb-2022: 增加安全與隱私章中關於閱讀系統威脅模型一節，以及額外推薦事項以確保安全與隱私。請見 issue 1871、issue 1872, issue 1875以及issue 1876。
03-Feb-2022: 降低支援解模糊化的規定為推薦。請見issue 1873。
19-Jan-2022: 提高rendition:spreadd以及rendition:orientation特性的預設陳述為推薦，與rendition:layout相同。請見issue 1936。
08-Dec-2021: page-spread-center現在是spread-none的別名。請見issue 1929。
10-Nov-2021: 修改對內容URL以及處理相對URL的定義。請見issue 1374以及issue 1888。
01-Nov-2021: 新增當item參照在書脊中重複出現的閱讀系統行為陳述。請見issue 1686。
25-Oct-2021: 釐清閱讀系統必須在讀者透過超連結進入時，處理非線性資源。請見issue 1864。
27-Aug-2021: 新增無障礙列表以涵蓋對放大的需求，特別用於固定版面文件。請見issue 1776。
27-Aug-2021: 移除推薦對SVG中文字搜尋以及選擇的支援。以更一般性的搜尋近用性表列取代，以避免對閱讀系統使用者介面定義規定。請見issue 1774。
09-July-2021: 恢復客製化屬性章節，因為有已知的用例，但不參照到屬性註冊表。請見issue 1602。
09-July-2021: 移除推薦使用第一個語言標籤來判斷未指定的行頁方向。請見issue 1482。
18-June-2021: 移動對支援SSML、PLS辭典以及CSS 3 Speech支援規定到EPUB 3文字轉換語音支援備忘。請見issue 1690。
20-May-2021: 規定支援腳本的閱讀系統需提供腳本共享與獨特來源。請見issue 1659。
20-May-2021: 移除對閱讀系統作為合規的xml:base處理器規定。請見pull request 1678。
12-May-2021: 新增額外規定，要求閱讀系統忽略展開後為不合規URL字串，以及property值有空白參照的property值。請見issue 1673。
12-May-2021: 更改所有對URIs/IRIs的參照為URLs，以及對RFCs 3986及3987的參照為URL標準。請見issue 808。
06-May-2021: 推薦閱讀系統支援對HTML target元素以及SVG斷片識別碼在textref屬性以及text元素的src屬性的參照。對其他斷片識別碼綱要的支援為選擇性。請見issue 1586。
23-Apr-2021: 釐清閱讀系統應該嘗試處理不合規的檔案與路徑名稱。請見issue 1629
16-Apr-2021: 移除客製化屬性的章節。請見工作小組決議。
15-Apr-2021: 移除對「顯示邏輯」的參照。請見issue 1516 以及工作小組決議。
12-Apr-2021: 章節B. epubReadingSystem物件現在被標記為「有風險」。請見 工作小組決議。
09-Apr-2021: 新增章節專門說明近用性，以及移除對近用性規格過時的參照。請見issue 1608。
09-Apr-2021: 新增章節以釐清建立出版品資源主要語言以及基礎行文方向的符合性規定。請見pull request 1613。
01-Apr-2021: 新增章節以釐清如何從包裝文件的相對URL建立絕對URL。請見pull request 1468。
30-Mar-2021: 重構文件，移除重複的符合性章節與規定，其僅是作為定位點用以和製作規定結合。請見pull request 1597以及pull request 1609。
23-Mar-2021: 新增避免頂層導覽到資料URL的規定。請見issue 1564。
23-Mar-2021: 將當順著書脊閱讀時非線性內容從「壓制」改為「跳過」，以釐清意圖並非要移除所有對這樣內容的存取。請見issue 1480。
10-Mar-2021: 更改對於沒列在包裝文件中資源的限制為建議不要使用。請見issue 810。
09-March-2021: 對唯一識別碼的陳述改為非規範性，遵從工作小組的討論與決議。請見issue 1310。
08-Mar-2021: 移除推定處理後設資料預設值非必要的規定。請見issue 1313。
05-Mar-2021: 新增閱讀系統在結合DCMES與meta元素空白時，須按照[infra]規格定義的規定。請見issue 1295。
26-Feb-2021: 釐清：移除meta元素特性可以自行定義空白處理規則的例外，得按照[infra]定義裁去開頭與結尾空白。請見issue 1295。
19-Feb-2021: 更新腳本安全考量，推薦指派給EPUB出版品獨特來源的文字，比從EPUB內容文件層級製作網域孤立為佳。請見issue 1156。
15-Feb-2021: 釐清呈現導覽文件中nav元素的規定。toc nav現在為唯一必要的元素，page-list當存在，則為推薦，其他都是選擇性。請見issue 975。
10-Feb-2021: 新增最初的草稿15. 安全與隱私。
04-Feb-2021: 新增明確的規定，閱讀系統不能使dc:language元素中的語言作為資源的語言。
02-Feb-2021: 新增基礎行文方向判斷規則，供dir屬性處理新的auto值。請見issue 1491。
02-Feb-2021: 注意在link元素中新的hreflang屬性中的語言資訊不可信賴。請見issue 1488。
24-Dec-2020: 不再定義建立發布識別碼（release identifier）[epubpackages-32]的方法。請見issue 1440。
06-Nov-2020: 閱讀系統現在規定不得在doctype宣告中解析外部識別碼。請見issue 1338。
05-Nov-2020: 整合對客製化屬性命名空間URI的限制，排除所有idpf.org以及w3.org。請見issue 1388。
30-Sept-2020: 簡化EPUB核心規格的結構以降低理解與使用資訊的門檻。本規格現在整合了EPUB 3.2規格中包裝、內容文件、OCF與媒體層疊規格的閱讀系統規定。EPUB 3.3核心規格目前僅集中在製作規定上。
E. 致謝

本章節為非規範性。

規格，就像藝術，就像人類創作。沒有人對EPUB的貢獻多於Garth Conboy，他參與了規格發展的每一步，從最早1999年的OEB 1.0到現在的EPUB 3.3。若沒有Garth的遠見、知識，以及超常的善良本性，這一切都不會成真。我們將EPUB 3.3版貢獻於對他的紀念，Garth，我們永遠欠你一筆。

以下EPUB 3工作小組的成員對本文件的產製有所貢獻：:

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
此外，工作小組想要在此對EPUB 3規格與概要的前任編輯者致特別的感謝：Garth Conboy、 Marisa DeMeglio、Elika J. Etemad、Markus Gylling、William McCoy、 MURATA Makoto、James Pritchett、Tzviya Siegman、以及Daniel Weck。

F. 參考資料

F.1 規範性參考文件

[bidi]
Unicode Bidirectional Algorithm. Mark Davis; Ken Whistler. Unicode Consortium. 16 August 2022. Unicode Standard Annex #9. URL: https://www.unicode.org/reports/tr9/tr9-46.html
[css-fonts-4]
CSS Fonts Module Level 4. John Daggett; Myles Maxfield; Chris Lilley. W3C. 21 December 2021. W3C Working Draft. URL: https://www.w3.org/TR/css-fonts-4/
[csssnapshot]
CSS Snapshot. URL: https://www.w3.org/TR/CSS/
[dcterms]
DCMI Metadata Terms. DCMI Usage Board. DCMI. 20 January 2020. DCMI Recommendation. URL: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
[dom]
DOM Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://dom.spec.whatwg.org/
[dom-level-2-style]
Document Object Model (DOM) Level 2 Style Specification. Chris Wilson; Philippe Le Hegaret. W3C. 3 November 2020. W3C Recommendation. URL: https://www.w3.org/TR/DOM-Level-2-Style/
[epub-33]
EPUB 3.3. Matt Garrish; Ivan Herman; Dave Cramer. W3C. 4 January 2023. W3C Candidate Recommendation. URL: https://www.w3.org/TR/epub-33/
[epubcontentdocs-301]
EPUB Content Documents 3.0.1. Markus Gylling; William McCoy; Elika J. Etimad; Matt Garrish. IDPF. 26 June 2014. URL: https://idpf.org/epub/301/spec/epub-contentdocs-20140626.html
[epubcontentdocs-32]
EPUB Content Documents 3.2. Dave Cramer; Matt Garrish. W3C. 08 May 2019. URL: https://www.w3.org/publishing/epub32/epub-contentdocs.html
[epubmediaoverlays-32]
EPUB Media Overlays 3.2. Marisa DeMeglio; Daniel Weck. EPUB 3 Community Group. 08 May 2019. URL: https://www.w3.org/publishing/epub32/epub-mediaoverlays.html
[html]
HTML Standard. Anne van Kesteren; Domenic Denicola; Ian Hickson; Philip Jägenstedt; Simon Pieters. WHATWG. Living Standard. URL: https://html.spec.whatwg.org/multipage/
[infra]
Infra Standard. Anne van Kesteren; Domenic Denicola. WHATWG. Living Standard. URL: https://infra.spec.whatwg.org/
[mathml3]
Mathematical Markup Language (MathML) Version 3.0 2nd Edition. David Carlisle; Patrick D F Ion; Robert R Miner. W3C. 10 April 2014. W3C Recommendation. URL: https://www.w3.org/TR/MathML3/
[opentype]
OpenType specification. Microsoft. URL: http://www.microsoft.com/typography/otspec/default.htm
[rdfa-core]
RDFa Core 1.1 - Third Edition. Ben Adida; Mark Birbeck; Shane McCarron; Ivan Herman et al. W3C. 17 March 2015. W3C Recommendation. URL: https://www.w3.org/TR/rdfa-core/
[rfc1951]
DEFLATE Compressed Data Format Specification version 1.3. P. Deutsch. IETF. May 1996. Informational. URL: https://www.rfc-editor.org/rfc/rfc1951
[rfc2046]
Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types. N. Freed; N. Borenstein. IETF. November 1996. Draft Standard. URL: https://www.rfc-editor.org/rfc/rfc2046
[RFC2119]
Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc2119
[rfc2397]
The "data" URL scheme. L. Masinter. IETF. August 1998. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc2397
[rfc7230]
Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing. R. Fielding, Ed.; J. Reschke, Ed.. IETF. June 2014. Proposed Standard. URL: https://httpwg.org/specs/rfc7230.html
[rfc8089]
The "file" URI Scheme. M. Kerwin. IETF. February 2017. Proposed Standard. URL: https://www.rfc-editor.org/rfc/rfc8089
[RFC8174]
Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words. B. Leiba. IETF. May 2017. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc8174
[svg]
SVG. W3C. URL: https://www.w3.org/TR/SVG/
[truetype]
TrueType™ Reference Manual. Apple, Inc. URL: https://developer.apple.com/fonts/TrueType-Reference-Manual/
[url]
URL Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://url.spec.whatwg.org/
[w3cprocess]
W3C Process Document. URL: https://www.w3.org/Consortium/Process/
[webidl]
Web IDL Standard. Edgar Chen; Timothy Gu. WHATWG. Living Standard. URL: https://webidl.spec.whatwg.org/
[woff]
WOFF File Format 1.0. Jonathan Kew; Tal Leming; Erik van Blokland. W3C. 13 December 2012. W3C Recommendation. URL: https://www.w3.org/TR/WOFF/
[woff2]
WOFF File Format 2.0. Vladimir Levantovsky; Raph Levien. W3C. 10 March 2022. W3C Recommendation. URL: https://www.w3.org/TR/WOFF2/
[xml]
Extensible Markup Language (XML) 1.0 (Fifth Edition). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/
[xml-names]
Namespaces in XML 1.0 (Third Edition). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/
[xmlenc-decrypt]
Decryption Transform for XML Signature. Merlin Hughes; Takeshi Imamura; Hiroshi Maruyama. W3C. 10 December 2002. W3C Recommendation. URL: https://www.w3.org/TR/xmlenc-decrypt/
[zip]
.ZIP File Format Specification. 15 July 2020. Final. URL: https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT

F.2 參考性參考文件

[css2]
Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification. Bert Bos; Tantek Çelik; Ian Hickson; Håkon Wium Lie. W3C. 7 June 2011. W3C Recommendation. URL: https://www.w3.org/TR/CSS21/
[epub-tts-10]
EPUB 3 Text-to-Speech Enhancements 1.0. Matt Garrish. W3C. 10 August 2022. W3C Working Group Note. URL: https://www.w3.org/TR/epub-tts-10/
[epubpackages-32]
EPUB Packages 3.2. Matt Garrish; Dave Cramer. EPUB 3 Community Group. 08 May 2019. URL: https://www.w3.org/publishing/epub32/epub-packages.html
[h264]
H.264 : Advanced video coding for generic audiovisual services. 2017-04-13. URL: https://www.itu.int/ITU-T/recommendations/rec.aspx?rec=13189
[indexeddb]
Indexed Database API. Nikunj Mehta; Jonas Sicking; Eliot Graff; Andrei Popescu; Jeremy Orlow; Joshua Bell. W3C. 8 January 2015. W3C Recommendation. URL: https://www.w3.org/TR/IndexedDB/
[rfc6386]
VP8 Data Format and Decoding Guide. J. Bankoski; J. Koleszar; L. Quillio; J. Salonen; P. Wilkins; Y. Xu. IETF. November 2011. Informational. URL: https://www.rfc-editor.org/rfc/rfc6386
[uaag20]
User Agent Accessibility Guidelines (UAAG) 2.0. James Allan; Greg Lowney; Kimberly Patch; Jeanne F Spellman. W3C. 15 December 2015. W3C Working Group Note. URL: https://www.w3.org/TR/UAAG20/
[wai-aria-11]
Accessible Rich Internet Applications (WAI-ARIA) 1.1. Joanmarie Diggs; Shane McCarron; Michael Cooper; Richard Schwerdtfeger; James Craig. W3C. 14 December 2017. W3C Recommendation. URL: https://www.w3.org/TR/wai-aria-1.1/
↑