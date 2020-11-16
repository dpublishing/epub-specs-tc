# EPUB開放容器格式（Open Container Format, OCF) 3.2
社群小組規範完整版 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-ocf.html
**編輯**：
    Garth Conboy (Google)
**前任編輯**：
    James Pritchett (Learning Ally)
    Markus Gylling (International Digital Publishing Forum (IDPF))
**協助參與：**
    GitHub w3c/publ-epub-revision
    提出問題
    版本紀錄
    修改要求

Copyright © 1999-2019 International Digital Publishing Forum™ and W3C® (MIT, ERCIM, Keio, Beihang)

<hr />

EPUB是國際數位出版論壇（IDPF, International Digital Publishing Forum）的註冊商標

## 概要

本規格定義了一個檔案格式與處理模型，以包裝一組相關聯的資源以組成一本EPUB出版品為一個單一檔案容器，即為EPUB容器。

本規格定義了規則供建構抽象（即為「抽象容器（abstract container）」）的檔案集合，以及規則此抽象容器於ZIP封存檔（即為「ZIP容器」）的呈現。供ZIP容器的規則建構在由[ODF]所使用的ZIP技術。OCF也定義了一套標準方式供模糊的嵌入資源，例如字體，以提供需要這些功能的EPUB出版品使用。

本規格屬於組成[EPUB32]的規格群之一，其為基於XML與Web標準的數位出版品交換與遞送格式。要了解整體EPUB 3規格，需要與其他規格一併閱讀且理解。

可參考[EPUB32Changes]以了解本規格與其前版本的差異資訊。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
1.1 術語
1.2 適用性
2. OCF適用性
2.1 容器適用性
2.2 閱讀系統適用性
3. OCF抽象容器
3.1 導論
3.2 檔案與目錄結構
3.3 參照其他元件時相關的IRI
3.4 檔案名稱
3.5 META-INF目錄
3.5.1 包容性
3.5.2 保留的檔案
3.5.2.1 容器檔案 (container.xml)
3.5.2.2 加密檔案 (encryption.xml)
3.5.2.2.1 壓縮與解壓順序
3.5.2.3 宣告檔案 (manifest.xml)
3.5.2.4 詮釋資料檔案 (metadata.xml)
3.5.2.5 權利管理檔案 (rights.xml)
3.5.2.6 數位簽章檔案 (signatures.xml)
4. OCF ZIP容器
4.1 導論
4.2 ZIP檔案需求
4.3 OCF ZIP容器媒體類型識別
5. 資源模糊化
5.1 導論
5.2 模糊化密鑰
5.3 模糊化演算法
5.4 指定模糊化資源
A. 綱要（Schemas）
A.1 供container.xml使用的綱要
A.2 供encryption.xml使用的綱要
A.3 供signatures.xml使用的綱要
B. 範例
C. application/epub+zip 媒體類型
D. 謝詞與貢獻者
E. 參考資料
E.1 規範性文件
E.2 參考性文件

<br />

## 1. 導論

### 1.1 術語

專屬於EPUB 3的術語在本文件中以括號（譯注：英文版為首字大寫。範例如「作者」，「閱讀系統」）。術語與定義的完整清單提供於[EPUB32]。

每章節術語第一次出現時才會連結至其定義。

此外，以下術語專為本規格所定義使用：

**編碼（*Codec*）**
    編碼用於具備固有二進位格式特性的內容，例如影片或者聲音媒體類型等已經預供壓縮最佳化設計，或者能提供最佳化的串流相容性。

**預設內容解釋（*Default Rendition*）**
    列於container.xml檔案中的第一個*rootfile*元素中的預設內容。

**檔案名稱（*File Name*）**
    在OCF抽象容器中任何種類檔案的名稱，不管是檔案夾或者在檔案夾中的檔案。

**非編碼（*Non-Codec*）**
    非編碼用於其內在檔案結構性質能夠得益於壓縮的內容類型，例如基於文字字串的檔案格式（例如，HTML、CSS等）。

**OCF抽象容器（*OCF Abstract Container*）**
    OCF抽象容器定義了一個檔案系統模型供OCF ZIP容器的內容，如OCF抽象容器所定義。

**OCF處理器（*OCF Processor*）**
    一個軟體應用程式用於處理OCF ZIP容器，符合本規格中的需求。

**OCF ZIP容器（*OCF ZIP Container*）**
    基於ZIP技術的EPUB出版品包裝與遞送格式，定義於OCF ZIP容器。
    OCF ZIP容器與EPUB容器為同義詞。

**路徑名稱（*Path Name*）**
    在OCF抽象容器中所給予的檔案夾，該字串包含以完整路徑顯示的所有檔案夾及檔案名稱，以一個/ (U+002F)字元結合起，並分隔檔案夾與檔案名稱。
    在OCF抽象容器中所給予的檔案，其路徑名稱為一個字串包含所有檔案夾及檔案名稱，使用一個/字元分隔檔案夾與檔案名稱，後接/字元以及檔案的檔案名稱。

**根目錄（*Root Directory*）**
    根目錄表示OCF抽象容器檔案系統的基礎。其檔案夾性質為虛擬：當內容尚未解壓縮時，一個EPUB閱讀系統可或不可產生一個供OCF抽象容器內容的物理根目錄。

### 1.2 適用性

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、不得（MUST NOT）、推薦（RECOMMENDED）、應該（SHOULD）、不應（SHOULD NOT）**應該以[RFC2119]之記述解釋。

## 2. OCF適用性

### 2.1 容器適用性

- 一個OCF抽象容器**必需**符合定義於OCF抽象容器中的適用性限制。
- 一個OCF ZIP容器**必需**符合定義在OCF ZIP容器中的適用性限制。

### 2.2 閱讀系統適用性

一個EPUB閱讀系統**必需**滿足以下領域需求：

- 其**必需**符合OCF ZIP容器中所有對閱讀程式的適用性限制來處理OCF ZIP容器。
- 如果有Viewport時，其**必需**按照資源模糊化之定義來支援資源的去模糊化。

## 3. OCF抽象容器

### 3.1 導論

本章節為非規範性。

OCF抽象容器檔案系統模型使用單一通用根目錄置放所有內容。所有供EPUB出版品使用的本地資源都放在由根目錄所開頭的目錄樹中，本規格中不對資源做檔案系統結構的指定。

此檔案系統模型也包含一個必須的資料夾名為META-INF，為根目錄下直接子目錄，用於置放以下特別檔案：

*container.xml [必需]*
    識別定義該EPUB出版品中每個內容解釋的包裝文件位置。

*signatures.xml [選擇性]*
    包含供各種用途的數位簽章。

*encryption.xml [選擇性]*
    包含關於出版品資源加密的資訊。當使用模糊化時本檔案為必要。

*metadata.xml [選擇性]*
    用於儲存OCF ZIP容器的詮釋資料。

*rights.xml [選擇性]*
    用於儲存關於數位權利的資訊。

*manifest.xml [選擇性]*
    一份容器內容的宣告，開放文件格式[ODF]允許使用。

在META-INF資料夾中各檔案的適用性需求定義於META-INF目錄。

### 3.2 檔案與目錄結構

供OCF抽象容器使用的虛擬檔案系統**必需**有單一通用的根目錄置放容器中的所有內容。

OCF抽象容器**必需**有單一通用根目錄置放容器中的所有內容。

OCF抽象容器**必需**包含一個名為META-INF的目錄，作為容器根目錄的直接子目錄。對該資料夾中內容的需求在META-INF目錄中說明。

根目錄中mimetype檔案名稱保存供OCF ZIP容器使用，將於OCF ZIP容器中說明。

所有其他在OCF抽象容器中的檔案可以放置於根目錄以下的所有階層位置，但不能置放在META-INF資料夾中。

### 3.3 參照其他元件時相關的IRI

在OCF抽象容器中的檔案**必需**透過相關IRI位置相互參照 ([RFC3987]和[RFC3986])。

> ###### 範例 1
> 
> 以下範例呈現一個名為*image1.jpg*的檔案，與XHTML內容文件放在同一資料夾，如何透過一個[HTML] *img*元素參照。
> 
> <img src="image1.jpg" alt="…" />

對相關IRI位置，基礎IRI[RFC3986]由其給予的檔案格式之相關的語言規格所定義。例如，CSS的相關IRI位置如何運作，定義於CSS樣式表以及特性宣告[CSSSnapshot]之脈絡。

> ##### 注意事項
>
> 有些語言規格參考早於[RFC3987]的IETF意見需求[RFC]（Requests For comments），在這些案例中，特殊語言套用較早的意見需求於內容上。

不像大多數的語言規格，所有在META-INF資料夾中的檔案使用OCF抽象容器的根目錄作為預設的基礎IRI。

舉個例子，如果*META-INF/container.xml*有以下內容：

> ###### 範例2
> 
> <?xml version="1.0"?>
> <container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <rootfiles>
>         <rootfile full-path="EPUB/Great_Expectations.opf"
>             media-type="application/oebps-package+xml" />	
>     </rootfiles>
> </container>

接著*EPUB/Great_Expectations.opf*的路徑相關於該OCF抽象容器的根目錄，不相關於*META-INF*目錄。

所有相關的IRI位置必須解析到位於OCF抽象容器中的資源（例如，位於或者低於根目錄）。

### 3.4 檔案名稱

本章節所說明的檔案名稱限制，設計用於允許路徑名稱與檔案名稱在多數常用的作業系統上無需更動即可使用。本規格不指示OCF處理器在無法表現OCF檔案與路徑名時，如何添補其相容性問題的作法。

在一個OCF抽象容器的脈絡下，檔案與路徑名稱在乎大小寫區分，並且**必需**符合以下領域需求：

- 檔案名稱**必需**為UTF-8[Unicode]編碼。
- 檔案名稱**不得**超過255位元組（bytes）。
- 任何在OCF抽象容器中的資料夾與檔名，其路徑名稱**不得**超過65535位元組。
- 檔案名稱**不得**使用以下[Unicode]字元，因為這些字元可能不會在跨常用作業系統時受到支援：
    - SOLIDUS: */* (*U+002F*)
    - QUOTATION MARK: *"* (*U+0022*)
    - ASTERISK: ** (*U+002A*)
    - FULL STOP as the last character: *.* (*U+002E*)
    - COLON: *:* (*U+003A*)
    - LESS-THAN SIGN: *<* (*U+003C*)
    - GREATER-THAN SIGN: *>* (*U+003E*)
    - QUESTION MARK: *?* (*U+003F*)
    - REVERSE SOLIDUS: *\* (*U+005C*)
    - VERTICAL LINE: *\* (*U+007C*)
    - DEL (*U+007F*)
    - C0 range (*U+0000 … U+001F*)
    - C1 range (*U+0080 … U+009F*)
    - Private Use Area (*U+E000 … U+F8FF*)
    - Non characters in Arabic Presentation Forms-A (U*+FDDO … U+FDEF*)
    - Specials (*U+FFF0 … U+FFFF*)
    - Tags and Variation Selectors Supplement (*U+E0000 … U+E0FFF*)
    - Supplementary Private Use Area-A (*U+F0000 … U+FFFFF*)
    - Supplementary Private Use Area-B (*U+100000 … U+10FFFF*)

- 所有在同一個資料夾中的檔案名稱**必需**在大小寫正規化後皆為獨特，如3.13章節中[Unicode]所解釋。
- 所有在同一個資料夾中的檔案名稱**應該**在NFC或NFD正規化[TR15]後為獨特。

> ##### 注意事項
>
> 有些商用ZIP工具不支援完整Unicode範圍，且可能僅支援[US-ASCII]範圍的檔案名稱。作者若想使用有這些限制的ZIP工具的話，最好盡可能將檔案名稱限制在[US-ASCII]範圍。如果檔案的名稱在解壓縮過程時無法保留，在檔案透過URI被內容所參照時，可能有需要補齊名稱解譯。

### 3.5 META-INF目錄

#### 3.5.1 包容性

所有OCF抽象容器**必需**在其根目錄中包含一個名為*META-INF*的資料夾。

此資料夾包含檔案其為META-INF保留的檔案。其他未列於本章節的檔案**可以**被包含在*META-INF*資料夾中；OCF處理器當遇到這些檔案時**不得**發生問題。

#### 3.5.2 保留的檔案

##### 3.5.2.1 容器檔案 (*container.xml*)

置放於*META-INF*資料夾中**必要的***container.xml*，用於識別在OCF抽象容器中的EPUB包裝。

該檔案的內容**必需**在移除所有來自其他命名空間的元素以及屬性（包含所有屬性以及有這些元素的內容）後，合乎定義在「供container.xml使用的綱要」裡提供的綱要。

每一個*rootfile*元素**必需**指定一份包裝文件的位置，以代表EPUB出版品的一個內容解釋。每一個內容解釋**必需**與其容器的EPUB版本相容。

一個OCF處理器**必需**將在*rootfiles*元素中第一個*rootfile*元素視為所容納的EPUB出版品中的預設內容解釋。閱讀系統**需要**呈現預設內容解釋，但**可以**顯示容器中的其他內容解釋。

> ##### 注意事項
>
> 儘管EPUB容器提供能夠包含多於一個內容解釋之內容的能力，閱讀系統對於多重內容解釋的支援依然未受到廣泛支援，僅有參與的團體為了其目的與手段提供特定的環境支援。

> ###### 範例 3
> 
> 以下範例呈現一個EPUB出版品的*container.xml*範本，其根檔案為*EPUB/My Crazy Life.opf*（包裝文件）
> 
> <?xml version="1.0"?>
> <container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <rootfiles>
>         <rootfile full-path="EPUB/My_Crazy_Life.opf"
>             media-type="application/oebps-package+xml" />
>     </rootfiles>
> </container>

> ###### 範例 4
> 
> 以下範例呈現SVG與XHTML內容解釋包裝於相同的容器中：
> 
> <?xml version="1.0"?>
> <container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <rootfiles>
>         <rootfile full-path="SVG/Sandman.opf"
>             media-type="application/oebps-package+xml" />
>         <rootfile full-path="XHTML/Sandman.opf"
>             media-type="application/oebps-package+xml" />
>     </rootfiles>
> </container>

**選擇性**的*links*元素指定處理OCF ZIP容器時所需要的資源。其每一個*link*元素**必需**包含一個*href*屬性，其值指定了一個資源的位址。每一個*link*元素都**必需**包含一個*rel*屬性其值指定了與資源的關係，以及**可以**包含一個*media-type*屬性，其值**必需**為一個媒體類型[RFC2046]指定了該連結餐找的資源的類型與格式。

> ##### 注意事項
>
> *links*元素用於多重內容解釋EPUB中指出內容解釋所映射的文件。

*rootfile*元素中*full-path*屬性的值與*link*元素的*href*屬性**必需**包含一個路徑部件[RFC3986]其**必需**僅使用path-rootless[RFC3986]形式。其路徑部件對根目錄為相對。

OCF處理器**必需**忽略*container.xml*檔案中的外部元素與屬性。

##### 3.5.2.2 加密檔案 (*encryption.xml*)

在*META-INF*資料夾中選擇性的*encryption.xml*保有所有該容器內容的加密資訊。如果任何在容器中的資源加密，*encryption.xml* **必需**用於指出何資源受到加密以及提供如何解密的資訊。

本檔案是一個XML文件，其根元素為*encryption*。*encryption*元素包含類型子元素*EncryptedKey*及*EncryptedData*由[XMLENC-CORE1]所定義。一個*EncryptedKey*元素解釋了用於容器的每一個加密密鑰，而*EncryptedData*元素解釋了每一個加密檔案。每一個*EncryptedData*元素向一個*EncryptedKey*參照，如在XML加密中所說明。

*encryption.xml*檔案之內容**必需**合乎定義在「供encryption.xml使用的綱要」裡提供的綱要。

OCF獨立地加密個別檔案，以一些安全性交換效能的提升，允許容器內容能夠被遞增解密。以這種方式加密會暴露目錄結構與整個包裝的檔案命名。

OCF使用XML加密[XMLENC-CORE1]以提供一個加密使用的框架，允許使用多種演算法。XML加密指定一個程序供加密任意資料以及以XML表現其結果。儘管一個OCF抽象容器可能包含非XML資料，XML加密可用於加密OCF抽象容器中的所有資料。OCF加密僅支援對在容器中的整體檔案加密，而非部份檔案。*encryption.xml*檔案若存在，則**不得**被加密。

在OCF抽象容器中，以加密資料置換未加密的資料。例如，如果一個名為*photo.jpeg*的影像為加密，*photo.jpeg*資源的內容**應該**被置換成其加密後的內容。在ZIP資料夾中，**應該**儲存加密後的檔案而非Deflate壓縮檔。

請注意在一些狀況下，需要模糊儲存被內容解釋參照的嵌入資源，以連接到「母」EPUB出版品並且使他們更難以在非限制的使用下解壓縮（例如，字體）。儘管模糊化並非加密，*encryption.xml*檔案用於注入資源模糊化演算法以識別哪些資源需要在使用前去模糊化。

以下檔案**不得**被加密，無論是以預設或者呼叫特別的加密法：

- *mimetype*
- *META-INF/container.xml*
- *META-INF/encryption.xml*
- *META-INF/manifest.xml*
- *META-INF/metadata.xml*
- *META-INF/rights.xml*
- *META-INF/signatures.xml*
- *包裝文件*

簽署的資源**可以**之後使用供XML簽章[XMLENC-DECRYPT]的解密變形法（Decryption Transform）加密。這項功能使應用程式，例如一個OCF客戶端在從檔案簽署前來辨別資料是否加密。只有在簽署後為加密的檔案**必需**要在計算其摘要用於查核簽名前解壓縮。

> ###### 範例 5
> 
> 以下範例採用2.2.1節中之[XMLENC-CORE1]，資源*image.jpeg*使用對稱密鑰加密（AES）加密，其對稱密鑰更近一步使用非對稱密鑰加密（RSA）加密，其密鑰由John Smith持有。
> 
> <encryption
>     xmlns ="urn:oasis:names:tc:opendocument:xmlns:container"
>     xmlns:enc="http://www.w3.org/2001/04/xmlenc#"
>     xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
>     <enc:EncryptedKey Id="EK">
>         <enc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-1_5"/>
>         <ds:KeyInfo>
>             <ds:KeyName>John Smith</ds:KeyName>
>         </ds:KeyInfo>
>         <enc:CipherData>
>             <enc:CipherValue>xyzabc</enc:CipherValue>
>         </enc:CipherData>
>     </enc:EncryptedKey>
>     <enc:EncryptedData Id="ED1">
>         <enc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
>         <ds:KeyInfo>
>             <ds:RetrievalMethod URI="#EK"
>                 Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
>         </ds:KeyInfo>
>         <enc:CipherData>
>             <enc:CipherReference URI="image.jpeg"/>
>         </enc:CipherData>
>     </enc:EncryptedData>
> </encryption>

###### 3.5.2.2.1 壓縮與解壓順序

當儲存在ZIP容器中，有非編碼內容類型的資料流**應該**在加密前壓縮，**必需**使用Deflate壓縮。這種做法可確保存放在ZIP容器中的檔案能夠佔較少的空間。

編碼內容類型的資料得**不應**在加密前壓縮。在這些案例中，額外的壓縮會在製作時產生不必要的處理程序（尤其在處理大型資源檔案時），以及在閱讀時將會影響影音播放效率。在某些案例中，某些加密綱要的組合壓縮可能會降低閱讀系統處理部分內容需求的能力（例如，HTTP位元組範圍byte range），由於技術上無法在媒體播放時判斷完整資源的長度（例如，HTTP內容長度檔頭Content-Length header）。

在加密前壓縮的資料流**應該**提供額外的*EncryptionProperties*詮釋資料來指定初始資源的大小（即為，在壓縮與加密前），如同下列每個*Compression*XML元素所定義。加密前沒受壓縮的資料流**可以**提供額外的*EncryptionProperties*詮釋資料來指定初始資源的大小（即為，加密前）。

> ###### 元素名稱
> 
> *Compression*
>
> ###### 命名空間
> 
> http://www.idpf.org/2016/encryption#compression
> 
> ###### 用法
> 
> *EncryptionProperty*的**選擇性**子元素
> 
> ###### 屬性
> 
> **Method** *[必需]*
>     識別使用的壓縮法。
>     值需為「0」（無壓縮）或「8」（Deflate演算法）。
> 
> **OriginalLength** *[必需]*
>     代表資源初始大小（位元組數）。
>     值為正整數。
> 
> ###### 內容模型
> 
> 空白

> ###### 範例 6
> 
> 以下範例呈現一個MP4檔案經過Deflate壓縮，其原來大小為3500000位元組。
> 
> <encryption xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <enc:EncryptedData xmlns:enc="http://www.w3.org/2001/04/xmlenc#">
>         ...
>         <enc:CipherData>
>             <enc:CipherReference URI="OEPBS/video.mp4"/>
>         </enc:CipherData>
>         <enc:EncryptionProperties>
>             <enc:EncryptionProperty xmlns:ns="http://www.idpf.org/2016/encryption#compression">
>                 <ns:Compression Method="8" OriginalLength="3500000"/>
>             </enc:EncryptionProperty>
>         </enc:EncryptionProperties>
>         ...
>     </enc:EncryptedData>
> </encryption>

##### 3.5.2.3 宣告檔案 (*manifest.xml*)

*META-INF*資料夾裡**選擇性**的*manifest.xml*檔案提供了容器裡對檔案的宣告。

OCF規格不指定宣告的格式。

請注意在包裝文件中的*manifest*元素指定了為一個宣告用於處理該內容解釋。包含在ZIP封存中的額外宣告資訊或者**選擇性**的*manifest.xml***不得**被用於處理內容解釋。

> ##### 注意事項
>
> 本功能僅為了相容於[ODF]續存。

##### 3.5.2.4 詮釋資料檔案 (*metadata.xml*)

*META-INF*資料夾裡**選擇性**的*META-INF/metadata.xml*檔案，若存在，必須用於容器層級的詮釋資料。

如果*metadata.xml*檔案存在，其內容**應該**僅包含命名空間認可的元素[XML-NAMES]。該檔案**應該**包含根元素*metadata*，其命名空間為*http://www.idpf.org/2013/metadata*，但其他根元素允許供反向相容使用。閱讀系統**應該**忽略有無法識別的根元素之*metadata.xml*。 

本版本的OCF規格不定義供*metadata.xml*檔案使用的詮釋資料格式。容器層級的詮釋資料**可能**在本規格的未來版本以及EPUB延伸規格中定義。

##### 3.5.2.5 權利管理檔案 (*rights.xml*)

*META-INF*資料夾裡**選擇性**的*rights.xml*為供數位權利管理（DRM）資訊所保留，目的為讓EPUB出版品能在權利人、中介與使用者間前到信任地傳遞。

本版本的OCF規格不要求特定格式的DRM資訊，但未來版本可能會要求。*rights.xml*的內容**應該**僅包含命名空間認可的元素[XML-NAMES]，以避免與未來的格式產生斷裂。

當*rights.xml*檔案不存在時，該容器中沒有任何部分在容器層級上受到權利管控。但權利表述可能存在於容納的內容解釋。

如果*rights.xml*不存在時，OCF抽象容器沒有任何部分受到權利管控。

##### 3.5.2.6 數位簽章檔案 (signatures.xml)

> ##### 注意事項
>
> 添加數位簽章並不保證EPUB檔案不受到變更，主要因為閱讀系統並不需要確認簽章。

*META-INF*資料夾裡**選擇性**的*signatures.xml*包含供容器與其內容的數位簽章。本檔案的內容**必需**合乎定義在「供*signatures.xml*使用的綱要」裡提供的綱要。

*signatures.xml*檔案的根元素為*signatures*元素。該元素包含類型子元素*Signature*如[XMLDSIG-CORE1]所定義。簽章可套用於一本EPUB出版品的整體或者其部分，並且可以指定用於簽署任何種類的資料（即為，不只是XML）。

當*signatures.xml*不存在時，該容器中沒有任何部分在容器層級上受到數位簽署。但EPUB出版品中可能存在數位簽署。

當資料簽章為該容器所創建，其簽章**應該**被加到*signatures*元素中最後一個子*Signature*元素。

> ##### 注意事項
>
> 每一個在*signatures.xml*中的*Signature*由IRI所識別其簽章所適用的資料，使用[XMLDSIG-CORE1] *Manifest*元素以及其*Reference*子元素。獨立涵蓋的檔案可以被分別或者一起簽署。對每個檔案個別簽署時會創建資源的摘要值以能被獨立驗證。這種方式會讓簽章元素變大。如果檔案被一起簽署，簽署檔案的及殼可以被列於單一XML簽章*Manifest*元素以及被一或多個*Signature*元素參照。

任何，或所有位於容器中的檔案都可以被完整簽署，除了*signatures.xml*檔案自身，由該檔案包含計算過的簽章資訊。不管*signatures.xml*如何被簽署或者簽署者的目的為何。

當簽署者想要為容器允許加入或者移除簽章，卻沒有無效化簽署者簽章時，*signatures.xml***不應**被簽署。

如果簽署者想要對添加或者移除簽章以無效化簽署者的簽章時，可應用定義於節6.6.4中[XMLDSIG-CORE1]的Enveloped Signature transform以簽署整個預先存在的簽署檔，而非創建簽章。這種變形手段可以簽署所有之前的簽章，而在後續簽章加入套件時會變成無效。

> ##### 注意事項
>
> 如果簽署者想要移除既有的簽章使簽署者的簽章無效化，但也希望能夠允許添加簽章，可以適用XPath transform來僅對存在的簽章進行簽署。然而，像這樣變形的細節在本規格的目的之外。

[XMLDSIG-CORE1]規格與簽章的沒有任何語意關聯，使用者端可以包含語意資訊，例如，在簽章元素加入資訊來說明該簽章。[XMLDSIG-CORE1]規格解釋如何為簽章加入額外資訊，例如使用*SignatureProperties*元素。

> ###### 範例 7
> 
> 以下XML表述呈現一個*signatures.xml*檔案範例，其基於第二章[XMLDSIG-CORE1]中的範例。其包含一個簽章，該簽章適用於兩個容器中的資源*EPUB/book.xhtml*與*EPUB/images/cover.jpeg*。
> 
> <signatures xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <Signature Id="sig" xmlns="http://www.w3.org/2000/09/xmldsig#">
>         <SignedInfo>
>            <CanonicalizationMethod 
>                Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
>            <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#dsa-sha1"/>
>            <Reference URI="#Manifest1">
>                <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                <DigestValue>j6lwx3rvEPO0vKtMup4NbeVu8nk=</DigestValue>
>            </Reference>
>        </SignedInfo>
>        <SignatureValue>…</SignatureValue>
>        <KeyInfo>
>            <KeyValue>
>                <DSAKeyValue>
>                    <P>…</P><Q>…</Q><G>…</G><Y>…</Y> 
>                </DSAKeyValue>
>            </KeyValue>
>        </KeyInfo>
>        <Object>
>            <Manifest Id="Manifest1">
>                <Reference URI="EPUB/book.xhtml">                    
>                    <Transforms>                                                
>                        <Transform
>                            Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>                        
>                    </Transforms>
>                    <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                    <DigestValue></DigestValue>
>                </Reference>
>                <Reference URI="EPUB/images/cover.jpeg">
>                    <Transforms>                                                
>                        <Transform
>                            Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>                        
>                    </Transforms>
>                    <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                    <DigestValue></DigestValue>
>                </Reference>
>            </Manifest>
>        </Object>
>    </Signature> 
> </signatures>

## 4. OCF ZIP容器

### 4.1 導論

本章節為非規範性。

OCF ZIP容器為物理性單一檔案，宣告了OCF抽象容器。該容器用於：

- 在不同個人及/或不同組織間交換進行中的EPUB出版品；
- 讓EPUB出版品由一個出版社或者轉檔公司遞送到經銷或銷售管道；
- 將EPUB出版本遞交給EPUB閱讀系統或使用者。

### 4.2 ZIP檔案需求

OCF ZIP容器使用ZIP格式如[ZIP]所描述，但有著以下限制與澄清：

- OCF ZIP容器的內容**必需**為合乎規定的OCF抽象容器
- OCF ZIP容器**不得**使用ZIP應用程式備忘[ZIP]中的功能讓ZIP檔案跨多個儲存媒體，或者分割為複數檔案。OCF處理器**必需**在處理任何OCF檔案，其中指定ZIP檔分割跨多重儲存媒體的狀況為錯誤。
- OCF ZIP容器**必需**在ZIP封裝中僅包含儲存（無壓縮）及採Deflate演算法壓縮的ZIP內容。OCF處理器**必需**處理任何使用非Delate演算法的壓縮技術之OCF容器為錯誤。
- OCF ZIP容器**可以**使用在應用程式備忘[ZIP]中第五章G節定義為「Version 1」的ZIP64延伸，以及**應該**僅在內容需要他們時使用這些延伸。OCF處理器**必需**支援定義為「version 1」的ZIP64延伸。
- OCF ZIP容器**不得**使用由ZIP格式定義的加密功能；取而代之，加密**必需**使用加密檔案(*encryption.xml*)中所說明的功能來完成。OCF處理器**必需**處理使用ZIP加密功能的OCF ZIP容器為錯誤。
- OCF處理器不需要在讀取與存檔程序中保存來自OCF ZIP容器的資訊，由於在OCF抽象容器中並未定義；詳細說明，OCF處理器不需要保存CRC值、註解欄位或者其他欄位保存系統資訊以呼應特殊作業系統（例如，外部檔案屬性與額外的欄位）。
- OCF ZIP容器**必需**使用UTF-8[Unicode]為檔案系統名稱編碼。

以下限制適用於OCF ZIP容器封存的特殊欄位：

- 在本地檔案檔頭表格中，OCF ZIP容器**必需**設定*version needed to extract*欄位，值為*10*、*20*或者*45*，以符合該檔案的最大版本等級（例如，*20*代表需要Deflate演算法，*45*則是需要ZIP64）。OCF處理器**必需**將其他值視為錯誤。
- 在本地檔案檔頭表格中，OCF ZIP容器**必需**設定其*compression*方法欄位的值為0或8。OCF處理器**必需**將其他值視為錯誤。
- OCF處理器**必需**將有*Archive decryption header*或者一個*Archive extra data record*的OCF ZIP容器視為錯誤。

### 4.3 OCF ZIP容器媒體類型識別

OCF ZIP容器中第一個檔案**必需**為*mimetype*檔案，其須符合以下需求：

- *mimetype*檔案的內容**必需**為MIME媒體類型[RFC2046]字串*application/epub+zip*且以US-ASCII編碼[US-ASCII]。
- *mimetype*檔案**不得**包含任何開頭或結尾佔位符號或者空白。
- *mimetype*檔案**不得**以Unicode位元順序標記U+FEFF開始。
- *mimetype*檔案**不得**被壓縮或者加密，也**不得**有額外欄位在其ZIP檔頭。

> ##### 注意事項
>
> 參考附錄C，*application/epub+zip*媒體類型以了解關於*application/epub+zip*媒體類型的進一步資訊。

## 5. 資源模糊化

### 5.1 導論

本章節為非規範性。

由於OCF ZIP容器基本上是一個ZIP檔案，一般可得的ZIP工具都可以用於從其包裝中解壓縮未加密的內容流。此外，ZIP檔案的特性表示其內容可以如其他原生容器在一些系統上（例如，資料夾）顯示。

ZIP檔案的單純性很方便，但也產生了一個問題，不加密的副作用是易於提取資源，而這不是期盼的結果。例如，作者想要包含第三方字體時，一般不會希望字體被解壓縮並且被其他人使用。更重要的是，許多商用字體允許被嵌入，但嵌入字體即代表其為EPUB出版品整體的一部分，不只是隨著內容提供其原始字體。

雖然現在作業系統的ZIP支援整合相當普遍，但只是把字體置放到ZIP封裝並不足以表示其不想被用於其他脈絡的意圖。這種不確定性會損害EPUB出版品中相當好用的字體嵌入相容性。

為了避免字體受到使用，有些字體提供者可能僅會在以某些方法與EPUB出版品連結的狀況下，才允許使用它們的字體於EPUB出版品。即為，當字型檔案不能以預設工具被直接安裝在裝置中供作業系統使用，也不能被其他EPUB出版品所直接使用。

提供數位權利管理或者強制系統供這些資源使用超過本規格的目標。本章節則以定義模糊化的方法取代，其需要花額外的功夫在最終OCF收受端以增加對任何模糊化資源的一般性存取。

請注意，本規格並不將其宣稱為加密，也不能保障資源安全無虞不受侵權。然而，僅希望這項演算法將會符合多數提供者希望為其資源提供一些保障，而不能簡單地透過對容器解壓縮取出。

在字體的案例中，主要使用的方法是模糊化，定義的機制將簡單地提供阻擋方式來避免人們沒有注意到授權細節。其將無法避免有意圖的使用者獲得對字體的完整存取權。對該OCF容器而言，則可以套用該定義的演算法來取出原始字型檔案。本模糊手段是否能滿足個別字體的授權，依然還需詢問授權者與被授權者。

### 5.2 模糊化密鑰

用於模糊化演算法的密鑰，由預設內容解釋的唯一識別碼所取得。

所有空白字元，如XML 1.0規格[XML]中2.3章所定義，**必需**由識別碼中移除——尤其是Unicode碼點*U+0020*、*U+0009*、*U+000D*與*U+000A*。

UTF-8表意的SHA-1摘要結果字串**需要**被取得以被安全雜湊標準（Secure Hash Standard）[FIPS-180-4]所指定。其摘要即直接作為演算法密鑰使用。

### 5.3 模糊化演算法

部署供模糊化資源的演算法固定調整最初檔案的1040位元組（~1KB）。在罕見的狀態下檔案小於1040位元組時，整個檔案都會變動。

為了模糊化原始資料，結論上使用邏輯互斥或（logical exclusive or, XOR）於原始檔案的第一個位元組，以及將模糊化密鑰的第一個位元組儲存作為嵌入資源的第一個位元組。

本程序將逐來源檔案和密鑰的位元組重複，持續到所有密鑰的位元組都被使用完畢。此時，處理將會繼續從密鑰的第一個位元組與來源的第21個位元組開始。當1040個位元組以這種方式編碼後（或者到達來源的結束時），任何來源中剩下的資料都將直接複製到結果檔。

資源模糊化**必需**發生早於壓縮及加入OCF容器前。請注意模糊化不是加密，本需求不會違反加密檔案（*encryption.xml*）在加密前先壓縮資源的規則。

> ###### 範例 8
> 
> 以下假代碼展示了模糊化演算法。
> 
> set ocf to OCF container file
> set source to file
> set destination to obfuscated file
> set keyData to key for file
> set outer to 0
> while outer < 52 and not (source at EOF)
>     set inner to 0
>     while inner < 20 and not (source at EOF)
>         read 1 byte from source     //Assumes read advances file position
>         set sourceByte to result of read
>         set keyByte to byte inner of keyData
>         set obfuscatedByte to (sourceByte XOR keyByte)
>         write obfuscatedByte to destination
>         increment inner
>     end while
>     increment outer
> end while
> if not (source at EOF) then
>     read source to EOF
>     write result of read to destination
> end if
> Deflate destination
> store destination as source in ocf

為了恢復成原來的字型檔案，程序僅要簡單反向：來源檔案變成模糊化資料，而其結果檔案將包含原始資料。

> ##### 注意事項
>
> 對字體的模糊化早在EPUB 3.0.1版就已經允許使用，但沒有指定模糊化與壓縮的順序。結果而言，在解壓縮與去模糊化後可能會得到不合規的字體。在這些狀況下，在解壓縮前對資料進行去模糊化可能取得合規的字體。本規格不要求對這種逆向方法的支援，原因是不適用本版本規格，但其可能需要納入對EPUB 3內容的一般支援。

### 5.4 指定模糊化資源

儘管技術上並非對資料加密，所有模糊化資源**必需**在*encryption.xml*檔案中登記，並且出現於該EPUB出版品中（請見加密檔案(*encryption.xml*)）。

*EncryptedData*元素**必需**為每一個模糊化資源包含在內。每一個*EncryptedData*元素**必需**包含一個*EncryptionMethod*子元素，其*Algorithm*屬性之值設定為*http://www.idpf.org/2008/embedding*。這項屬性出現代表使用本規格所闡釋的演算法。對模糊化資源的路徑**必需**被列於*CipherData*元素中的*CipherReference*子元素。

> ###### 範例 9
> 
> 以下範例顯示一筆在*encryption.xml*檔案裡的模糊化字型資料。
> 
> <encryption 
>     xmlns="urn:oasis:names:tc:opendocument:xmlns:container" 
>     xmlns:enc="http://www.w3.org/2001/04/xmlenc#">
>     <enc:EncryptedData> 
>         <enc:EncryptionMethod Algorithm="http://www.idpf.org/2008/embedding"/> 
>         <enc:CipherData> 
>             <enc:CipherReference URI="EPUB/Fonts/BKANT.TTF"/>  
>         </enc:CipherData> 
>     </enc:EncryptedData>  
> </encryption>

為了避免無意義地複製嵌入資源到其他EPUB出版品，模糊化密鑰不得在*encryption.xml*檔案中提供。

## A. 綱要（Schemas）

### A.1 供*container.xml*使用的綱要

供*container.xml*檔案使用的綱要可於 *https://github.com/w3c/epubcheck/tree/master/src/main/resources/com/adobe/epubcheck/schema/30/ocf-container-30.nvdl.* 取得。

使用本綱要進行驗證需要支援[RelaxNG-Schema]及[XMLSCHEMA-2]的處理器。

### A.2 供*encryption.xml*使用的綱要

供*encryption.xml*檔案使用的綱要包含在[XMLSEC-RNGSCHEMA-20130411]中。

### A.3 供*signatures.xml*使用的綱要

供*signatures.xml*檔案使用的綱要包含在[XMLSEC-RNGSCHEMA-20130411]中。

## B. 範例

本章節為非規範性。

以下範例示範了使用OCF格式於OCF ZIP容器中包含簽署及加密的EPUB出版品。

> ###### 範例 10
> 
> OCF ZIP容器中依序排列的檔案列表
> 
> mimetype
> META-INF/container.xml
> META-INF/signatures.xml
> META-INF/encryption.xml
> EPUB/As_You_Like_It.opf
> EPUB/book.html
> EPUB/nav.html
> EPUB/images/cover.png

> ###### 範例 11
> 
> *mimetype*檔案的內容
> 
> application/epub+zip

> ###### 範例 12
> 
> *META-INF/container.xml*檔案的內容
> 
> <?xml version="1.0"?>
> <container version="1.0" xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <rootfiles>
>         <rootfile full-path="EPUB/As_You_Like_It.opf"
>             media-type="application/oebps-package+xml"/>
>     </rootfiles>
> </container>

> ###### 範例 13
> 
> *META-INF/signatures.xml*檔案的內容
> 
> <signatures xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
>     <Signature Id="AsYouLikeItSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
>         
>         <!--
>              SignedInfo is the information that is actually signed.
>              In this case, the SHA-1 algorithm is used to sign the 
>              canonical form of the XML documents enumerated in the
>              Object element below.
>         -->
>         <SignedInfo>
>             <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
>             <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#dsa-sha1"/>
>             <Reference URI="#AsYouLikeIt">
>                 <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                 <DigestValue>…</DigestValue>
>             </Reference>
>         </SignedInfo>
>         
>         <!--
>              The signed value of the digest above, using the DSA 
>              algorithm
>         -->
>         <SignatureValue>…</SignatureValue>
>         
>         <!--
>              The key used to validate the signature
>         -->
>         <KeyInfo>
>             <KeyValue>
>                 <DSAKeyValue>
>                     <P>…</P>
>                     <Q>…</Q>
>                     <G>…</G>
>                     <Y>…</Y>
>                 </DSAKeyValue>
>             </KeyValue>
>         </KeyInfo>
>         
>         <!--
>              The list of resources to sign (note that the canonical
>              form of XML documents is signed, while the binary form
>              of all other resources is used)
>         -->
>         <Object>
>             <Manifest Id="AsYouLikeIt">
>                 <Reference URI="EPUB/As_You_Like_It.opf">
>                     <Transforms>
>                         <Transform Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
>                     </Transforms>
>                     <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                     <DigestValue></DigestValue>
>                 </Reference>
>                 <Reference URI="EPUB/book.html">
>                     <Transforms>
>                         <Transform Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
>                     </Transforms>
>                     <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                     <DigestValue></DigestValue>
>                 </Reference>
>                 <Reference URI="EPUB/images/cover.png">
>                     <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
>                     <DigestValue></DigestValue>
>                 </Reference>
>             </Manifest>
>         </Object>
>     </Signature>
> </signatures>

> ###### 範例 14
> 
> *META-INF/encryption.xml*檔案的內容
> 
> <?xml version="1.0"?>
> <encryption xmlns="urn:oasis:names:tc:opendocument:xmlns:container"
>     xmlns:enc="http://www.w3.org/2001/04/xmlenc#" xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
> 
>     <!--
>          The RSA-encrypted AES-128 symmetric key used to encrypt
>          data enumerated in EncryptedData blocks below
>     -->
>     <enc:EncryptedKey Id="EK">
>         <enc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-1_5"/>
>         <ds:KeyInfo>
>             <ds:KeyName>John Smith</ds:KeyName>
>         </ds:KeyInfo>
>         <enc:CipherData>
>             <enc:CipherValue>xyzabc…</enc:CipherValue>
>         </enc:CipherData>
>     </enc:EncryptedKey>
> 
>     <!--
>          Each EncryptedData block identifies a single resource
>          that has been encrypted using the AES-128 algorithm.
>          The data remains stored, in its encrypted form, in the
>          original file within the container.
>     -->
>     <enc:EncryptedData Id="ED1">
>         <enc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
>         <ds:KeyInfo>
>             <ds:RetrievalMethod URI="#EK" Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
>         </ds:KeyInfo>
>         <enc:CipherData>
>             <enc:CipherReference URI="EPUB/book.html"/>
>         </enc:CipherData>
>     </enc:EncryptedData>
> 
>     <enc:EncryptedData Id="ED2">
>         <enc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#kw-aes128"/>
>         <ds:KeyInfo>
>             <ds:RetrievalMethod URI="#EK" Type="http://www.w3.org/2001/04/xmlenc#EncryptedKey"/>
>         </ds:KeyInfo>
>         <enc:CipherData>
>             <enc:CipherReference URI="EPUB/images/cover.png"/>
>         </enc:CipherData>
>     </enc:EncryptedData>
> </encryption>

> ###### 範例 15
> 
> *EPUB/As_You_Like_It.opf*檔案的內容
> 
> <?xml version="1.0"?>
> <package version="3.0"
>          xml:lang="en"
>          xmlns="http://www.idpf.org/2007/opf"
>          unique-identifier="pub-id">
>     
>     <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>         <dc:identifier id="pub-id">urn:uuid:B9B412F2-CAAD-4A44-B91F-A375068478A0</dc:identifier>
>         
>         <dc:language>en</dc:language>
>         
>         <dc:title>As You Like It</dc:title>
>         
>         <dc:creator id="creator">William Shakespeare</dc:creator>
>         
>         <meta property="dcterms:modified">2000-03-24T00:00:00Z</meta>
>         
>         <dc:publisher>Project Gutenberg</dc:publisher>
>         
>         <dc:date>2000-03-24</dc:date>
>         
>         <meta property="dcterms:dateCopyrighted">9999-01-01</meta>
>         
>         <dc:identifier id="isbn13">urn:isbn:9780741014559</dc:identifier>
>         
>         <dc:identifier id="isbn10">0-7410-1455-6</dc:identifier>
>         
>         <link rel="xml-signature"
>               href="../META-INF/signatures.xml#AsYouLikeItSignature"/>
>     </metadata>
>     
>     <manifest>
>         <item id="r4915" 
>               href="book.html" 
>               media-type="application/xhtml+xml"/>
>         <item id="r7184" 
>               href="images/cover.png" 
>               media-type="image/png"/>
>         <item id="nav" 
>               href="nav.html" 
>               media-type="application/xhtml+xml" 
>               properties="nav"/>
>     </manifest>
>     
>     <spine>
>         <itemref idref="r4915"/>
>     </spine>
> </package>

## C. application/epub+zip 媒體類型

本章節為非規範性。

本附錄註冊媒體類型*application/epub+zip*供EPUB開放容器格式（Open Container Format, OCF）使用。

一個OCF ZIP容器，或EPUB容器，檔案為基於[ZIP]封存格式技術的容器。用於包覆EPUB出版品的內容解釋。OCF與其相關標準由World Wide Web Consortium (W3C)所維護並且定義。

**MIME媒體類型名稱：** 
    *application*

**MIME子類型名稱：**
    *epub+zip*

**必要參數：**
    無。

**選擇性參數：**
    無。

**編碼考量：**
    OCF ZIP容器檔案為以*application/zip*媒體類型編碼的二進位檔案。 

**安全性考量：**
    所有能夠讀取OCF ZIP容器檔案的處理器應該嚴密地對取得的檔案大小以及合規性進行檢查。  
    此外，因為各種不同內容類型可被嵌入到OCF ZIP容器檔案中，*application/epub+zip*可以敘述為擁有超過此處說明含有安全性問題的內容。然而在這些案例中，僅有在處理器辨別並且處理這些額外內容，或者將內容交派到其他處理器進行近一步處理時，才會遇到這些潛在的安全問題。在這些案例中，安全性問題落於本註冊文件的領域之外。
    適用於*application/zip*的安全性考量也適用於OCF ZIP容器檔案。

**互通性考量：**
    無。

**已發表規格：**
    本媒體類型註冊供EPUB開放容器格式（Open Container Format, OCF）使用，如EPUB開放容器格式(OCF)3.2規格所敘述，位於*https://w3c.github.io/publ-epub-revision/epub32/spec/epub-ocf.html*。
    EPUB OCF 3.2規格同時取代RFC 4839以及開放容器格式2.0.1規格，其位於*https://www.idpf.org/doc_library/epub/OCF_2.0.1_draft.doc*，其也使用*application/epub+zip*媒體類型。

**使用該媒體類型的應用程式：**
    本媒體類型廣泛用於遞送EPUB格式的電子書。以下為非窮舉的應用程式列表：

- Adobe Digital Editions
- Aldiko
- Azardi
- Apple iBooks
- Barnes & Noble NOOK
- Bluefire Reader
- Calibre
- Google Play Books
- Kobo
- Microsoft Edge
- Readium

**額外資訊：**
    **魔術數字：**
        0: *PK 0x03 0x04*, 30: *mimetype*, 38: *application/epub+zip*
    **副檔名：**
        OCF ZIP容器檔案多半可透過副檔名.epub進行識別。
    **麥金塔檔案類型代碼：**
        ZIP
    **斷片識別碼：**
        連結綱要註冊維護於*https://www.idpf.org/epub/linking/*。這些綱要部分定義了客製化斷片識別碼可解析到*application/epub+zip*及*application/oebps-package+xml*文件。

**進一步資訊的聯絡人與郵件位址：**
    public-epub3@w3.org

**預計用途：**
    COMMON

**作者/變更管控**
    發布的規格是World Wide Web Consortium之EPUB 3社群小組的成果產品。W3C對本規格有變更的管控權。

## D. 謝詞與貢獻者

本章節為非規範性。

EPUB 3由W3C EPUB 3社群小組所開發，並且與出版業界小組相互協力。

EPUB 3.2改版由以下主導：

- Rachel Comerford (Macmillan Higher Education), 主席
- Dave Cramer (Hachette Livre), 主席

此外向編輯群致敬，本版本EPUB若缺少以下人物的顯著貢獻，則不可能完成：

- Aaron Troia
- Adam Sobieski
- Alberto Pettarin
- Andrew Gribben (Houghton Mifflin Harcourt)
- Avneesh Singh (DAISY Consortium)
- Ben Walters (Microsoft)
- Benjamin Young (Wiley)
- Bill Kasdorf (BISG)
- Brady Duga (Google)
- Carlos Araya
- Charles LaPierre (Benetech)
- Daniel Glazman (Disruptive Innovations)
- Daniel Weck (DAISY Consortium)
- David Herron
- Deborah Kaplan
- Evan Owens (Cenveo Publisher Services)
- Franco Alvarado
- Garth Conboy (Google)
- Georg Stadler
- George Kersher (DAISY Consortium)
- Greg Alchin
- Hadrien Gardeur (Feedbooks)
- Iris Febres
- Ivan Herman (W3C)
- James Briano
- Jeff Buehler
- Johan van der Knijff
- John Costa (Repub Interactive Technologies LLC)
- Julian Calderazi (DigitalBe)
- Ken Jones (Circular Software)
- Krzysztof Zemczak
- Laura Brady
- Laurent Le Meur (EDRLab)
- Léonie Watson (Paciello Group)
- Lloyd Rasmussen (Library of Congress)
- Luc Audrain (Hachette Livre)
- Makoto Murata (Keio Advanced Publishing Laboratory)
- Martin Kraetke (le-tex publishing services GmbH)
- Mateus Manço Teixeira (W. W. Norton)
- Matt Curtis
- Matt Garrish (DAISY Consortium)
- Mike Baker (Houghton Mifflin Harcourt)
- Mustapha Lazrek (Microsoft)
- N. Erhan Uzumcu
- Naomi Kennedy (Penguin Random House)
- Nick Ruffilo (VitalSource)
- Olaf Hoffmann
- Peter Krautzberger (krautzource UG)
- Rachel Comerford (Macmillan Higher Education)
- Ric Wright
- Rick Johnson (VitalSource)
- Romain Deltour (DAISY Consortium)
- Ruth Tait
- Theresa O’Connor (Apple)
- Tobias Fischer
- Toshiaki Koike (Voyager Japan Inc.)
- Tzviya Siegman (Wiley)
- Wolfgang Schindler (PONS GmbH)
- Zheng (Jeff) Xu (Rakuten Inc.)

特別感謝IDPF的前會員，尤其是Markus Gylling與Bill McCoy，沒有他們EPUB不可能成真。

## E. 參考資料

### E.1 規範性文件

#### [CSSSnapshot]

　　[CSS Snapshot](https://www.w3.org/TR/CSS/). URL: https://www.w3.org/TR/CSS/

#### [EPUB32]

　　[EPUB 3.2](https://www.w3.org/publishing/epub3/epub-spec.html). URL: epub-spec.html
　　
#### [FIPS-180-4]

　　[FIPS PUB 180-4 Secure Hash Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf). U.S. Department of Commerce/National Institute of Standards and Technology. URL: https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf
　　
#### [RelaxNG-Schema]

　　[Information technology -- Document Schema Definition Language (DSDL) -- Part 2: Regular-grammar-based validation -- RELAX NG](http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip). ISO/IEC. 2008. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip

#### [RFC2046]

　　[Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types](https://tools.ietf.org/html/rfc2046). N. Freed; N. Borenstein. IETF. November 1996. Draft Standard. URL: https://tools.ietf.org/html/rfc2046

#### [RFC2119]

　　[Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

#### [RFC3986]

　　[Uniform Resource Identifier (URI): Generic Syntax](https://tools.ietf.org/html/rfc3986). T. Berners-Lee; R. Fielding; L. Masinter. IETF. January 2005. Internet Standard. URL: https://tools.ietf.org/html/rfc3986

#### [RFC3987]

　　[Internationalized Resource Identifiers (IRIs)](https://tools.ietf.org/html/rfc3987). M. Duerst; M. Suignard. IETF. January 2005. Proposed Standard. URL: https://tools.ietf.org/html/rfc3987

#### [TR15]

　　[Unicode Normalization Forms](http://www.unicode.org/reports/tr15/). URL: http://www.unicode.org/reports/tr15/

#### [Unicode]

　　[The Unicode Standard](https://www.unicode.org/versions/latest/). Unicode Consortium. URL: https://www.unicode.org/versions/latest/

#### [US-ASCII]

　　"Coded Character Set - 7-bit American Standard Code for Information Interchange", ANSI X3.4, 1986..

#### [XML]

　　[Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/

#### [XML-NAMES]

　　[Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/

#### [XMLDSIG-CORE1]

　　[XML Signature Syntax and Processing Version 1.1](https://www.w3.org/TR/xmldsig-core1/). Donald Eastlake; Joseph Reagle; David Solo; Frederick Hirsch; Magnus Nyström; Thomas Roessler; Kelvin Yiu. W3C. 11 April 2013. W3C Recommendation. URL: https://www.w3.org/TR/xmldsig-core1/

#### [XMLENC-CORE1]

　　[XML Encryption Syntax and Processing Version 1.1](https://www.w3.org/TR/xmlenc-core1/). Donald Eastlake; Joseph Reagle; Frederick Hirsch; Thomas Roessler. W3C. 11 April 2013. W3C Recommendation. URL: https://www.w3.org/TR/xmlenc-core1/

#### [XMLENC-DECRYPT]

　　[Decryption Transform for XML Signature](https://www.w3.org/TR/xmlenc-decrypt/). Merlin Hughes; Takeshi Imamura; Hiroshi Maruyama. W3C. 10 December 2002. W3C Recommendation. URL: https://www.w3.org/TR/xmlenc-decrypt/

#### [XMLSCHEMA-2]

　　[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/xmlschema-2/). Paul V. Biron; Ashok Malhotra. W3C. 28 October 2004. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema-2/

#### [XMLSEC-RNGSCHEMA-20130411]

　　[XML Security RELAX NG Schemas](https://www.w3.org/TR/2013/NOTE-xmlsec-rngschema-20130411/). Murata Makoto; Frederick Hirsch. W3C. 11 April 2013. W3C Note. URL: https://www.w3.org/TR/2013/NOTE-xmlsec-rngschema-20130411/

#### [ZIP]

　　[.ZIP File Format Specification](https://www.pkware.com/documents/casestudies/APPNOTE.TXT). 1 September 2012. Final. URL: https://www.pkware.com/documents/casestudies/APPNOTE.TXT

### E.2 參考性文件

#### [EPUB32Changes]

　　[EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html). URL: epub-changes.html

#### [HTML]

　　[HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [ODF]

　　[Open Document Format for Office Applications (OpenDocument) v1.0](https://www.oasis-open.org/committees/download.php/12572/OpenDocument-v1.0-os.pdf). 1 May 2005. URL: https://www.oasis-open.org/committees/download.php/12572/OpenDocument-v1.0-os.pdf

#### [RFC]

　　[Request for Comments](https://www.ietf.org/standards/rfcs/). URL: https://www.ietf.org/standards/rfcs/
