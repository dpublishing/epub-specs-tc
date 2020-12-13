# EPUB 3.2 變更點
最終社群小組規格 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-changes.html
**編輯**：
    Matt Garrish (DAISY Consortium)
    Dave Cramer (Hachette Book Group)
**協助參與：**
    GitHub w3c/publ-epub-revision
    提出問題
    版本紀錄
    修改要求

Copyright © 1999-2019 International Digital Publishing Forum™ and W3C® (MIT, ERCIM, Keio, Beihang)

<hr />

EPUB是國際數位出版論壇（IDPF, International Digital Publishing Forum）的註冊商標

## 概要

本文件敘述了EPUB® 3規格第二次小型改版的變更點，主要著重於關鍵變更與加筆。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
2. 總覽
3. 規範結構變更
4. EPUB 3.2
4.1 無障礙功能支援
4.2 新的核心媒體類型資源
4.3 澄清外部資源回退
4.4 遠端託管資源
4.5 移除對EPUBCFI連結的支援
4.6 對不支援功能的新定義
5. 包裝3.2
5.1 包裝詮釋資料變更
5.2 連結的詮釋資料紀錄
5.3 不推薦binding元素的使用
6. 內容文件3.2
6.1 HTML與SVG參考去日期
6.2 以CSS參考取代EPUB樣式表
6.3 作者與使用者樣式的優先順序
6.4 移除取代樣式標籤
6.5 准許epub:type的任何值
6.6 澄清對腳本的支援
6.7 不推薦switch元素
6.8 不推薦trigger元素
6.9 澄清epubReadingSystem物件
7. 開放容器格式 (OCF) 3.2
7.1 加密與解壓縮順序
7.2 新壓縮元素
8. 媒體層疊
9. EPUB無障礙功能
10. EPUB規範化段片識別碼
11. 替代樣式標籤
A. 參考資料
A.1 參考性文件

<hr />

## 1. 導論

EPUB是一種供數位出版品交換與遞送使用的格式，基於XML以及網頁標準。一本EPUB出版品可以被看作網頁內容的可靠包裝，用於表現一本數位書、雜誌，或者其他類型的出版品，可以被傳遞供線上或離線使用。

EPUB 3.2是EPUB 3規格的小改版，可以被視為EPUB 3.0.1與EPUB 3.1兩方的後繼。EPUB 3.1並未受到廣泛採納，所以社群小組決定創立EPUB 3.2以更能具備對EPUB 3.0.1的向後支援性，而回復了許多EPUB 3.1中的變更（各版本的EPUB都應該具備對舊版的相容性，唯有在EPUB出版品相容於舊版時，才會相容於新版）。

本文件敘述所有自EPUB 3.0.1的EPUB變革，所以讀者在判斷本版本從EPUB 3.0.1的變化時，可以無需複習EPUB 3.1規格。

本文件為非規範性。請參考EPUB規格以確認EPUB 3的明確資訊。

除非特別指出，此處出現的術語意義定義於[EPUB32]。

## 2. 總覽

多數既存的EPUB 3.0.1檔案應該不需修改就合於EPUB 3.2標準，所以內容作者應該不需要改變他們的工作流程與手續。EPUB 3.2提供了一些選項，並且正式建議內容創作者遵循EPUB無障礙規範。

> ##### 注意事項
> 
> 網頁標準，如HTML、CSS以及SVG的變革可能會改變驗證，所以EPUBCheck也會跟著改變。

EPUB 3.2最大的變革是與核心網頁規格，如HTML、CSS和SVG的關係。過去EPUB僅只向特定日期版本的HTML或CSS。現在EPUB 3.2正式支援由W3C定義最新版本的HTML、CSS和SVG。這些版本會隨著時間進化，可以讓EPUB能夠和網頁一樣保持更新。

另外一項值得注意的變更是WOFF 2.0與SFNT字型為新核心媒體類型資源。EPUB 3.2也不再推薦使用舊的功能，例如：bindings, epub:trigger以及epub:switch。

## 3. 規範結構變更

為了更容易閱讀及參考EPUB標準，我們為標準做了一項明顯的結構變更。最主要的變化就是推出了頂級的EPUB規格作為開始點。EPUB出版品以及閱讀系統的需求之前定義於[Publication301]，現在則移到規格的最頂級，與出版品資源章節放在一起。所有一般術語也集中到頂級規格，同時為了提供常用參考資料，也加入關鍵概念與術語的索引來為多個子規格提供導覽。

[Publication301]改名為EPUB包裝3.2[Package32]更好反應了透過包裝文件對內容解釋的定義。EPUB導覽文件定義則從[ContentDocs301]移到了包裝規格作為包裝的中心元件而並非EPUB內容文件的一般功能。之前定義在本規格中的屬性定義被移出到外部詞彙中。

[MediaOverlays32]的嵌入屬性定義也移到了分開的詞彙表，但結構上沒有改變。

[ContentDocs32]則是除了移除EPUB導覽文件定義外，僅做了修飾性改變。許多章節改名以反映實際上不是特殊文件類型、卻是加強的內容文件而已（例如，「有腳本的內容文件」一章改名為「腳本」），但該章節的內容大多數沒有變更。

[OCF32]同樣只做了小部分的文字與結構清理，沒有添加移除任何章節。

## 4. EPUB 3.2

> ##### 注意事項
> 
> 請參考issue tracker以獲得EPUB 3.2中對EPUB 3.0.1規格的澄清、修正與其他問題。

### 4.1 無障礙功能支援

EPUB 3.1推薦所有的EPUB出版品都能符合新版EPUB無障礙功能規格[EPUBAccessibility]。此項無障礙功能規格推薦包含提供具發現性的詮釋資料，以及內容支援[WCAG20]。

EPUB閱讀系統也推薦符合[EPUBAccessibility]中的需求。

### 4.2 新的核心媒體類型資源

EPUB 3.2將WOFF 2.0與SFNT字型格式納入核心媒體類型資源[EPUB32]。

### 4.3 澄清外部資源回退

EPUB 3.2新增對於外部資源的額外澄清，當他們不出現在書脊也不嵌入於EPUB內容文件時，則無須提供回退。

這項變革讓作者可以加入資料檔案供腳本使用而不需提供非必要的回退，以及其他優點。

### 4.4 遠端託管資源

EPUB 3.2讓可以透過腳本存取外於EPUB容器，託管在網路上的字型與資源。

### 4.5 移除對EPUBCFI連結的支援

EPUB 3.2移除要求閱讀系統對於EPUB規格化段片識別碼[EPUB-CFI]對超連結的支援要求（即為EPUB 3.0.1 EPUBCFI要求）。

### 4.6 對不支援功能的新定義

EPUB 3.2更新了對「不支援」的定義，移除「替代（superseded）」詞彙，並且添加「遺存（legacy）」功能的概念，目的僅為了向後相容性。

## 5. 包裝3.2

> ##### 注意事項
> 
> 請參考issue tracker以獲得EPUB 3.2中對EPUB包裝規格的澄清、修正與其他問題的完整清單。

### 5.1 包裝詮釋資料變更

EPUB 3.2對包裝詮釋資料做出以下變更：

- 不支援rendition:spread屬性的portrait值。
- 不支援rendition:viewport屬性。
- 不支援meta-auth屬性。
- display-seq屬性不再適用。顯示順序現在追隨文件順序。
- 新增與dc:subject元素一起使用的authority和term屬性。
- 現在所有為link元素的特化詮釋資料紀錄關聯不再支援（marc21xml-record, mods-record, onix-record, 與 xmp-signature)。推薦使用一般紀錄關聯。屬性的性質也加到link元素，以協助識別紀錄類型，而不使用獨特的媒體類別。
- 新增alternate, acquire與voicing連結關聯。
- 外部詮釋資料與會被重新整合到規格中作為附錄。
- epubsc （作為可腳本元件）不再是反向字首。

### 5.2 連結的詮釋資料紀錄

EPUB 3.2也改變了對於連結技術的處理順序，在優先處理連結記錄中的書籍資訊，勝於直接包含在包裝文件metadata元素中的資訊。

> ##### 注意事項
> 
> 在最新的草稿的附錄中，正在開發一項取得遠端紀錄的協定。該項作業已經移除，並且會在另一份獨立的文件上繼續進行。

### 5.3 不推薦binding元素的使用

EPUB 3.2不推薦在包裝文書中使用bingings來提供嵌入於object元素中的外部資源之替代性腳本化回退（EPUB 3.0.1 bindings)。

[HTML]物件元素原生回退機制（嵌入內容）可用於對核心媒體類型資源提供回退。

## 6. 內容文件3.2

> ##### 注意事項
> 
> 請參考issue tracker以獲得EPUB 3.2中對EPUB內容文件的澄清、修正與其他問題的完整清單。

### 6.1 HTML與SVG參考去日期

EPUB 3.0.1使用具日期的HTML 5.0和SVG 1.1參考，以至於將規格綁緊在這些特定的版本上。依照此模型，當新版HTML或者SVG發布時，都需要隨之改版。

為了確保EPUB 3.2可以跟隨這些規格的最新推薦版本更新，EPUB 3.2中具日期的參考資料被去日期的參考資料所取代。這項變革意味著當新推薦版本的HTML與SVG發布時，EPUB出版品就立即可使用。

這項變得的結果使得，SVG中animation元素和事件的使用限制被移除，但作者在使用這些SVG尚未完整支援的功能時，得要多加注意。

想要知道更多資訊，請看與HTML的關係，和與SVG的關係。

### 6.2 以CSS參考取代EPUB樣式表

EPUB 3.2移除了EPUB樣式表規格。取而代之定義了更多一般CSS的支援需求：

- 視覺性的閱讀系統得支援CSS。
- 取代CSS規格，EPUB 3.2使用「官方定義」的CSS，來自CSS工作組快照文件。
- 移除對position: absolute的使用限制。
- 所有來自CSS Speech的-epub字首屬性都移除，因為缺少實作。
- 移除-epub-ruby-position屬性。
- 移除-epub-text-combine-horizontal屬性。
- 移除-epub-fullsize-kana屬性。
- 移除-epub-text-emphasis簡寫屬性。
- 移除-epub-text-orientation中use-glyph-orientation與sideways-left兩值。
- 移除顯示屬性中oeb-page-head與oeb-page-foot兩值。在EPUB 3.0.1中已不再推薦。

> ##### 注意事項
> 
> 限制於EPUB出版品中使用樣式表，並非EPUB的角色定位。CSS有著完整定義的錯誤處理，以及許多技巧（如@supports和層疊）都可以讓作者活動更新的CSS功能同時確保合理的回退行為。

### 6.3 作者與使用者樣式的優先順序

EPUB 3.2新增了對閱讀系統的指南，應該優先使用作者或使用者選擇的樣式，而非閱讀器自己的樣式，這樣需求透過覆蓋樣式達成，列於閱讀系統適用性需求的子章節中。

### 6.4 移除取代樣式標籤

EPUB 3.2不再指出替代樣式標籤，由於這項機制使用class屬性，所以不會影響到既有內容的合規性。

### 6.5 准許epub:type的任何值

EPUB 3.2接受沒有字首的值，就算不屬於EPUB結構語意詞彙[EPUB-SSV]也能使用在epub:type屬性中。

### 6.6 澄清對腳本的支援

EPUB 3.2對於腳本支援作出以下變革：

- 容器內的腳本將限制使用於[HTML]iframe元素（移除embed與object）。
- 閱讀程式應該支援容器內的腳本（從「必需」降階，主要因為腳本造成的安全與隱私考量）。
- 閱讀系統應該支援固定版面文件在書脊層級的腳本，以及定義在rendition:flow屬性中的「scrolled-doc」、「scrolled-continuous」介面顯示。

### 6.7 不推薦switch元素

EPUB 3.2不再推薦使用switch元素來對內容做顯示控制（EPUB 3.0.1 switch元素）

### 6.8 不推薦trigger元素

EPUB 3.2不再推薦包含trigger元素來對聲音與影片內容進行宣告式控制（EPUB 3.0.1 trigger元素）

作者推薦使用[HTML]聲音與影片元素的原生控制。

### 6.9 澄清epubReadingSystem物件

epubReadingSystem物件新增了一項IDL定義。

也澄清了該物件於不同腳本脈絡，包括巢狀脈絡中的需求。

## 7. 開放容器格式 (OCF) 3.2

> ##### 注意事項
> 
> 請參考issue tracker以獲得EPUB 3.2中對OCF規格的澄清、修正與其他問題的完整清單。

### 7.1 加密與解壓縮順序

澄清了加密與解壓縮的順序。新規則澄清當無法有效減少資源大小時，壓縮則為非必要。

### 7.2 新壓縮元素

新的Compression元素加入encryption.xml模式用以指出一項資源是否被壓縮，以及提供原來的位元尺寸。

## 8. 媒體層疊

> ##### 注意事項
> 
> 請參考issue tracker以獲得EPUB 3.2中對媒體層疊規格的澄清、修正與其他問題的完整清單。

本次改版中，媒體層疊規格沒有大幅修正。

## 9. EPUB無障礙功能

EPUB 3.2改版提出了[EPUBAccessibility]規格，敘述了如何讓EPUB出版品具無障礙輔助性並且易於被發現的細節。這項規格受到[WCAG20]的影響也添加EPUB出版品的需求。同時伴隨著參考性文件[EPUBAccessibilityTechniques]解釋達到需求的最佳實踐。

本規格設計適用於舊版EPUB。作者可以立即用來檢查所製作的EPUB 3.0.1或2.0.1出版品是否符合無障礙需求。

## 10. EPUB規範化斷片識別碼

EPUB規範化斷片識別碼規格從EPUB 3.2起不再作為參考。閱讀程式的支援改為選擇性。

## 11. 替代樣式標籤

替代樣式標籤規格從EPUB 3.2起不再作為參考。閱讀程式的支援改為選擇性。

## A. 參考資料

### A.1 參考性文件

#### [ContentDocs301]

   [EPUB Content Documents 3.0.1](http://www.idpf.org/epub/301/spec/epub-contentdocs.html). URL: http://www.idpf.org/epub/301/spec/epub-contentdocs.html
   
#### [ContentDocs32]

   [EPUB Content Documents 3.2](https://www.w3.org/publishing/epub3/epub-contentdocs.html). URL: epub-contentdocs.html
   
#### [EPUB-CFI]

   [EPUB Canonical Fragment Identifier (epubcfi) Specification](http://www.idpf.org/epub/linking/cfi/epub-cfi.html). URL: http://www.idpf.org/epub/linking/cfi/epub-cfi.html
   
#### [EPUB-SSV]

   [EPUB Structural Semantics Vocabulary](http://www.idpf.org/epub/vocab/structure/). IDPF. URL: http://www.idpf.org/epub/vocab/structure/

#### [EPUB32]

   [EPUB 3.2](https://www.w3.org/publishing/epub3/epub-spec.html). URL: epub-spec.html

#### [EPUBAccessibility]

   [EPUB Accessibility](http://www.idpf.org/epub/latest/accessibility). URL: http://www.idpf.org/epub/latest/accessibility

#### [EPUBAccessibilityTechniques]

   [EPUB Accessibility Techniques](http://www.idpf.org/epub/latest/accessibility/techniques). URL: http://www.idpf.org/epub/latest/accessibility/techniques

#### [HTML]

   [HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [MediaOverlays32]

   [EPUB Media Overlays 3.2](https://www.w3.org/publishing/epub3/epub-mediaoverlays.html). URL: epub-mediaoverlays.html

#### [OCF32]

   [Open Container Format (OCF) 3.2](https://www.w3.org/publishing/epub3/epub-ocf.html). URL: epub-ocf.html

#### [Packages32]

   [EPUB Packages 3.2](https://www.w3.org/publishing/epub3/epub-packages.html). URL: epub-packages.html

#### [Publications301]

   [EPUB Publications 3.0.1](http://www.idpf.org/epub/301/spec/epub-publications.html). URL: http://www.idpf.org/epub/301/spec/epub-publications.html

#### [WCAG20]

   [Web Content Accessibility Guidelines (WCAG) 2.0](https://www.w3.org/TR/WCAG20/). Ben Caldwell; Michael Cooper; Loretta Guarino Reid; Gregg Vanderheiden et al. W3C. 11 December 2008. W3C Recommendation. URL: https://www.w3.org/TR/WCAG20/
