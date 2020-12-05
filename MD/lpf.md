# 輕量包裝格式（Lightweight Packaging Format,LPF）
W3C工作小組備忘 19 March 2020

**本版本：**
    https://www.w3.org/TR/2020/NOTE-lpf-20200319/
**最新發佈版本：**
    https://www.w3.org/TR/lpf/
**前版本：**
    https://www.w3.org/TR/2019/NOTE-lpf-20191205/
**最新編輯草稿：**
    https://w3c.github.io/lpf/
**編輯：**
    Laurent Le Meur (EDRLab)
**協助參與：**
    GitHub w3c/lpf
    提出問題
    版本紀錄
    修改要求

Copyright © 2019-2020 W3C® (MIT, ERCIM, Keio, Beihang). 適用於W3C之責任、商標以及許可之文件授權規則。

<hr />

## 概要

本章節為非規範性。

本規格定義了一個檔案格式與處理模型以包裝成單一檔案容器，含納一組關聯的資源以及相關的詮釋資料以組成一本數位出版品。

## 本文件狀態

本章解釋了本文件在其發布時的狀態。其他文件可以取代本文件。當下W3C出版品清單可於W3C技術報告索引下進行查找https://www.w3.org/TR/。

本文件由出版工作小組發行為工作小組備忘。

推薦使用GitHub Issues對本規格進行討論。此外，你也可以將意見寄送到我們的郵寄列表。請寄送到 public-publ-wg@w3.org （郵件紀錄）。

作為工作小組備忘的出版品不代表受到W3C會員所支持。此為草稿文件並且可能隨時受其他文件更新、取代或者淘汰。除了在工作進程外，不建議摘要本文件。

本文件由W3C專利政策下營運的小組所製作。

小組不預期本文件成為W3C推薦規格。

本文件由2019年3月1日W3C進程文件所管控。

## 目錄

1. 導論
2. 術語
3. 適用性
4. 包裝格式
5. 資源壓縮
6. 檔案與目錄結構
7. 取得出版品宣告
A. application/lpf+zip媒體類別
B. 謝詞
C. 參考資料
C.1 規範性文件
C.2 參考性文件

<br />

## 1. 導論

本章節為非規範性。

數位出版品包裝用於：

- 在不同個人及/或不同組織間交換進行中的包裝化出版品；
- 從出版社或者轉換公司提供完成的包裝出版品到不同的配送或者銷售管道；以及
- 提供包裝化出版品給使用者或者使用者代理。

本規格基於已受驗證的技術且允許數位出版品能被以簡單的方式包裝，所以使用術語「輕量」於其名稱。

## 2. 術語

本章節為非規範性。

本文件使用的術語定義於W3C備忘「Web上的出版與連結」[publishing-linking]，尤其包含了使用者與使用者代理。

此外，以下術語定義專供本規格所使用：

**編碼內容類型（Codec content types）**
    內容類型其擁有明確的二進位格式特質，例如影片及聲音媒體類型其已經設計供壓縮最佳化，或者其提供最佳化的串流相容性。

**非編碼內容類型（Non-Codec content types）**
    內容類型因其內在資料結構而能受益於壓縮，例如檔案格式基於字元字串（例如HTML、CSS等。）。

**包裝（Package）**
    單一檔案容器供一組構成的資源以及相關的詮釋資料以組成一份數位出版品。

**主要進入頁面（Primary Entry Page）**
    數位出版品所偏好的開始資源，在某些案例中可用於發現其出版品宣告。

**數位出版品（Digital Publication）**
    一組構成的資源與相關的詮釋資料，被組織在一起為一可獨特識別的群組。

**出版品宣告（Publication Manifest）**
    如定義在[pub-manifest]中，採[JSON-LD]的數位出版品表述。

**根目錄（Root Directory）**
    包裝檔案系統的基礎目錄。

每一章節術語僅在第一次出現時，連結到其定義。

## 3. 適用性

本章節為非規範性。

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、應該（SHOULD）**應該以BCP 14 [RFC2119] [RFC8174]之記述解釋，同時也僅於在出現時以全大寫（中文為粗體）顯示。

## 4. 包裝格式

本章節為非規範性。

為了將一組構成的資源與相關的詮釋資料組成數位出版品，本規格採用ZIP格式，其定義在ISO/IEC 21320-1:2015 ([ISO21320] 與 [zip])中。

## 5. 資源壓縮

本章節為非規範性。

當儲存於包裝中，非編碼內容類型的資源**應該**被壓縮並且**必須**使用Deflate壓縮演算法。這項實踐確保檔案實體能在包裝中以較小的尺寸存放。

編碼內容類型資源**應該**以無壓縮的方式儲存。在這狀況下，壓縮會在製作時產生不必要的處理（尤其對大型資源檔案而言）並且可能會在消費內容時影響聲音/影片的播放表現。

> ##### 注意事項
> 
> 在某些狀況下，以某些加密綱要進行壓縮組合時可能會阻礙使用者代理的處理部分內容要求（例如，HTTP位元組範圍）的能力，由於在技術上難以在媒體播放前確認整個資源的長度（例如，HTTP內容長度標頭）。

## 6. 檔案與目錄結構

本章節為非規範性。

包裝**必需**在其根目錄中包含至少一個以下檔案：

- 名為*publication.json*的檔案，其**必需**為定義供出版品宣告使用的格式。
- 名為*index.html*的檔案，其**必需**按照數位出版品主要進入頁面的需求。

根目錄在性質上為虛擬：使用者代理在內容未包裝時，可以或不可產生物理根目錄供包裝中的內容。

這兩個檔案的內容**不得**被加密。

包裝**必需**也包含所有在數位出版品邊界中的資源，例如，在出版品宣告的預設閱讀順序以及資源清單中的資源集合所能取得的有限資源集。

這些資源檔案**可以**置放在根目錄下的任何子資料夾位置，或者放在根目錄中。

包裝中的內容**必需**透過相對URL字串[url]以參照到這些內容。

> ##### 注意事項
> 
> [zip]規格對允許使用的檔案與資料夾名稱字元有一些限制。當使用這些名稱時，作者必須小心使用這些字元，使在跨作業系統時能得到廣泛的互通性。

## 7. 取得出版品宣告

本章節為非規範性。

當包裝在其根目錄中包含*publication.json*檔案時，出版品宣告可於開啟及分析該檔案時取得。

除此之外，當包裝在其根目錄中包含*index.html*檔案時，出版品宣告可透過以下步驟取得：

1. 由包裝中解壓縮*index.html*檔案時，讓*document*作為其結果。
2. 如果其媒體類型並非*text/html*或*application/xhtml+xml*時，結束該演算法。
3. 讓*document*中，其*rel*屬性包含*publication*標記的manifest link作為樹狀順序的第一個*link*元素。
4. 如果manifest link為*null*，結束該演算法。
5. 如果manifest link的*href*屬性的值為空白字串，結束該演算法。
6. 如果manifest link的*href*屬性值有非空白的斷片可識別*document*中的識別碼id時：
    1. 讓embedded manifest script為樹狀順序中第一個*script*元素，其*id*屬性等同於id，及其*type*屬性等同於*application/ld+json*。
    2. 如果embedded manifest script為*null*，結束該演算法。
    3. 讓manifest text作為embedded manifest script的子文字內容。

> ###### 解釋
> 
> 此分支用於當宣告嵌入在主要進入頁面時。該演算法確認*script*元素的位置並且取出宣告。

7. 此外：
    1. 讓manifest URL作為*href*屬性的值。
    2. 如果manifest URL不是一個相對URL字串，就中止這些步驟。
    3. 透過manifest URL從包裝中將宣告取出。
    4. 開啟並且讀取宣告檔案，讓manifest text作為結果。

> ###### 解釋
> 
> 此分之用於當宣告在分隔的檔案時。其展示了標準程序以從包裝中取得宣告。

如果*index.html*與*publication.json*兩者都在包裝中存在，那麼主要進入頁面**應該**包含對*publication.json*檔案之參照，遵從定義在本章節中的規則。

> ###### 範例 1
> 
> 這裡是一份出版品宣告，其位置位於根目錄，簡單地在主要進入頁面中透過[HTML] *link*元素參照。
> 
> <link href="publication.json" rel="publication"/>
> 
> 主要進入頁面中嵌入出版品宣告的範例在[audiobooks]中提供。

## A. application/lpf+zip媒體類別

本章節為非規範性。

本附錄註冊了*application/lpf+zip*媒體類型供輕量包裝格式使用。

輕量包裝格式（Lightweight Packaging Format, LPF）為一個容器技術其基於[zip]封存格式，用於將一組關聯的資源以及相關的詮釋資料包裝為單一檔案容器以組成數位出版品。LPF以其相關標準由W3C所維護並且定義。

**MIME媒體類型名稱：** 
    *application*

**MIME子類型名稱：**
    *lpf+zip*

**必要參數：**
    無。

**選擇性參數：**
    無。

**編碼考量：**
    LPF檔案為ZIP格式的二進位檔案。 

**安全性考量：**
    適用於*application/zip*的安全性考量也適用於LPF檔案。例如，一個可能包含壓縮檔案的封存檔可能在硬碟上擴張填滿所有可用的磁碟空間。結果上，可以讀取LPF檔案的使用者代理應該嚴密地檢查所取得的資料的尺寸以及合規性。
    此外，由於各種內容類型都可能嵌入於LPF檔案，application/lpf+zip可以視為內容會帶來安全問題，例如，在包裝中包含了刻意的惡意執行內容。然而在這些案例中只會發生於使用者代理辨識並且處理額外內容，或者在內容進一步交付給其他使用者代理處理時，這都會引起潛在的安全問題。在這些案例中，安全考量落於本註冊文件領域之外。

**互通性考量：**
    任何基於LPF的格式，當使用內容加密時，**必需**選擇不同於本規格定義之MIME媒體類型與副檔名。
 
**已發表規格：**
    本媒體類型註冊供輕量包裝格式（Lightweight Packaging Format, LPF）使用，如輕量包裝格式規格所敘述，位於*https://www.w3.org/TR/lpf*。

**使用該媒體類型的應用程式：**
    本媒體類型目的用於多重互通應用程式，供電子書、有聲書、數位視覺旁白與其他類型之數位出版品之配送與消費使用。 

**額外資訊：**
    **魔術數字：**
        *0: PK 0x03 0x04*
    **副檔名：**
        LPF容器檔案多半可透過副檔名.lpf進行識別。
    **麥金塔檔案類型代碼：**
        ZIP
    **斷片識別碼：**
        無

**進一步資訊的聯絡人與郵件位址：**
    Ivan Herman (ivan@w3.org)

**預計用途：**
    COMMON

**作者/變更管控**
    發布的規格是World Wide Web Consortium之出版工作小組的成果產品。W3C對本規格有變更的管控權。

## B. 謝詞

本章節為非規範性。

編輯對出版工作小組的成員對本規格的貢獻致謝：

Greg Albers (J. Paul Getty Trust) Franco Alvarado (Macmillan Learning) Boris Anthony (The Rebus Foundation) Luc Audrain (Hachette Livre) Baldur Bjarnason (The Rebus Foundation) Laura Brady (W3C Invited Expert) Steve Breault (Scenarex Inc.) Don Brutzman (Web3D Consortium) Kaylin Bugbee (Earth Science Data Systems Program) Yu-Wei Chang (Taiwan Digital Publishing Forum) Fred Chasen (W3C Invited Expert) Timothy Cole (University of Illinois at Urbana-Champaign) Simon Collinson (Rakuten, Inc.) Rachel Comerford (Macmillan Learning) Garth Conboy (Google, Inc., chair) Juan Corona (Evident Point Software) Christopher Cosner (Stanford University) Dave Cramer (Hachette Livre) Greg Davis (Pearson plc) Romain Deltour (DAISY Consortium) Marisa DeMeglio (DAISY Consortium) Vagner Diniz (NIC.br - Brazilian Network Information Center) Kenneth Dougherty (Pearson plc) Brady Duga (Google, Inc.) Ben Dugas (Rakuten, Inc.) Roger Espinosa (University of Michigan) Reinaldo Ferraz (NIC.br - Brazilian Network Information Center) Teenya Franklin (Pearson plc) Jun Gamo (Voyager Japan, Inc.) Matt Garrish (DAISY Consortium) Michael Goodman (Wiley) Markku Hakkinen (Educational Testing Service) Katie Haritos-Shea (Knowbility) Ivan Herman (W3C Staff) Geoff Jukes (Blackstone Audio, Inc.) Deborah Kaplan (W3C Invited Expert) Bill Kasdorf (Book Industry Study Group) George Kerscher (DAISY Consortium) Yuri Khramov (Evident Point Software) Masakazu Kitahara (Voyager Japan, Inc.) Toshiaki Koike (Voyager Japan, Inc.) Charles LaPierre (Benetech) Mustapha Lazrek (Microsoft Corporation) Vladimir Levantovsky (Monotype) Mia Lipner (Pearson plc) Phil Madans (Hachette Livre) Christopher Maden (University of Illinois at Urbana-Champaign) Dmitry Markushevich (Evident Point Software) keith mcfarland (Blackstone Audio, Inc.) Jonathan McGlone (University of Michigan) Hugh McGuire (The Rebus Foundation) Nellie McKesson (W3C Invited Expert) Selma Morais (NIC.br - Brazilian Network Information Center) Jasmine Mulliken (Stanford University) Cristina Mussinelli (Fondazione LIA) Christos Nikolakakos (Wiley) Gregorio Pellegrino (Fondazione LIA) Fernando Pinto da Silva (EDRLab) Nicholas Polys (Web3D Consortium) Chris Powell (University of Michigan) Jeff Printy (Macmillan Learning) Ryan Pugatch (Hachette Livre) Joshua Pyle (Wiley) Wendy Reid (Rakuten, Inc., chair) Florian Rivoal (W3C Invited Expert) Leonard Rosenthol (Adobe) Robert Sanderson (J. Paul Getty Trust) Jodi Schneider (University of Illinois at Urbana-Champaign) Ben Schroeter (Pearson plc) Tzviya Siegman (Wiley, chair) Avneesh Singh (DAISY Consortium) Adam Sisco (Earth Science Data Systems Program) David Stroup (Pearson plc) Mateus Teixeira (W. W. Norton & Company) Jonathan Thurston (Pearson plc) Yukio Tomikura (Kodansha, Publishers, Ltd.) Ben Walters (Microsoft Corporation) Daniel Weck (EDRLab, DAISY Consortium) John Weise (University of Michigan) Jason White (Educational Testing Service) Richard Wright (EDRLab) Jeff Xu (Rakuten, Inc.) Evan Yamanishi (W. W. Norton & Company) Maurice York (University of Michigan) Junichi Yoshii (Kodansha, Publishers, Ltd.) Benjamin Young (Wiley) Mohamed ZERGAOUI (INNOVIMAX)

## C. 參考資料

### C.1 規範性文件

**[RFC2119]**
    [Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

**[RFC8174]**
    [Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words](https://tools.ietf.org/html/rfc8174). B. Leiba. IETF. May 2017. Best Current Practice. URL: https://tools.ietf.org/html/rfc8174

### C.2 參考性文件

**[audiobooks]**
    [Audiobooks](https://www.w3.org/TR/audiobooks/). Wendy Reid; Matt Garrish. W3C. 28 January 2020. W3C Candidate Recommendation. URL: https://www.w3.org/TR/audiobooks/

**[dom]**
    [DOM Standard](https://dom.spec.whatwg.org/). Anne van Kesteren. WHATWG. Living Standard. URL: https://dom.spec.whatwg.org/

**[HTML]**
    [HTML Standard](https://html.spec.whatwg.org/multipage/). Anne van Kesteren; Domenic Denicola; Ian Hickson; Philip Jägenstedt; Simon Pieters. WHATWG. Living Standard. URL: https://html.spec.whatwg.org/multipage/

**[ISO21320]**
    [Document Container File - ISO/IEC 21320](https://www.iso.org/standard/60101.html). ISO. 2015. International Standard. URL: https://www.iso.org/standard/60101.html

**[JSON-LD]**
    [JSON-LD 1.0](https://www.w3.org/TR/json-ld/). Manu Sporny; Gregg Kellogg; Markus Lanthaler. W3C. 16 January 2014. W3C Recommendation. URL: https://www.w3.org/TR/json-ld/

**[pub-manifest]**
    [Publication Manifest](https://www.w3.org/TR/pub-manifest/). Matt Garrish; Ivan Herman. W3C. 28 January 2020. W3C Candidate Recommendation. URL: https://www.w3.org/TR/pub-manifest/

**[publishing-linking]**
    [Publishing and Linking on the Web](https://www.w3.org/TR/publishing-linking/). Ashok Malhotra; Larry Masinter; Jeni Tennison; Daniel Appelquist. W3C. 30 April 2013. W3C Note. URL: https://www.w3.org/TR/publishing-linking/

**[url]**
    [URL Standard](https://url.spec.whatwg.org/). Anne van Kesteren. WHATWG. Living Standard. URL: https://url.spec.whatwg.org/

**[zip]**
    [.ZIP File Format Specification](https://www.pkware.com/documents/casestudies/APPNOTE.TXT). 1 September 2012. Final. URL: https://www.pkware.com/documents/casestudies/APPNOTE.TXT