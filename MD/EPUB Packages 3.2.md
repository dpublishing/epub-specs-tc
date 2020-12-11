# EPUB包裝 3.2
最終社群小組規格 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-packages.html
**編輯**：
    Matt Garrish (DAISY Consortium)
    Dave Cramer (Hachette Book Group)
**前任編輯**：
    Markus Gylling (International Digital Publishing Forum (IDPF))
    William McCoy (International Digital Publishing Forum (IDPF))
**協助參與：**
    GitHub w3c/publ-epub-revision
    提出問題
    版本紀錄
    修改要求

Copyright © 1999-2019 International Digital Publishing Forum™ and W3C® (MIT, ERCIM, Keio, Beihang)

<hr />

EPUB是國際數位出版論壇（IDPF, International Digital Publishing Forum）的註冊商標

## 概要

本規格定義了一個EPUB® 3包裝的語意與適用性需求。每個包裝代表了一本EPUB出版品的一項內容解釋，並且由包裝文件所定義，其敘述了內容解釋的內容並且設置了出版品資源如何產生關連的需求。

本規格也定義了EPUB導覽文件，一份可由機器與人類閱讀的特化EPUB內容文件，能夠提供導覽協助，如：目次。

本規格屬於組成[EPUB32]的規格群之一，其為基於XML與Web標準的數位出版品交換與遞送格式。要了解整體EPUB 3規格，需要與其他規格一併閱讀且理解。

可參考[EPUB32Changes]以了解本規格與其前版本的差異資訊。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
1.1 術語
1.2 適用性
1.3 字首對應
2. 適用性
2.1 包裝適用性
2.2 閱讀系統適用性
3. 包裝文件
3.1 導論
3.2 內容適用性
3.3 閱讀系統適用性
3.4 包裝文件定義
3.4.1 package元素
3.4.2 共享的屬性
3.4.3 詮釋資料（metadata）
3.4.3.1 metadata元素
3.4.3.2 DCMES必需元素
3.4.3.2.1 identifier元素
3.4.3.2.2 title元素
3.4.3.2.3 language元素
3.4.3.3 DCMES選配元素
3.4.3.3.1 一般定義
3.4.3.3.2 contributor元素
3.4.3.3.3 creator元素
3.4.3.3.4 date元素
3.4.3.3.5 subject元素
3.4.3.3.6 type元素
3.4.3.4 meta元素
3.4.3.5 link元素
3.4.4 宣告（manifest）
3.4.4.1 manifest元素
3.4.4.2 item元素
3.4.4.3 宣告回退
3.4.4.4 bindings元素 (不再推薦)
3.4.5 書脊（spine）
3.4.5.1 spine元素
3.4.5.2 itemref元素
3.4.6 集合（collections）
3.4.6.1 collection元素
3.4.7 遺存（Legacy）
3.4.7.1 meta元素
3.4.7.2 guide元素
3.4.7.3 NCX
4. 包裝詮釋資料
4.1 出版品識別碼
4.1.1 獨特識別碼
4.1.2 發布識別碼
4.2 用語關聯機制
4.2.1 導論
4.2.2 預設用語
4.2.3 保留字首
4.2.4 prefix屬性
4.2.5 特性（property）資料類別
4.2.5.1 語法
4.2.5.2 處理方式
4.3 包裝顯示詮釋資料
4.3.1 導論
4.3.2 參考
4.3.3 一般特性
4.3.3.1 rendition:flow特性
4.3.3.1.1 用法
4.3.3.1.2 允許的值
4.3.3.1.3 覆蓋書脊
4.3.3.1.4 範本
4.3.3.2 rendition:align-x-center特性
4.3.4 固定版面特性
4.3.4.1 導論
4.3.4.2 rendition:layout特性
4.3.4.2.1 用法
4.3.4.2.2 允許的值
4.3.4.2.3 覆蓋書脊
4.3.4.2.4 範本
4.3.4.3 rendition:orientation特性
4.3.4.3.1 用法
4.3.4.3.2 允許的值
4.3.4.3.3 覆蓋書脊
4.3.4.3.4 範本
4.3.4.4 rendition:spread特性
4.3.4.4.1 用法
4.3.4.4.2 允許的值
4.3.4.4.3 覆蓋書脊
4.3.4.4.4 範本
4.3.4.5 rendition:page-spread-* 特性
4.3.4.5.1 用法
4.3.4.5.2 範本
4.3.4.6 rendition:viewport特性 (不再推薦)
5. EPUB導覽文件
5.1 導論
5.2 內容適用性
5.3 閱讀系統適用性
5.4 EPUB導覽文件定義
5.4.1 nav元素：限制
5.4.2 nav元素：類型
5.4.2.1 導論
5.4.2.2 toc nav元素
5.4.2.3 page-list nav元素
5.4.2.4 landmarks nav元素
5.4.2.5 其他nav元素
5.4.3 hidden屬性
A. 包裝文件模式
B. application/oebps-package+xml媒體類型
C. Meta特性用語
C.1 概論
C.1.1 關於本用語
C.1.2 參考
C.2 詮釋資料meta特性
C.2.1 alternate-script
C.2.2 authority
C.2.3 belongs-to-collection
C.2.4 collection-type
C.2.5 display-seq
C.2.6 file-as
C.2.7 group-position
C.2.8 identifier-type
C.2.9 meta-auth (不再推薦)
C.2.10 role
C.2.11 source-of
C.2.12 term
C.2.13 title-type
C.2.14 範例
D. 詮釋資料連結用語
D.1 概論
D.1.1 關於本用語
D.1.2 參考
D.2 連結關係
D.2.1 acquire
D.2.2 alternate
D.2.3 marc21xml-record (不再推薦)
D.2.4 mods-record (不再推薦)
D.2.5 onix-record (不再推薦)
D.2.6 record
D.2.7 voicing
D.2.8 xml-signature (不再推薦)
D.2.9 xmp-record (不再推薦)
D.3 連結特性
D.3.1 onix
D.3.2 xmp
E. 宣告特性用語
E.1 概論
E.1.1 關於本用語
E.1.2 參考
E.2 宣告item特性
E.2.1 cover-image
E.2.2 mathml
E.2.3 nav
E.2.4 remote-resources
E.2.5 scripted
E.2.6 svg
E.2.7 Usage
E.2.8 Examples
F. 書脊特性用語
F.1 概論
F.1.1 關於本用語
F.1.2 參考
F.2 書脊itemref特性
F.2.1 page-spread-left
F.2.2 page-spread-right
F.2.3 範本
G. 謝詞與貢獻者
H. 參考資料
H.1 規範性文件
H.2 參考性文件

<br />

## 1. 導論

### 1.1 術語

專屬於EPUB 3的術語在本文件中以括號（譯注：英文版為首字大寫。範例如「作者」，「閱讀系統」）。術語與定義的完整清單提供於[EPUB32]。

每章節術語第一次出現時才會連結至其定義。

### 1.2 適用性

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、不得（MUST NOT）、推薦（RECOMMENDED）、應該（SHOULD）、不應（SHOULD NOT）**應該以[RFC2119]之記述解釋。

### 1.3 字首對應

為求方便，以下保留字首對應用於本規格中。

prefix | URI
------- | -------
dcterms | http://purl.org/dc/terms/
opf | http://www.idpf.org/2007/opf
rendition | http://www.idpf.org/vocab/rendition/#

## 2. 適用性

### 2.1 包裝適用性

一個適用的EPUB包裝**必需**滿足以下領域需求：

#### 包裝文件

- **必需**包含唯一的包裝文件，其內容**必需**符合定義在內容文件—內容適用性中的需求。

#### 出版品資源

- 所有與包裝相關的出版品資源**必需**列於包裝文件（定義於宣告）

#### EPUB導覽文件

- **必需**包含唯一的EPUB導覽文件，其內容**必需**符合定義在EPUB導覽文件—內容適用性中的需求。

#### 內容文件

- **必需**包含一或多個EPUB內容文件，個別內容**必需**符合定義於[ContentDocs32]中的需求。

#### CSS樣式表

- **可以**包含零或多個CSS樣式表，個別內容**必需**符合定義於CSS樣式表—內容適用性[ContentDocs32]中的需求。

#### 發音辭典

- **可以**包含零或多個PLS文件，個別內容**必需**符合定義在PLS文件—內容適用性[ContentDocs32]中的需求。

#### 媒體層疊文件

- **可以**包含零或多個媒體層疊文件，個別內容**必需**符合定義在[MediaOverlays32]中的需求。

#### 額外資源

- **可以**包含零或多個以上所列之外的出版品資源，個別**必需**遵守出版品資源[EPUB32]的需求。

### 2.2 閱讀系統適用性

一個EPUB閱讀系統**必需**滿足以下領域需求：

- **必需**以定義於包裝文件—閱讀系統適用性的方式處理包裝文件，且期盼所有使用包裝文件所能達到的邏輯表達呈現（例如，閱讀順序，回退鏈，行頁方向與固定版面）。

- **必需**以定義於EPUB導覽文件—閱讀系統適用性的方式處理EPUB導覽文件。

- 處理包裝時**不得**使用任何未列於包裝文件外的資源（例如，META-INF檔案（[OCF32]）或者專屬於該EPUB出版品中其他內容解釋的資源。）

## 3. 包裝文件

### 3.1 導論

本章節為非規範性。

包裝文件是一份包含一系列元素的XML文件，各元素分別內含有EPUB包裝各特殊用途的資訊。這些元素提供了集中的詮釋資料，組成包裝個別資源的細節，並且提供閱讀順序以及其他必要的資訊來排出內容解釋的版面。

以下列表歸納了能在包裝文件中取得的資訊：

- 詮釋資料—用來包含及/或參照能適用於該EPUB出版品內容解釋之詮釋資料的機制。

- 宣告—識別（透過IRI[RFC3987]）及描述（透過MIME媒體類型[RFC4839]）一系列集體對組成該內容解釋的資源

- 書脊—依序排列的ID對照，呼應宣告中最上層資源，使所有其他的系列資源能夠被接觸並且使用。書脊也定義了該內容解釋的預設閱讀順序。

- 集合—在包裝內包含以及識別子元件的方法。

- 宣告回退鏈—用以將最上層資源作為同等內容的順序清單。閱讀系統可以藉此在資源中挑選何者是於排版顯示。

### 3.2 內容適用性

一份包裝文件**必需**符合以下領域的需求：

#### 文件特性

- **必需**符合定義在XML適用性[EPUB32]中的XML文件規定的適用性要求。

- **必需**符合內容文件定義中所表達的內容適用性規定。

> ##### 注意事項
> 有些內容適用性可以利用附錄A包裝文件模式中提供的模式來驗證內容文件進行檢查。

#### 檔案特性

- 包裝文件檔名**應該**使用副檔名 .opf。

包裝文件的MIME媒體類別為 application/oebps-package+xml [RFC4839]。

### 3.3 閱讀系統適用性

一個EPUB閱讀系統**必需**符合以下領域的需求：

#### 處理

- **必需**符合包裝文件定義中閱讀系統相容性限制之規定。
- **應該**如包裝文件詮釋資料中所表述的方式處理顯示詮釋資料。
- **必需**如固定版面特性中所表述的方式處理固定版面詮釋資料。
- 當私有的詮釋資料特性，在行為上和固定版面特性中定義的適當語意有所顯示的衝突時，**必需**忽略。

### 3.4 包裝文件定義

除另有指定，本章節所有定義的[XML]元素都在 *http://www.idpf.org/2007/opf* 命名空間 [XML-NAMES]。

當定義在本章節中的元素有強制性文字內容，該內容再解釋描述中會提供元素參考的值。

#### 3.4.1 *package*元素

*Package* 元素是包裝文件的根元素，並且定義了EPUB包裝的各面向資訊（參考導論獲得一般性概論）。

> ###### 元素名稱
> 
> *package*
> 
> ###### 用法
> 
> package元素是包裝文件的根元素
> 
> ###### 屬性
> 
> *dir [選擇性]*
> 
> *id [選擇性]*
> 
> *prefix [選擇性]*
> 
> *xml:lang [選擇性]*
> 
> *unique-identifier [必需]*
> 
> *version [必需]*
> 
> ###### 內容模型
> 依此順序：
> 
> *metadata [唯一]*
> 
> *manifest [唯一]*
> 
> *spine [唯一]*
> 
> *guide [零或一個]* (遺存)
> 
> *bindings [零或一個]* (不推薦)
> 
> *collection [零或多個]*

*version* 屬性專用於指定EPUB規格版本，決定該EPUB包裝適用何版。該屬性之值**必需**為"3.0"才能與本規格版本相容。

*unique-identifier* 屬性以一個IDREF [XML]用以對照哪一個提供的 *dc:identifier* 元素為偏好，或者主要的識別碼。要了解更多請參照出版品識別碼。

*perfix* 屬性提供了一個字首的宣告機制，用於本規格沒有保存的字首。請參考*perfix*屬性以獲得更多資訊。

#### 3.4.2 共享的屬性

本章節提供共享屬性的定義（即為，二或多個元素都會使用到的元素）。

##### *dir*

指定內容的基本文字方向，屬性值適用於使用屬性的元素以及子孫元素。

原生方向性使用[Unicode]進行定義，且優先於本屬性。

准許使用值 *ltr* （左到右）與 *rtl* （右到左）

> <package … dir="ltr">

可以用在： *collection*, *dc:contributor*, *dc:coverage*, *dc:creator*, *dc:description*, *dc:publisher*, *dc:relation*, *dc:rights*, *dc:subject*, *dc:title*, *meta* 及 *package*。

##### *href*

對資源的絕對或相對IRI參照[RFC3987]。

> <link rel="record"
>       href="meta/9780000000001.xml" 
>       media-type="application/marc"/>

可以用在：*item* 及 *link*。

##### *id*

元素的ID [XML]，**必需**在該文件範圍內為唯一值。

> <dc:identifier id="pub-id">urn:isbn:97800000000001</dc:identifier>

可以用在：*collection*, *dc:contributor*, *dc:coverage*, *dc:creator*, *dc:date*, *dc:description*, *dc:format*, *dc:identifier*, *dc:language*, *dc:publisher*, *dc:relation*, *dc:rights*, *dc:source*, *dc:subject*, *dc:title*, *dc:type*, *item*, *itemref*, *link*, *manifest*, *meta*, *package* 及 *spine*。

##### *media-type*

用以指定參照資源的類型與格式的媒體類型[RFC2046]。

> <link rel="record"
>       href="http://example.org/meta/12389347?format=xmp"
>       media-type="application/xml"
>       properties="xmp"/>

可以用在：*item* 及 *link*。

##### *properties*

由空格區分的特性與值的列表。

請參考各元素的定義以確認能用在屬性中的反向用語。

> <item id="nav" 
>     href="nav.xhtml" 
>     properties="nav"
>     media-type="application/xhtml+xml"/>

可以用在：*item*, *itemref* 及 *link*。

##### *refines*

用以識別元素的表意或者元素添加的資源。屬性的值必須是相對IRI[RFC3987]，以解釋參照的資源或元素。

*refines* 屬性為**選擇性**，按照所添附的詮釋資料類別如何表述。當被忽略時，該元素定義了一個主要表述。

可以用在：*link* 及 *meta*。

##### *xml:lang*

指定用於內容的語言，屬性值適用於使用屬性的元素以及子孫元素。值定義於[XML]的2.12章節語言識別中。

> <package … xml:lang="ja">
>    …
> </package>

可以用在：*collection*, *dc:contributor*, *dc:coverage*, *dc:creator*, *dc:description*, *dc:publisher*, *dc:relation*, *dc:rights*, *dc:subject*, *dc:title*, *meta* 及 *package*。

#### 3.4.3 詮釋資料（metadata）

##### 3.4.3.1 *metadata*元素

*metadata*元素封裝了該內容解釋的詮釋資訊。

> ###### 元素名稱
> 
> *metadata*
> 
> ###### 用法
>
> **需**為包裝的第一個子元素。
> 
> ###### 屬性
> 無
> 
> ###### 內容模型
> 順序自由：
> 
> *dc:identifier [一或多個]*
> 
> *dc:title [一或多個]*
> 
> *dc:language [一或多個]*
> 
> *DCMES Optional Elements [零或多個]*
> 
> *meta [一或多個]*
> 
> *OPF2 meta [零或多個]* (遺存)
> 
> *link [零或多個]*

包裝文件的*metadata*元素有兩個主要功能：

1. 提供最小限的詮釋資訊讓閱讀系統能用於內部對EPUB出版品得分類，以及對使用者呈現（例如在書架上顯示）。
2. 提供取得所有顯示上必要的詮釋資料的機制，用以控制排版及顯示該內容解釋的內容（例如：固定版面的特性）。

包裝文件並非設計為提供複雜詮釋資料編目使用。若需要對一本EPUB出版品更細節的資訊，詮釋資料記錄（例如適用於國際標準，像是[ONIX]或者各種客制需求）可利用*link*元素進行關聯。這種做法讓詮釋資料可以以其原生形式被處理，被免在轉譯成最小限包裝文件結構時有潛在的問題或者資訊遺失。

為了維持這項哲學，包裝文件僅需要以下最小限度的詮釋資料：**必需**包含 [DC11] *title*、*identifier*及*language*元素加上 [DCTERMS] *modified*特性，所有其他的詮釋資料都為*選擇性*。

> ###### 範例1
> 
> 以下範例呈現詮釋資料最小限度的組合，作者必須加在包裝文件中。
> 
> <package … unique-identifier="pub-id">
>     …
>     <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>         <dc:identifier id="pub-id">urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809</dc:identifier>
>         <dc:title>Norwegian Wood</dc:title>
>         <dc:language>en</dc:language>
>         <meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>
>     </metadata>
>     …
> </package>

*meta*元素提供了普通機制來包含各種用語的詮釋資料特性。標準上用來包含定義於EPUB規格中的顯示用詮釋資料，但**可以**用於各種詮釋資料目的。

> ##### 注意事項
> 請見[EPUBAccessibility]以了解詮釋資料無障礙功能推薦做法。

##### 3.4.3.2 DCMES必需元素

###### 3.4.3.2.1 *identifier*元素

[DC11]的identifier元素包含連結到該內容解釋的識別碼，例如UUID、DOI或ISBN。

> ###### 元素名稱
> 
> *dc:identifier*
> 
> ###### 命名空間
> 
> *http://purl.org/dc/elements/1.1/*
> 
> ###### 用法
> 
> *metadata*的**必要**子元素
> 
> ###### 屬性
> 
> *id [選擇性]*
> 
> ###### 內容模型
> 文字

*metadata*區塊**必需**包含一個*identifier*元素內有該內容解釋明確的識別碼。該識別碼**必需**透過*package*元素中*unique-identifier*屬性被標註為獨特識別碼

> ###### 範例2
> 
> 以下範例呈現一本EPUB出版品的獨特識別碼元素
> 
> <package … unique-identifier="pub-id">
>     <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>         <dc:identifier id="pub-id">
>             urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809
>         </dc:identifier>
>         …
>     </metadata>
> </package>

每一份內容解釋的獨特識別碼**可以**不同，且一份內容解釋**可以**包含額外的*identifier*元素。

為了區分同EPUB出版品的不同版本，本規格切分出EPUB出版品用的獨特識別碼，以及發布識別碼用來辨識屬於哪一版本。

為了識別包裝後EPUB出版品的版本，發布識別碼可以透過組合獨特識別碼和該內容解釋的最後修改日期來建構。若要了解更多關於發布識別碼的語意以及要求，請參照發布識別碼章節。

> ###### 範例3
> 
> 以下範例呈現組成發布識別碼的兩個元件
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:identifier id="pub-id">
>         urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809
>     </dc:identifier>
>     <meta property="dcterms:modified">2016-01-01T00:00:01Z</meta>
>     …
> </metadata>

無論內容解釋何時更動，都**必需**包含一個最新的更動日期。

為了辨別一個識別碼是否適用於既有的系統或者是否獲得發行端的認證，閱讀系統**應該**檢查*identifier-type*特性。

> ###### 範例4
> 
> 以下範例呈現一個識別碼如何使用identifier-type特性來被額外標記為DOI。此處ONIX代碼列表5用於解釋產品識別碼類別
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:identifier id="pub-id">urn:doi:10.1016/j.iheduc.2008.03.001</dc:identifier>
>     <meta refines="#pub-id" property="identifier-type" scheme="onix:codelist5">06</meta>
>     …
> </metadata>

閱讀系統在處理元素的值之前，**必需**刪除前後的空白[XML]。

本規格對於識別碼沒有額外的限制與要求，除了**必需**至少在刪除空白後需要有一個字元長。並且強烈鼓勵識別碼為完整受驗證的URI。

###### 3.4.3.2.2 title元素

[DC11] title元素呈現了給予EPUB出版品的名稱範例。

> ###### 元素名稱
> 
> *dc:title*
> 
> ###### 命名空間
> 
> *http://purl.org/dc/elements/1.1/*
> 
> ###### 用法
> 
> *metadata*的**必要**子元素。
> 
> ###### 屬性
> 
> *dir [選擇性]*
> 
> *id [選擇性]*
> 
> *xml:lang [選擇性]*
> 
> ###### 內容模型
> 
> 文字

*metadata*區塊**必需**包含至少一個*title*元素內有EPUB出版品的標題。

> ###### 範例5
> 
> 以下範例呈現基本title元素：
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:title>Norwegian Wood</dc:title>
>     …
> </metadata>

閱讀系統**必需**按照文件順序識別第一個*title*元素作為該EPUB出版品的主要標題（即為最主要顯示給使用者的那一個）。本規格不定義如何處理額外的*title*元素。

> ###### 範例6
> 
> 以下範例呈現多重區塊標題：
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:title>THE LORD OF THE RINGS</dc:title>
>     <dc:title>Part One: The Fellowship of the Ring</dc:title>
>     …
> </metadata>
> 
> 相同的title可以使用單一*dc:title*元素作為表述，如以下：
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:title>
>         THE LORD OF THE RINGS, Part One: The Fellowship of the Ring
>     </dc:title>
>     …
> </metadata>

每一份內容解釋的標題**可以**不同。

閱讀系統在處理值之前，**必需**刪除前後的空白[XML]。

本規格對於標題沒有額外的限制與要求，除了**必需**至少在刪除空白後需要有一個字元長。

###### 3.4.3.2.3 language元素

[DC11] *language*元素指定了該內容解釋之內容使用的語言。本質不會由內容解釋中的個別元素所繼承。

> ###### 元素名稱
> 
> *dc:language*
> 
> ###### 命名空間
> 
> *http://purl.org/dc/elements/1.1/*
> 
> ###### 用法
> 
> *metadata*的**必要**子元素，可重複。
> 
> ###### 屬性
> 
> *id [選擇性]*
> 
> ###### 內容模型
> 
> 文字

*metadata*區塊**必需**包含至少一個*language*元素，其值適用於[BCP47]。

> ###### 範例7
> 
> 以下範例呈現一份使用美式英文的EPUB出版品：
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:language>en-US</dc:language>
>     …
> </metadata>

額外的*language*元素**可以**被包含在多語文出版品中，但各個元素的值**必需**符合[BCP47]。文件中的第一個*language*元素被視為該內容解釋的主要語言。

每一份內容解釋的語言**可以**不同。

閱讀系統在處理值之前，**必需**刪除前後的空白[XML]。

##### 3.4.3.3 DCMES選配元素

###### 3.4.3.3.1 一般定義

除了*identifier*、*language*與*title*外，所有其他[DC11]元素都設計為**選擇性**。這些元素需要符合以下一般定義：

> ###### 元素名稱
> 
> *contributor* | *coverage* | *creator* | *date* | *description* | *format* | *publisher* | *relation* | *rights* | *source* | *subject* | *type*
> 
> ###### 命名空間
> 
> *http://purl.org/dc/elements/1.1/*
> 
> ###### 用法
> 
> *metadata*的**選擇性**子元素，可重複。
> 
> ###### 屬性
> 
> *dir [選擇性]* – 僅允許用於*contributor*、*coverage*、*creator*、*description*、*publisher*、*relation*、*rights*與*subject*。
> 
> *id [選擇性]* – 允許用於任何元素。
> 
> *xml:lang [選擇性]* – 僅允許用於*contributor*、*coverage*、*creator*、*description*、*publisher*、*relation*、*rights*與*subject*。
> 
> ###### 內容模型
> 
> 文字

每一份內容解釋的**選擇性**[DC11]詮釋資料**可以**不同。

閱讀系統在處理值之前，**必需**刪除前後的空白[XML]。

所有**選擇性**[DC11]元素的值，**必需**至少在刪除空白後需要有一個字元長。

本規格不變更[DC11]元素定義除了以下章節的注意事項外。

###### 3.4.3.3.2 contributor元素

[DC11] *contributor*元素用於表現一個人、組織或其他的名字，作為創造本EPUB出版品內容次要地位的角色。

*contributor*元素的要求與對*creator*元素的要求一樣，無論各種方面。

###### 3.4.3.3.3 creator元素

[DC11] *creator*元素用於表現一個人、組織或其他的名字，對本內容解釋之內容創作負責。可以附加role特性到本元素來指出創作者在內容創作中所扮演的功能角色。

> ###### 範例8
> 
> 以下範例呈現如何使用MARC關係者用語來表達創作者為作者身份。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator">Haruki Murakami</dc:creator>
>     <meta refines="#creator" property="role" scheme="marc:relators" id="role">aut</meta>
>     …
> </metadata>

*creator*元素**應該**包含作者作為創作者的名稱，用以對使用者顯示。**可以**添加*file-as*特性來包含姓名正規化後的型態，以及*alternate-script*特性來呈現創作者以另一種語文或文字的名稱。

> ###### 範例9
> 
> 以下範例呈現處理使創作者名稱便於排序以及顯示。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator">Haruki Murakami</dc:creator>
>     <meta refines="#creator" property="role" scheme="marc:relators" id="role">aut</meta>
>     <meta refines="#creator" property="alternate-script" xml:lang="ja">村上 春樹</meta>
>     <meta refines="#creator" property="file-as">Murakami, Haruki</meta>
>     …
> </metadata>

如果一本EPUB出版品有多於一位的創作者，每一位都**應該**以不同的*creator*元素包含於其中。

當決定顯示順序時，閱讀系統**必需**使用文件中*metadata*區塊裡*creator*元素的順序。第一個*creator*元素就是主要創作者。如果一個閱讀系統要顯示創作者詮釋資料給使用者時，只要有可能，**應該**包含所有列於*metadata*區塊中的創作者（即為不考量顯示上的限制）。

> ###### 範例10
> 
> 以下範例中，Lewis Carroll因為列於第一位，為主要創作者。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator01">Lewis Carroll</dc:creator>
>     <dc:creator id="creator02">John Tenniel</dc:creator>
>     …
> </metadata>

次要貢獻者**應該**使用*contributor*元素來呈現。

###### 3.4.3.3.4 date元素

[DC11] *date*元素**必需**僅用於定義該EPUB出版品的出版日期。出版日期和最後修改日期（該內容解釋修改的最後時刻）不一樣。

**推薦**日期字串符合[ISO8601]，尤其是W3C日期與時間格式[DateTime]的子集表述，那樣的字串可同時供人讀與機讀。

> ###### 範例11
> 
> 以下範例呈現出版日期。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:date>2000-01-01T00:00:00Z</dc:date>
>     …
> </metadata>

額外的日期**應該**使用[DCTERMS]用語中特別的日期特性或者之類的來表達。

一份EPUB出版品的出版日期在所有副本中**可以**一樣，也**可以**因為副本而有所不同。（若EPUB出版品在應需求而產生）。

僅允許一個*date*元素。

###### 3.4.3.3.5 subject元素

[DC11] *subject*元素用以識別該EPUB出版品的主題。該元素的值**應該**為人讀標題或者標籤，但是**可以**為編碼的值，當主題分類不提供分離的解釋標籤時。

作者可以使用權威特性來識別該系統或者模式中該元素的值。

當模式被識別時，主題編碼**必需**使用*term*特性來聯繫。

> ###### 範例12
> 
> 以下範例呈現一個BISAC編碼以及標題。
> 
> <dc:subject id="subject01">FICTION / Occult &amp; Supernatural</dc:subject>
> <meta refines="#subject01" property="authority">BISAC</meta>
> <meta refines="#subject01" property="term">FIC024000</meta>

> ###### 範例13
> 
> 以下範例呈現使用一個IRI作為模式。
> 
> <dc:subject id="sbj01">Number Theory</dc:subject>
> <meta refines="#sbj01" property="authority">http://www.ams.org/msc/msc2010.html</meta>
> <meta refines="#sbj01" property="term">11</meta>

*term*特性**不得**在沒有指定模式的狀況下連結在*subject*元素中。

*subject*元素的值與*term*特性在指定的模式有所需求時，得區分大小寫。

###### 3.4.3.3.6 type元素

[DC11] *type*元素用來識別EPUB出版品屬於哪種特化類別（即為使用EPUB格式的註解或者字典）。

特化EPUB出版品的類別有一參考用的註冊檔，本元素可以由[TypesRegistry]中取用，但作者**可以**使用任何文字字串作為值。

##### 3.4.3.4 meta元素

*meta*元素提供用以包含包裝詮釋資料的基本手段。

> ###### 元素名稱
> 
> *meta*
> 
> ###### 用法
> 
> *metadata*元素的子元素，可以重複。
> 
> ###### 屬性
> 
> *dir [選擇性]*
> 
> *id [選擇性]*
> 
> *property [必需]*
> 
> *refines [選擇性]*
> 
> *scheme [選擇性]*
> 
> *xml:lang [選擇性]*
> 
> ###### 內容模型
> 
> 文字

每個meta元素定義了詮釋資料表述。其*property*屬性包含了一個特性資料類別值來定義表述中的陳述，以及該元素的文字內容所代表的聲明（參考詞彙關聯機制以獲得更多資訊）。

本規格定義了兩種詮釋資料表述的類型，可以使用*meta*元素進行定義：

- 「主要表述」是透過*meta*元素定義的表述之一，用來建立EPUB出版品的某些面向。沒有refines屬性的*meta*元素可被定義為主要表述。

- 「次要表述」是透過*meta*元素定義的表述之一，透過*refines*屬性用以強化表述的意義或者參照到資源。一個次要表述可能用以描述一段媒體片段的細節，例如，用以表述長度、透過定義該人物的角色來添加創作者或者貢獻者的表述。

次要表述不限於提供主要表述與資源的細節；還可以用於對其他次要表述添加意義，可用於創造資訊鏈。

> ##### 注意事項
> 
> 所有DCMES[DC11]元素皆用於表示主要表述，並且允許透過meta元素次要表述來強化。

本規格保留Meta特性用語用於特性的屬性。由其他用語來的術語**可以**透過提供字首使用（參考反向字首來取得不需要宣告的字首清單）。

> ###### 範例14
> 
> 以下範例呈現使用反向字首進行多種特性宣告
> 
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <meta property="dcterms:modified">2016-02-29T12:34:56Z</meta>
>     <meta property="rendition:layout">pre-paginated</meta>
>     <meta property="media:active-class">-epub-media-overlay-active</meta>
>     …
> </metadata>

*scheme*屬性定義了系統或者模式中元素的值來自何處。屬性的值**必需**為特性資料類型能夠解析到定義模式的資源。如果一個閱讀系統不能辨識*scheme*的屬性值，其**應該**將元素的值視為字串。

閱讀系統**應該**忽略所有他們無法辨識的*meta*元素之特性屬性。閱讀系統在遇到未知的表述時**不可**失敗。

除非一項單獨特性特別定義了一項不同的空白正規化演算法，閱讀系統在處理*meta*元素的職前，**必需**刪除所有開頭與結尾的空白[XML]。

每一項*meta*元素之表述值在空白正規化後，**必需**至少為一字元長。

##### 3.4.3.5 link元素

*link*元素用於讓內容解釋與資源進行關聯，例如詮釋資料記錄。

> ###### 元素名稱
> 
> *link*
> 
> ###### 用法
> 
> *metadata*元素的子元素，可以重複。
> 
> ###### 屬性
> 
> *href [必需]*
> 
> *id [選擇性]*
> 
> *media-type [視狀況必需]*
> 
> *properties [選擇性]*
> 
> *refines [選擇性]*
> 
> *rel [必需]*
> 
> ###### 內容模型
>
> 空白

*metadata*元素可以包含零或多個*link*元素，每一項都透過**必要**的*herf*屬性識別連結資源的所在位置。

連結的資源並非出版品資源，同時**不可**列於宣告中。連結的資源**可以**嵌入於列在宣告的出版品資源中，然而，在此狀況下，則**必需**為核心媒體類型資源[EPUB32]（例如，一份EPUB內容文件可以包含一份詮釋資料記錄序列化如[RDFA-CORE]或[JSON-LD]）。

> ###### 範例15
> 
> 以下範例呈現在一份XHTML內容文件中，於*script*元素裡嵌入一份對詮釋資料紀錄的參考。請注意嵌入的紀錄的媒體類型取得自*script*元素的*type*屬性；並非在*link*元素中指出
> 
> 
> 
> <metadata>
>     … 
>     <link rel="record"
>           href="front.xhtml#meta-json"
>           media-type="application/xhtml+xml"/>
>     …
> </metadata>

連結的資源可以位於本地或者遠端，但是作者需要注意閱讀系統對於取得遠端資源的支援為**選擇性**（即為資源可能無法取得）。

*media-type*屬性為**選擇性**，當連結的資源位於EPUB容器之外，而同一個IRI可以提供多於一個的媒體類型。該屬性對所有本地資源皆為**必要**。

**必要**的*rel*屬性由空格區分的特性值列表來建構內容解釋中的資源關係。

> ###### 範例16
> 
> 以下範例呈現使用link元素來連結本地MARC XML紀錄。
> 
> <link rel="record"
>       href="meta/9780000000001.xml" 
>       media-type="application/marc"/>

閱讀系統不需要使用或者顯示連結的資源，就算他們可以透過定義的*rel*屬性來識別關係。

*media-type*屬性的值不會永遠夠用於辨識連結資源的類型（例如，許多基於XML的紀錄格式使用媒體類型"*application/xml*"）。為了協助閱讀系統來辨識這種一般性的資源，可以*properties*屬性來附加語意識別碼。

> ###### 範例17
> 
> 以下範例呈現使用propertirs屬性來識別一個遠端的XMP紀錄。
> 
> <link rel="record"
>       href="http://example.org/meta/12389347?format=xmp"
>       media-type="application/xml"
>       properties="xmp"/>

本規格在EPUB詮釋資料連結用語中，定義了可被識別的保留關係與特性清單。

作者**可以**透過定義於本規格中的詮釋資料延伸性機制來使用其他用語添加關係與特性。作者也**可以**透過定義自己的字首來添加新的值。想了解更多資訊，請參考用語關聯機制。

> ###### 範例18
> 
> 以下範例呈現使用*link*元素連結到資訊性的網頁。請注意foaf不是預先定義的字首，所以必須在*prefix*屬性中被宣告。
> 
> <package … prefix="foaf: http://xmlns.com/foaf/spec/">
>     <metadata>
>         … 
>         <link rel="foaf:homepage"
>               href="http://example.org/book-info/12389347" />
>         …
>     </metadata> 
>     …
> </package>

在連結詮釋資料紀錄的案例中，閱讀系統**不得**忽略處理在包裝文件中的詮釋資料表達，以及只使用紀錄中表達的訊息。連結記錄的目的是為了增強提供給閱讀系統的資訊，而包裝的詮釋資料通常只包含重要的顯示用資訊。閱讀系統**可以**從多個連結記錄中組譯詮釋資料；不必選擇其一。

當要處理包裝文件中表述的詮釋資料和連結詮釋資料紀錄的衝突與不一致時，閱讀系統**必需**按照link元素在包裝文件中的順序來建立優先順序（例如，詮釋資料第一個連結的紀錄有最高優先順序，而包裝文件中的詮釋資料則為最低，無論連結元素放置在包裝metadata元元素之前、其中或者之後）。

> ###### 範例19
> 
> 以下範例呈現遠端紀錄有著高於本地紀錄的優先順序，也就是其優先順序高於可在metadata元素中發現的詮釋資料。
> 
> <metadata>
>     … 
>     <link rel="record"
>           href="http://example.org/onix/12389347"
>           media-type="application/xml"
>           properties="onix" />
>     
>    <link rel="record"
>          href="meta/meta.jsonld"
>          media-type="application/ld+json" />
>    …
> </metadata>

閱讀系統**必需**忽略任何包含在連結資源中，與EPUB出版品排版及顯示有關的程序。

> ##### 注意事項
> 
> 因為可以被連結到EPUB出版品的詮釋資料紀錄格式與序列多樣，比較詮釋資料特型變得相當複雜，本規格並不要求閱讀系統需處理連結的紀錄。

#### 3.4.4 宣告（manifest）

##### 3.4.4.1 *manifest*元素

*manifest*元素提供了出版品資源的窮舉清單，用以建構該內容解釋，每一項都由一個*item*元素所表示。

> ###### 元素名稱
> 
> *manifest*
> 
> ###### 用法
> 
> **必需**為*package*的第二個子元素，緊接在*metadata*之後。
> 
> ###### 屬性
> 
> *id [選擇性]*
> 
> ###### 內容模型
> 
> *item [一或多個]*

> ##### 注意事項
> 
> 本規格支援國際化資源名稱，所以出版品元素的元素與屬性接受IRI作為其值。為了與舊版僅支援URI的閱讀系統相容，資源名稱得限制使用ASCII字元集。

##### 3.4.4.2 item元素

*item*元素代表了一項出版品資源。

> ###### 元素名稱
> 
> *item*
> 
> ###### 用法
> 
> *manifest*元素的子元素，可以重複。
> 
> ###### 屬性
> 
> *fallback [視狀況必需]*
> 
> *href [必需]*
> 
> *id [必需]*
> 
> *media-overlay [選擇性]*
> 
> *media-type [必需]*
> 
> *properties [選擇性]*
> 
> ###### 內容模型
> 
> 空白

每一個在*manifest*裡的*item*元素識別了一項出版品資源，於其href屬性中提供了IRI[RFC3987]。IRI**可以**為絕對或者相對路徑。在相對IRI的案例中，閱讀系統**必需**將包裝文件的IRI所在位置視為根路徑來解析為絕對IRI。這使得絕對路徑的IRI在*manifest*範圍中必須為唯一。

所有的出版品資源**必需**在*manifest*中被參照，不分本地或者遠端資源。請參考出版品資源位置[EPUB32]以了解按照資源位置對指定媒體類型的需求。

請注意*manifest*非自我參照：**不可**包含一個*item*元素參照到包裝文件自身。

由*item*元素識別的出版品資源**必需**符合由其*media-type*屬性所提供的MIME媒體類型所適用之規格。核心媒體類型資源**必需**使用支援媒體類別[EPUB32]中的媒體類別。

*fallback*屬性使用IDREF [XML]來識別出版品資源可回退到另一個*item*元素。核心媒體類型資源**可以**適用回退。（例如為有腳本的內容文件提供靜態的替代內容）。外部資源的回退需求定義在宣告回退中。

本規格保留的EPUB宣告特性用語供*properties*屬性使用。由其他用語來的詞彙**可以**在添加字首的狀況下使用（請參考保留的字首以取得不需要宣告的字首清單）。

作者**必需**在屬性中對每一個出版品資源宣告所有可適用的描述詮釋資料特性，這麼一來閱讀系統**可以**按照這些設定的特性對顯示進行最佳化（關閉某個排版處理或者使用回退）。閱讀系統**必需**忽視所有無法被辨識的描述詮釋資料特性。

**必需**要有唯一一個*item*使用*nav*特性宣告為EPUB導覽文件。

*media-overlay*屬性使用IDREF [XML]來識別用以解釋該*item*資源的媒體層疊文件。請參考包裝[MediaOverlay32]以了解更多資訊。

> ##### 注意事項
> 
> *manifest*中的*item*元素順序不重要。內容文件的顯示序列由*spine*所提供。
> 

> ##### 範本
> 
> 以下範例呈現*manifest*僅包含核心媒體類型資源
> 
> <manifest>
>    <item id="nav" 
>           href="nav.xhtml" 
>           properties="nav"
>           media-type="application/xhtml+xml"/>
>    <item id="intro" 
>           href="intro.xhtml" 
>           media-type="application/xhtml+xml"/>
>    <item id="c1" 
>           href="chap1.xhtml" 
>           media-type="application/xhtml+xml"/>
>    <item id="c1-answerkey" 
>          href="chap1-answerkey.xhtml" 
>          media-type="application/xhtml+xml"/>
>    <item id="c2" 
>          href="chap2.xhtml" 
>          media-type="application/xhtml+xml"/>
>    <item id="c2-answerkey" 
>          href="chap2-answerkey.xhtml" 
>          media-type="application/xhtml+xml"/>
>    <item id="c3" 
>          href="chap3.xhtml" 
>          media-type="application/xhtml+xml"/>
>    <item id="c3-answerkey" 
>          href="chap3-answerkey.xhtml" 
>          media-type="application/xhtml+xml"/>    
>    <item id="notes" 
>          href="notes.xhtml" 
>          media-type="application/xhtml+xml"/>
>    <item id="cover" 
>          href="./images/cover.svg" 
>          properties="cover-image"
>          media-type="image/svg+xml"/>
>    <item id="f1" 
>          href="./images/fig1.jpg" 
>          media-type="image/jpeg"/>
>    <item id="f2" 
>          href="./images/fig2.jpg" 
>          media-type="image/jpeg"/>
>    <item id="css" 
>          href="./style/book.css" 
>          media-type="text/css"/>   
>    <item id="pls" 
>          href="./speech/dict.pls" 
>          media-type="application/pls+xml"/>
></manifest>

> ###### 範例20
>
> 以下範例呈現*manifest*參照兩個外部資源，使用回退鍊機制來支援替代內容。回退鍊結束於核心媒體類型資源。
> 
> <manifest>
>     <item id="item1" 
>           href="chap1_docbook.xml" 
>           media-type="application/docbook+xml" 
>           fallback="fall1"/>
>     <item id="fall1" 
>           href="chap1.xml" 
>           media-type="application/z3998-auth+xml" 
>           fallback="fall2" />
>     <item id="fall2" 
>           href="chap1.xhtml" 
>           media-type="application/xhtml+xml"/> 
>     … 
> </manifest>

> ###### 範例21
>
> 以下範例呈現在宣告中參照一個遠端的聲音檔案（該聲音在XHTML內容文件中顯示於內文，所以屬於出版品資源）
> 
> XHTML:
> <audio src="http://www.example.com/book/audio/ch01.mp4" controls="controls"/>
> 
> Manifest:
> <item id="audio01"
      href="http://www.example.com/book/audio/ch01.mp4"
      media-type="audio/mp4"/>

> ###### 範例22
> 
> 以下範例呈現對同一個聲音檔案的連結，但在本範例中，檔案未列於宣告中（超連結的遠端資源不屬於出版品資源）。如果作者想要將其用於嵌入在[HTML]內容元素中，本聲音檔案才需要列於宣告中（在作為出版品資源的脈絡下）。

> XHTML:
> <a href="http://www.example.com/book/audio/ch01.mp4">Go to audio file</a>
> 
> Manifest:
> No Entry

> ###### 範例23
> 
> 以下範例呈現對本地版本聲音檔案的連結。因為聲音檔案不是EPUB內容文件，而需要回退到另一個EPUB內容文件（需要列於書脊之中）。
> 
> XHTML:
> <a href="audio/ch01.mp4">Open Audio File</a>
> 
> Manifest:
> <item id="audio01"
>       href="audio/ch01.mp4"
>       media-type="audio/mp4"
>       fallback="#audio01-xhtml"/>

##### 3.4.4.3 宣告回退

外部資源在無法提供明確的回退之下，也**可以**於脈絡中參照（例如，來自列於書脊的*itemref*元素；來自XHTML內容文件的[HTML]*img*、*iframe*以及*link*元素；以及來自CSS樣式表中的*@import*規則）。這些狀況都**必需**提供宣告回退。

宣告回退使用宣告*item*元素中的*fallback*屬性來代表出版品資源。*fallback*屬性的IDREF [XML]值**必需**解析到另一項宣告中的*item*。回退*item*自身可以指定另一個回退*item*，以此類推。

所有ID參照的順序清單可以從某一個項目的fallback屬性開始，代表了該項目的「回退鍊」。該回退鍊中的資源順序代表了作者希望的回退順序。

閱讀系統不用支援回退鍊中所提出出版品資源的媒體類型，但在不支援的資源中，**必需**追朔到至少一個支援的出版品資源。

如果閱讀系統支援回退鍊中的多個出版品資源，**可以**基於該資源的指定特性選擇其一，不然就**應該**尊重作者希望的回退順序。如果閱讀系統不支援任何回退鍊中的資源，則**必需**警告讀者該內容無法被顯示。

回退鍊**必需**適當地符合以下要求其一：

- 對直接來自書脊*itemref*元素的外部資源參照，該鍊**必需**包含至少一個EPUB內容文件。
- 對無法提供明確回退的外部資源，該鍊**必需**包含至少一個核心媒體類型資源。

回退鍊不得包含任何item元素的循環或者自身參照。使用者端遇到第一個參照元素已經被辨識的狀態時，就**必需**中止回退鍊。

回退也**可以**用於為EPUB內容文件的上層內容文件；閱讀系統**可以**選擇活用這樣的回退機制以找尋到所給予脈絡中最適宜的內容文件版本。活用這項功能的範例，如提供具備腳本內容[ContentDocs32]的回退。

##### 3.4.4.4 *bindings*元素 (不再推薦)

*bindings*元素定義了一系列對本規格不支援媒體類型的處理程序。不再推薦使用。

請參考[Publications301]了解本元素的更多資訊。

#### 3.4.5 書脊（spine）

##### 3.4.5.1 *spine*元素

*spine*元素定義了宣告中*item*參照的排序清單，表達該內容解釋的預設閱讀順序。

> ###### 元素名稱
> 
> *spine*
> 
> ###### 用法
> 
> **必需**為*package*的第三個子元素，緊接在*manifest*之後。
> 
> ###### 屬性
> 
> *id [選擇性]*
> 
> *page-progression-direction [選擇性]*
>  
> *toc [選擇性] (遺存)*
> 
> ###### 內容模型
> 
> *itemref [一或多個]*

閱讀系統**必需**提供按照定義在*spine*中的順序來排出內容解釋版面的手段，包括：１）辨識第一個主要itemref做為預設閱讀順序的開始，以及２）按照*spine*給出的順序接續第一個項目排版。

所有超連結到列於*spine*中出版品資源的出版品資源必需列於*spine*之中，超連結定義為任何連結機制需要使用者從現在資源中跳出的導覽方式。一般的超連結機制包含[HTML]中*a*以及*area*元素和腳本化連結（例如使用DOM事件及/或form元素）的*href*屬性。對列出超連結資源的要求適用於迴圈（即為，所有的出版品資源連結到被連結的出版品資源都需要被列出，以此類推）。

所有超連結到EPUB導覽文件的出版品資源也必需要列於*spine*，無論導覽文件自身是否被列於*spine*。

> ##### 注意事項
> 
> 透過超連結參照的遠端資源並非出版品資源，所以不再需要包含於書脊的需求之內（例如網頁與資源）。

嵌入出版品資源（例如，透過[HTML]*iframe*元素）不需要列於*spine*中。

*page-progression-direction*屬性設定了全域的內容行進方向。可接受的值為*ltr*（左向右）、*rtl*（右向左）以及*default*。當辨識為*default*時，代表作者沒有偏好，所以閱讀系統可以選擇排版方向。*default*值**必需**假設該屬性沒有指定。於此狀況下，閱讀系統**應該**基於第一個*language*元素，挑選一個預設的*page-progression-direction*。

因為*page-progression-direction*屬性設定了全域的行進方向，個別內容文件以及部分內容文件**可以**複寫該項設定（例如透過CSS *writing-mode*特性）。閱讀系統**可以**提供機制以覆蓋預設方向（例如，透過按鍵或者設定來允許套用替代樣式表）。

閱讀系統**必需**忽略*pre-paginated*的XHTML內容文件的行頁方向。page-progression-direction屬性定義了固定版面頁面到下一頁的行進方向。

遺存的*toc*屬性使用IDREF [XML]識別宣告項目中的NCX。

##### 3.4.5.2 itemref元素

*spine*的*itemref*子元素表示出版品資源的序列清單（標準上為EPUB內容文件）。*itemref*元素的順序定義了該內容解釋預設的閱讀順序。

> ###### 元素名稱
> 
> *itemref*
> 
> ###### 用法
> 
> *spine*元素的子元素，可以重複。
> 
> ###### 屬性
> 
> *id [選擇性]*
> 
> *idref [必需]*
> 
> *linear [選擇性]*
> 
> *properties [選擇性]*
> 
> ###### 內容模型
> 
> 空白

每一個*itemref元*素**必需**指向宣告中的唯一*item*，其ID[XML]需要與其*idref*屬性的IDREF[XML]一致。（即是，不能有兩個或以上的*itemref*元素指向相同的*item*）。

每一個被指向的宣告*item***必需**同時為ａ）一個EPUB內容文件或者ｂ）另一種類型的出版品資源，其無論是否為核心媒體類型資源或者外部資源，都**必需**在其回退鍊中包含一個EPUB內容文件。

> ##### 注意事項
> 
> 雖然EPUB出版品需要包含一個EPUB導覽文件，但不強制包含在*spine*之中。

*linear*屬性只是是否參照的*item*是否包含建構主要閱讀順序的內容，以及是否要被依序閱讀（"*yes*"），或者為用來增強補添主要內容的輔助內容，並且可以在序列之外被存取（"*no*"）。輔助內容範例包括：注意事項、解說以及答案等。

*linear*屬性讓閱讀系統得以區別內容是否為預設閱讀順序中，使用者需要存取的一部分，或者可能是補充用內容，例如，顯示一個跳出視窗或者從朗讀處理中跳過。

當處理一本EPUB出版品時，閱讀系統**可以**跳過非線性的內容，而不會出現在預設閱讀順序，也可以忽視*linear*屬性，讓使用者接觸整本EPUB出版品的全部內容。本規格不指定閱讀系統需使用何種模式。閱讀系統也可以提供選項，讓使用者於兩種模式間切換。

每一份內容解釋都**必需**包含至少一個*itemref*，其*linear*屬性的值為未標示或者明確指定為"*yes*"，一個沒有*linear*屬性的*itemref*假設其值為"*yes*"。

作者**必需**提供存取所有非線性內容的方法（例如，內容內加入超連結或者透過EPUB導覽文件）。

本規格保留EPUB書脊特性用語供properties屬性使用。由其他用語來的詞彙**可以**在添加字首的狀況下使用（請參考保留的字首以取得不需要宣告的字首清單）

所有定義於書脊特性用語中，適用的描述性詮釋資料特性**應該**被宣告。

閱讀系統**必需**忽視所有無法辨識，在propertirs屬性中表述的詮釋資料特性。

##### 範本

> ###### 範例24
> 
> 以下範例呈現一個呼應上面範例宣告的spine元素。
> 
> 
> <spine page-progression-direction="ltr">
>     <itemref idref="intro"/>
>     <itemref idref="c1"/>
>     <itemref idref="c1-answerkey" linear="no"/>
>     <itemref idref="c2"/>
>     <itemref idref="c2-answerkey" linear="no"/>
>     <itemref idref="c3"/>
>     <itemref idref="c3-answerkey" linear="no"/>
>     <itemref idref="notes" linear="no"/>
> </spine>

#### 3.4.6 集合（collections）

##### 3.4.6.1 collection元素

*collection*元素定義了一組相關的資源。

> ###### 元素名稱
> 
> *collection*
> 
> ###### 用法
> 
> *package*的選擇性第六個元素，可以重複。
> 
> ###### 屬性
> 
> *dir [選擇性]*
> 
> *id [選擇性]*
> 
> *role [必需]*
> 
> *xml:lang [選擇性]*
> 
> ###### 內容模型
> 
> 依此順序：*metadata [零或壹]*, ( *collection [一或多]* 或 ( *collection [零或多]*, *link [一或多]* ))

*collection*元素能夠將資源組成邏輯上的群組做為各種潛在用途：讓被切分為多個EPUB內容文件的內容重組為一個有意義的單元（例如橫跨多個文件的索引）、識別供特殊目的使用的資源（例如預覽內容），或者將資源組合在一起來表示該內容解釋的額外資訊。

*collection*元素，如本章節定義，用以表達一個一般化的框架用來取得特化的內容（例如，透過EPUB子規格）。這些特化的內容必需在內容解釋中定義*collection*元素的目的，也須在製作與使用上符合需求（特別是那些不同於以下所列一般化框架的規則）。

每一個特化的內容都必需定義一個角色值，在所有適用的*collection*元素中為唯一識別。包裝文件中每一個*collection*元素的角色**必需**在其*role*屬性中被識別，其值**必需**為一或多個NMTOKENs [XMLSCHEMA-2]及/或絕對IRIs [RFC3987]。角色中使用NMTOKEN的值為反向，也未定義在EPUB中，而由[RoleRegistry]所維護。未定義在註冊中的值不符合規範，本章節不定義任何角色。

第三方**可以**為*collection*元素定義客製化角色，但這些角色**必需**使用絕對IRIs來識別。客製化角色不得在其識別IRI的host component中包含字串"idpf.org"。

> ##### 注意事項
> 
> 為了協助跨閱讀系統的客製化角色互通性，強烈鼓勵實作者在將實際使用*collection*元素的狀況記載到[RoleExtensions]。

選擇性作為*collection*的*metadata*子元素爲包裝*metadata*元素的挪用，需要遵循以下語法與語意的差異：

- 所有詮釋資料預設不強制套用。
- 包裝層級對詮釋資料元素的限制**可以**被覆蓋。
- 所有主要詮釋資料表述適用於*collection*。
- *refines*屬性**不得**參照外於*collection*的元素。
- 不得包括OPF2*meta*元素。

*collection*可以透過包含一或多個子*collection*元素來定義子集合。

*collection*的*link*子元素為詮釋資料*link*元素的挪用，需要遵循以下語法與語意的差異：

- *rel*屬性為**選擇性**。
- *properties*屬性也接受沒有字首的宣告*item*特性（即為，如此集合中可以宣告自己的導覽文件或者封面圖片）。
- 不得附加*refines*屬性。

*collection*元素的特化**可以**透過定義於以上的需求來更有效地打造，以反映其需求（例如，要求詮釋資料、對於元素與屬性的使用賦予進一步的限制，或者讓*link*元素的順序更為明顯）。然而，最終的內容模型必需為合乎規定的本章節定義子集之一（例如特化不可以提出新的元素或者屬性，或者重新提出前面禁止使用的元素）。特化不得以集合定義來覆蓋*manifest*與*spine*的規則。

在本規格的脈絡下，閱讀系統支援集合為**選擇性**。閱讀系統**必需**在無法辨識所定義角色的狀況下忽略*collection*元素。

內容解釋排版時**不得**依存對collection元素的解析。內容**必需**在沒有丟師資炫或者其他明顯劣化的狀況下依然能被使用者所閱讀。

##### 範本

> ###### 範例25
> 
> 以下範例呈現如何組合兩個XHTML內容文件已表示為一個單一元件。
> 
> <package …>
>     …
>     <collection role="http://example.org/roles/unit">
>         <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>             <dc:title>Foo Bar</dc:title>
>         </metadata>
>         <link href="EPUB/xhtml/foo-1.xhtml"/>
>         <link href="EPUB/xhtml/foo-2.xhtml"/>
>     </collection>
>     …
> </package>

#### 3.4.7 遺存（Legacy）

##### 3.4.7.1 *meta*元素

*meta*元素[OPF2]是一個遺存功能，之前為提供包含一般性詮釋資料的手段。在EPUB 3中被更新的*meta*元素所取代，有著不同的屬性與必需的文字內容。

若要了解更多關於*meta*元素，請參考[OPF2]中的定義。

##### 3.4.7.2 *guide*元素

*guide*元素[OPF2]是一個遺存功能，之前為EPUB出版品提供機器可處理的關鍵架構導覽。在EPUB 3中被導覽文件的landmarks所取代。

若要了解更多關於*guide*元素，請參考[OPF2]中的定義。

##### 3.4.7.3 NCX

NCX[OPF2]是一個遺存功能，之前為EPUB出版品提供目次。在EPUB 3中被導覽文件所取代。

若要了解更多關於NCX，請參考[OPF2]中的定義。

## 4. 包裝詮釋資料

### 4.1 出版品識別碼

#### 4.1.1 獨特識別碼

作者有責任要在包裝文件中的詮釋資料包含一個主要識別碼，每一本EPUB出版品都需要獨特的識別碼。獨特識別碼，無論是挑選或者指派，都必需保存在*dc:identifier*元素中，並且在*package*元素的*unique-identifier*屬性中被參照為獨特識別碼。

就算非固定，一本EPUB出版品的獨特識別碼**應該**盡可能地不受變更。新的識別碼**不應**在更新詮釋資料、更正錯誤、或者其他對EPUB出版品的小修改時發行。

閱讀系統**不得**依靠獨特識別碼作為辨識EPUB出版品唯一性的依據。若要判斷是否兩個擁有同樣獨特識別碼的EPUB出版品是否為同一份出版品（見發布識別碼）還是不同出版品，可能需要檢查其他詮釋資料，如書名或者作者。

#### 4.1.2 發布識別碼

EPUB出版品的獨特識別碼一般**不應**隨著包裝或其內容的小更改而變動，獨特識別碼設計應該有最大限的持續性，無論是供參考或者發行用途。一本EPUB出版品的每次發行都需要被識別為獨特的新版本，故此，結論上需要一個可以被信任及可以變更的獨特識別碼。

為了在不變更獨特識別碼的狀況下處理辨識小改版與發行的問題，本規格定義了「發布識別碼」的語意，或者用以區別及序列排序具有同一個獨特識別碼的EPUB出版品之手段。

發布識別碼並非在包裝*metadata*區塊中的實際特性，但卻是可以從其他兩個必須的詮釋資料獲取的值：獨特識別碼與內容解釋最後修改日期。當一起取得時，所結合的值可以作為一個獨特識別用以區別EPUB出版品的任何不同版本。

為確保發布識別碼能被建構，每一個內容解釋都**必需**包含唯一的[DCTERMS]*modified*特性包含其最後修改日期。該特性的值**必需**為一個[XMLSCHEMA-2]日期時間，適用以下形式：

CCYY-MM-DDThh:mm:ssZ

最後修改日期**必需**以世界協調時間（UTC）表述，也**必需**以「Ｚ」（Zulu）時區識別作結。

附加的修改特性**可以**包含在包裝詮釋資料中，但**必需**有不同目的（例如，需要一個*refines*屬性參照到一個元素或者資源）。

儘管並非包裝詮釋資料的一部分，為了參照或起其他用途，所有識別碼的字串表現形式都**必需**使用at（@）作為區分符號來建構（例如，以此形式「id@日期」。當連結字串時，空白**不得**包含在內。

> ###### 範例26
> 
> 以下範例呈現如何結合獨特別碼與修改日期為發布識別碼形式。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:identifier id="pub-id">urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809</dc:identifier>
>     <meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>
>     …
> </metadata>
> 
> 包裝ID的結果為：
> 
> urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809@2011-01-01T12:00:00Z

注意區分符號**可以**出現在獨特識別碼中，這些識別碼**可以**為任何字串值。發布識別碼結果上，要分解成組成元件時，**必需**以最後一個at符號來分割。

發布識別碼不優先於獨特識別碼，但能供發佈管道以及閱讀系統用以區分識別相同EPUB出版品的不同版本。在不具這樣精確的識別碼知識時，也應用格式中的時間標記來排序、依時序排列。

發布識別碼結果上允許一組EPUB出版品能被檢驗並且判斷他們是否為同一本出版品的相同版本、同一本EPUB出版品的不同版本，或者和相似或者不同EPUB出版品的組合。

> ##### 注意事項
> 
> 當一個EPUB容器包含一個EPUB出版品多於一個的內容解釋時，請在每次發布時更新預設內容解釋的最後修改日期——就算沒有更新——也能協助確保EPUB出版品不會和前一次發布的被視為相同版本，閱讀系統僅需處理預設內容解釋。

### 4.2 用語關聯機制

#### 4.2.1 導論

本章節為非規範性。

*property*、*properties*、*rel*及*scheme*屬性用於特性資料類型可透過詮釋資料用語來表意。和CURIE [RDFA-CORE]一樣，特性資料類型可IRI [RFC3987]作為精簡形式表達，簡化使用標準化用語發布詮釋資料。

特性的值表述上常態包含一個字首以及一個參照，字首——無論是字面還是隱含——是映射到一個IRI的捷徑，通常可解析到一個用語詞彙。當字首轉化到其IRI表意並且與參照結合時，結果可使IRI被一般化解析為用語斷片，包含該詞彙的人讀和/或機讀資訊。

為協助閱讀系統處理特性值，本規格定義了三種機制來建立IRI與字首的對應：

- 預設用語：定義當特性值不包含字首時該如何映射；
- 保留字首：這些映射為預先定義（即為，所有閱讀系統都應該識別）且可不需宣告而使用；以及
- *prefix*屬性：用以在根*package*元素宣告新字首映射的手段。

#### 4.2.2 預設用語

預設用語為不需要宣告字首就可以使用其詞彙的用語，而其詞彙**必需**永遠都無需字首。

包裝文件有著多個彼此無相關的詮釋資料詞彙用法，單一預設用語並非為所有屬性所定義。相對之下，不同的預設用語定義供屬性使用可接受的特性資料類型如下：

- Meta特性用語定義為*meta property*屬性的預設用語。\
若屬性的值不包含字首，則必須要從以下IRI[RFC3987]主幹中獲得結果IRI：http://idpf.org/epub/vocab/package/meta/#

- 詮釋資料連結用語定義為*link rel*以及*properties*屬性的預設用語。\
若其中任何屬性的值不包含字首，則必須要從以下IRI[RFC3987]主幹中獲得結果IRI：http://idpf.org/epub/vocab/package/link/#

- 宣告特性用語定義為*item properties*屬性的預設用語。\
如果其中任何屬性的值不包含字首，則必須要從以下IRI[RFC3987]主幹中獲得結果IRI：http://idpf.org/epub/vocab/package/item/#

- 書脊特性用語定義為*itemref properties*屬性的預設用語。\
如果其中任何屬性的值不包含字首，則必須要從以下IRI[RFC3987]主幹中獲得結果IRI：http://idpf.org/epub/vocab/package/itemref/#

與這些用語連結的IRI們**不得**使用*prefix*屬性指派字首。

#### 4.2.3 保留字首

本規格保留以下字首組，作者**可以**用於包裝詮釋資料而不需宣告。

> ###### 警告
> 
> 儘管保留字首是為了製作時的便利，依賴他們會造成相容性問題。例如，驗證工具可能經常性地推回新的字首直到更新。強烈建議作者宣告所有字首以避免這些狀況發生。

字首 | IRI
------- | -------
a11y	 | http://www.idpf.org/epub/vocab/package/a11y/#
dcterms | http://purl.org/dc/terms/
marc | 	http://id.loc.gov/vocabulary/
media | http://www.idpf.org/epub/vocab/overlays/#
onix | http://www.editeur.org/ONIX/book/codelists/current.html#
rendition | http://www.idpf.org/vocab/rendition/#
schema | http://schema.org/
xsd | http://www.w3.org/2001/XMLSchema#

閱讀系統**必需**以其預先定義的URI來解析所有用於包裝文件的保留字首，除非有本地字首被宣告。保留字首**不應**在prefix屬性中被覆蓋，但閱讀系統**必需**當遇到這些本地覆蓋時必須套用。

當保留字首有變更時，閱讀系統不會總是同步更新，閱讀系統遇到無法辨識的字首時，不得失敗（即為，既非保留，也沒使用*prefix*屬性宣告）。

#### 4.2.4 prefix屬性

*prefix*屬性定義了本規格未保留、額外的字首映射。

*prefix*屬性的值是由空白分隔的清單，內有一或多個字首與IRI的映射，以此形式：

<small>(EBNF productions ISO/IEC 14977)<br />所有結束符號位於Unicode區塊「基本拉丁字母區」(U+0000 to U+007F)<small>

 |  | 
------- | ------- | -------
prefixes | = | mapping , { whitespace, { whitespace } , mapping } ;	 
mapping | = | prefix , ":" , space , { space } , ? xsd:anyURI ? ;	 
prefix | = | ? xsd:NCName ? ;	 
space | = | #x20 ;	 
whitespace | = | (#x20 | #x9 | #xD | #xA) ;	 

> ###### 範例27
> 
> 以下範例呈現使用*prefix*屬性宣告字首朋友的朋友(*foaf*)以及DBPedia (*dbp*)用語。
> 
> <package … 
> 	prefix="foaf: http://xmlns.com/foaf/spec/
> 		 dbp: http://dbpedia.org/ontology/">
> 	…
> </package>

為了避免衝突，*prefix*屬性**不得**宣告映射到預設用語的字首。如果*prefix*屬性包含對預定義字首的宣告，閱讀系統必需使用*prefix*屬性中的URI映射定義，無論預定義的字首是否映射到相同的URI。

字首「_」不得被宣告，其已經被保留供未來處理RDFa [RDFA-CORE]的相容性。

為了保障包裝文件未來對替代序列化的相容性，**不得**透過*prefix*屬性宣告供都柏林核心集使用的字首 /elements/1.1/ 命名空間 [DCTERMS]。作者**必需**僅使用准許在包裝文件詮釋資料中使用的[DC11]元素。

#### 4.2.5 特性（*property*）資料類別

##### 4.2.5.1 語法

特性資料類型是一個簡潔的手段，用於表述一個IRI[RFC3987]也可透過分號添加**選擇性**的字首。

<small>(EBNF productions ISO/IEC 14977)<br />所有結束符號位於Unicode區塊「基本拉丁字母區」(U+0000 to U+007F)<small>

 |  | 
------- | ------- | -------
property | = | [ prefix , ":" ] , reference;	 
prefix | = | ? xsd:NCName ? ;	 
reference | = | ? irelative-ref ? ;	/* as defined in [RFC3987] */

特性資料類型由定義於[RDFA-CORE]的CURIE資料類型延伸，作為CURIEs的子集。

> ###### 範例28
> 
> 以下範例呈現一個由字首*dcterms*以及參照*modified*組成的特性值。
> 
> <meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>

處理之後，該特性可透過以下IRI擴張：

http://purl.org/dc/terms/modified

*dcterms:*字首為保留字首映射到IRI"http://purl.org/dc/terms/"。

當一個字首在特性值中被忽略，所表達的參照表達了來自預設用語供該屬性使用的詞彙。

> ###### 範例29
> 
> 以下範例呈現在宣告*item*元素中使用的*mathml*特性。
> 
> <item … properties="mathml"/>
> 
> 該特性可擴張到：
> 
> http://idpf.org/epub/vocab/package/item/#mathml
> 
> 使供該用語的IRI連結到參照。

空白字串不表示合法的特性值，就算合乎以上定義亦然。

##### 4.2.5.2 處理方式

閱讀系統**必需**使用以下規則來由一個特性中建立IRI[RFC3987]：

- 如果特性僅包含參照，IRI透過其IRI主幹取得預設用語到參照。
- 如果特性包含一個字首和參照，IRI透過其IRI主幹取得字首到參照。如果沒有受定義的匹配字首，該特性為不符規定，**必需**被忽視。

結果得到的IRI必需合乎[RFC3987]。然而，閱讀系統不需解析該IRI。

### 4.3 包裝顯示詮釋資料

#### 4.3.1 導論

本章節為非規範性。

並非所有的顯示資訊都能透過EPUB建立時所依靠的技術。例如，儘管HTML與CSS提供了強烈的排版能力，但這些能力受到文件排版目標的限制。

本章節定義了一般目的的特性，允許作者表示包裝層級的顯示意圖（例如，僅能由EPUB閱讀系統所實作的功能）。如果閱讀系統支援期望的排版，這些特性可讓使用者看到作者理想上設計的內容。

#### 4.3.2 參考

這些特性所參照的基礎IRI為：*http://www.idpf.org/vocab/rendition/#*.

「*rendition:*」字首為了包裝顯示特性而保留，而不需於包裝文件中宣告。

#### 4.3.3 一般特性

##### 4.3.3.1 rendition:flow特性

*rendition:flow*特性指定作者的偏好，讓閱讀系統知道該怎麼處理內容流動。

###### 4.3.3.1.1 用法

當*rendition:flow*特性在*meta*元素中指定時，其指出作者對全域內容流動處理的偏好（如，對所有書脊項目）。作者**可以**只是其偏好為動態分頁或者捲軸顯示。對捲軸顯示內容，也可以是否連接的EPUB內容文件要被一起排版作為連續捲動顯示，或者彼此應該分別排版顯示（例如，中間有著動態分頁）。

如果閱讀系統支援這樣只是的排版，其**應該**使用該方式處理流動內容，但**可以**提供選項供使用者覆蓋這樣要求的排版方式。

在*metadata*區塊中，沒有*meta*元素包含本特性時，預設值*auto***必需**被閱讀系統推測為全域值。閱讀系統**可以**僅支援此預設值。

如果閱讀系統支援*rendition:layout*特性，則在一個書脊項目同時被指定*rendition:layout*值為*pre-paginated*時，**必需**忽略*rendition:flow*特性

請注意當兩個可重排的EPUB內容文件依序出現在書脊時，預設對其[HTML] *body*元素的排版須為一致，當遇到*page-break-before*[CSSSnapshot]特性時，必須被設定為*always*。此外，在使用*rendition:flow*特性時，作者**可以**透過適當的樣式表宣告覆蓋其特性，只要閱讀系統支援覆蓋手段。

*rendition:flow***不可**被宣告超過一次。

###### 4.3.3.1.2 允許的值

以下值定義可供*rendition:flow*特性使用：

**paginated**
閱讀系統**應該**將所有流動內容動態分頁。

**scrolled-continuous**
閱讀系統**應該**將所有具流動內容的內容文件設定為捲軸顯示，EPUB出版品由其內容解釋表現**應該**被呈現為一個連續捲動形式，由一個書脊項目往下一個（除了部分覆蓋之外）。

請注意作者**不應**製作不同有著不一樣區塊流動方向的資源的出版品，這樣連續捲動的內容解釋在EPUB閱讀系統中會出問題。

**scrolled-doc**
閱讀系統**應該**將所有具流動內容的內容文件設定為捲軸顯示，每一個書脊項目**應該**被呈現為分隔的捲軸文件。

**auto**
作者對於流動處理沒有偏好。閱讀系統**可以**將流動內容以其預設方式或者使用者設定，取任一可適用者排版呈現。

###### 4.3.3.1.3 覆蓋書脊

作者**可以**對書脊*itemref*元素個別指定以下特性來讓書脊項目覆蓋全域值：

**flow-auto**
指定作者對流動內容處理沒有特別偏好。

**flow-paginated**
指定作者偏好對流動內容採動態分頁。

**flow-scrolled-continuous**
指定作者偏好對流動內容提供捲軸顯示，同時接續的書脊項目有此特性，要被排為連續捲軸。

**flow-scrolled-doc**
指定作者偏好對流動內容提供捲軸顯示，同時每個書脊項目有此特性，要配排成分隔的捲軸文件。

每一個書脊項目都僅允許使用一個特性覆蓋。

對*rendition:flow-scrolled-continuous*特性，捲軸方向定義關聯在itemref元素所參照的XHTML內容文件之根元素之區塊流動方向。如果當區塊流動方向向下（由上而下），捲軸方向就為垂直。如果跟元素的區塊流動方向是向右（由左而右）或者向左（由右而左），就為水平。

###### 4.3.3.1.4 範本

> ###### 範例30
> 
> 以下範例展示一個作者意圖想要讓分頁的內容解釋擁有可捲動的目次。
> 
> <metadata>
>     <meta property="rendition:flow">paginated</meta>
> </metadata>
> 
> <spine>
>     <itemref idref="toc" properties="rendition:flow-scrolled-doc"/>
>     <itemref idref="c01"/>
> </spine>

##### 4.3.3.2 *rendition:align-x-center*特性

*rendition:align-x-center*特性指定了該書脊項目在viewport或者跨頁時，應該要被水平置中。

當*rendition:align-x-center*特性設置在書脊項目中，其指出了，若可以適用，內容排版在viewport或者跨頁**應該**被水平置中。本項特性並不影響書脊項目的排版，僅影響內容盒中的位置。

對可重排的內容而言，閱讀系統支援這項特性則必須在每一個虛擬的頁面都置中。

本規格版本未定義當本特性不支援或未指定時預設的排版行為。閱讀系統**可以**以自己的設計排列書脊項目。

> ##### 注意事項
> 
> 本特性開發主要用於處理"Naka-Tobira (中扉)"（章節標題頁），因為內容排版缺乏可靠置中控制項。對分頁媒體的支援主要靠CSS推薦，所以，本特性預期會不再支援。建議作者在可以使用CSS方案處理時改用。

#### 4.3.4 固定版面特性

##### 4.3.4.1 導論

本章節為非規範性。

EPUB文件，不像印刷書或者PDF檔案，是為了變動而設計，內容流動或者可重排以適應螢幕或者使用者需求。如同排版與CSS的注意事項「內容呈現要適應讀者，而不是讓讀者得要適應特別的內容呈現。」[EPUB3Overview]

但本原則不適用於所有類型的文件。有時候內容與設計彼此交纏而無法切分。任何對外觀的變更都可能改變意義或者失去所有意義。固定版面文件提供作者對顯示更大的控制，尤其在重排EPUB無法適用於內容時。

本章節定義了一組詮釋資料特性，在EPUB脈絡下，允許宣告性表述固定版面文件的預期排版行為。

> ##### 注意事項
> 
> EPUB 3具備顯示固定版面內容的多重機制。當固定版面內容有必要時，作者對機制的選擇將依靠於多種現實，包括希望的精準程度、檔案大小、無障礙功能等。本章節不試圖指示作者如何做機制的選擇。

##### 4.3.4.2 rendition:layout特性

*rendition:layout*特性指定了該內容解釋為重排或者預先分頁。

###### 4.3.4.2.1 用法

當*rendition:layout*在*meta*元素中指定時，其指示了整個內容解釋該為分頁或者重排版面形式（即套用於所有書脊項目）。

預設值*reflowable*當在*metadata*區塊中沒有*meta*元素乘載這項特性時，EPUB閱讀系統**必需**視為全域值。

當*rendition:layout*特性設定為*pre-paginated*時，閱讀系統**不得**在排版同步跨頁中加入調整內容的空白隙縫。

當書脊項目的值設定為pre-paginated時，其內容空間必需被設定如固定版面的定義[ContentDocs32]。

*rendition:layout*特性**不得**被宣告多於一次。

###### 4.3.4.2.2 允許的值

以下值被定義供*rendition:layout*特性使用：

**reflowable**
該內容解釋不是預先分頁。閱讀系統**可以**排版時可套用動態分頁。

**pre-paginated**
該內容解釋為預先分頁。閱讀系統**必需**在排版時將每一個書脊項目處理成正好一頁。

> ##### 注意事項
> 
> 閱讀系統一般限制或者拒絕套用使用者或者使用者代理樣式表到預先分頁的文件上，所以，這樣的文件得依靠固有的特性，動態樣式改變極為容易造成非預期的結果。作者選擇使用預先分頁來取代重排內容時，需要對這樣限制造成的使用性以及無障礙輔助性的負面結果負責。請參考基準1.4——提供文字組態[UAAG20]以獲得相關資訊。

###### 4.3.4.2.3 覆蓋書脊

作者**可以**對書脊*itemref*元素個別指定以下特性來覆蓋書脊項目的全域值：

**layout-pre-paginated**
指定該書脊項目為預先分頁。

**layout-reflowable**
指定該書脊項目為重排內容。

一個書脊項目僅允許套用一個覆蓋。

###### 4.3.4.2.4 範本

> ###### 範例31
> 
> 以下範例展示完整的固定版面內容，使用[CSS3-MediaQueries]在不同裝置分類時套用不同的樣式表。請注意媒體查詢僅影響套用該文件的樣式表，設定在*viewport meta*標籤中的內容區域依然為固定
> 
> **包裝文件**
> 
> <meta property="rendition:layout">pre-paginated</meta>
> 
> **XHTML**
> 
> <head>
>     <meta name="viewport" content="width=1200, height=900"/>
> 	
>     <link rel="stylesheet" href="eink-style.css" media="(max-monochrome: 3)"/>
>    <link rel="stylesheet" href="skinnytablet-style.css" media="((color) and
>        (max-height:600px) and (orientation:landscape), (color) and (max-width:600px)
>        and (orientation:portrait))"/>
>    <link rel="stylesheet" href="fattablet-style.css" media="((color) and
>        (min-height:601px) and (orientation:landscape), (color) and (min-width:601px)
>        and (orientation:portrait)"/>	
> </head>

##### 4.3.4.3 rendition:orientation特性

*rendition:orientation*特性指定作者希望該內容解釋排版時的頁面方向。

###### 4.3.4.3.1 用法

當指定於*meta*元素時，其指示意圖要套用在內容解釋全域的頁面方向（即為，所有書脊項目）。

當在*metadata*區塊中沒有*meta*元素指定本特性時，預設值*auto***必需**由閱讀系統推測設定為全域值。

*rendition:orientation*特性**不得**宣告多於一次。

###### 4.3.4.3.2 允許的值

以下值被定義供*rendition:orientation*特性使用：

**landscape**
該內容解釋指示排版成landscape（橫寬直窄）。

**portrait**
該內容解釋指示排版成portrait（橫窄直寬）。

**auto**
該內容解釋不受方向指定。

支持多重頁面方向的閱讀系統**應該**傳達意圖的頁面方向給使用者，除非給出的值為*auto*。意味著其意向由實作所指定。

###### 4.3.4.3.3 覆蓋書脊

作者**可以**對書脊*itemref*元素個別指定以下特性來覆蓋書脊項目的全域值：

**orientation-auto**
指定閱讀系統可決定如何排列書脊項目的方向。

**orientation-landscape**
指定該書脊項目應該以landscape（橫寬直窄）方向排列

**orientation-portrait**
指定該書脊項目應該以portrait（橫窄直寬）方向排列

一個書脊項目僅允許套用一個覆蓋。

###### 4.3.4.3.4 範本

> ###### 範例32
> 
> 以下範例展示完整的固定版面內容，意圖不以自動跨頁排版，而鎖定在landscape（橫寬直窄）方向。
> 
> 
> <metadata>
>     <meta property="rendition:layout">pre-paginated</meta>
>     <meta property="rendition:spread">none</meta>
>     
>     <meta property="rendition:orientation">landscape</meta>
> </metadata>

##### 4.3.4.4 rendition:spread特性

*rendition:spread*特性指示該內容解釋在閱讀系統同步跨頁行為的意圖。

###### 4.3.4.4.1 用法

當*rendition:spread*指定於*meta*元素時，其指定了套用內容解釋全域的同步跨頁行為的意圖（即為，所有書脊項目）。

當在*metadata*區塊中沒有*meta*元素指定本特性時，預設值*auto***必需**由閱讀系統推測設定為全域值。

*rendition:spread*特性**不得**宣告多於一次。

###### 4.3.4.4.2 允許的值

以下值被定義供*rendition:spread*特性使用：

**none**
閱讀系統**不得**對包含的書脊項目做同步跨頁。

**landscape**
閱讀系統只有在裝置為landscape（橫寬直窄）方向時，**應該**對書脊項目做同步跨頁排版。

**portrait (不再推薦)**
僅在portrait（橫窄直寬）方向時跨頁不再推薦。

作者建議使用"*both*"值取代，如此跨頁不僅在portrait方向時可以讀，在landscape時也可讀。閱讀系統**應該**將"*portrait*"值視為"*both*"的同義詞，無論方向都創造跨頁。

**both**
閱讀系統**應該**不管裝置方向做同步跨頁排版。

**auto**
沒有明確的同步跨頁行為定義。閱讀系統**可以**在特別或者所有裝置方向使用同步跨頁，作為內容顯示區域最佳化利用的程序。

> ##### 注意事項
> 
> 當同步跨頁用於HTML及SVG內容文件的脈絡時，透過*viewport meta*元素[ContentDocs32]以及*viewBox*屬性[ContentDocs32]提供的空間代表跨頁中一頁的尺寸，應予尊重。

> ##### 注意事項
> 
> 請參考書脊以獲得關於全域流動方向宣告的資訊，包括使用*page-progression-direction*屬性，以及在內容文件中指定個別page-progression-direction。

###### 4.3.4.4.3 覆蓋書脊

作者**可以**對書脊*itemref*元素個別指定以下特性來覆蓋書脊項目的全域值：

**spread-auto**
指定閱讀系統決定何時該對書脊項目做同步跨頁。

**spread-both**
指定閱讀系統應該在portrait與landscape兩方向都對書脊項目做同步跨頁。

**spread-landscape**
指定閱讀系統應該僅在landscape方向對書脊項目做同步跨頁。

**spread-none**
指定閱讀系統不應對書脊項目做同步跨頁。

**spread-portrait**
*spread-portrait*特性不再推薦。請參考[Publications301]之定義以獲得更多資訊

一個書脊項目僅允許套用一個覆蓋。

###### 4.3.4.4.4 範本

> ###### 範例33
> 
> 以下範例展示完整的固定版面內容，意圖在landscape方向使用同步跨頁，並且在portrait方向不跨頁。
> 
> <metadata>
>     <meta property="rendition:layout">pre-paginated</meta>
>     <meta property="rendition:spread">landscape</meta>
> </metadata>

> ###### 範例34
> 
> 以下範例展示重排內容伴隨單一固定版面標題頁，固定版面頁面在裝置排版為同步跨頁時，意圖置放在右手邊的跨頁區塊。
> 
> <metadata>
>     <meta property="rendition:layout">reflowable</meta>
>     <meta property="rendition:spread">auto</meta>
> </metadata>
> 
> <spine>
>     <itemref idref="titlepage" properties="page-spread-right rendition:layout-pre-paginated"/>
> </spine>

##### 4.3.4.5 rendition:page-spread-* 特性

###### 4.3.4.5.1 用法

當閱讀系統進行同步跨頁排版時，預設行為是填充到跨頁，透過將下一個EPUB內容文件排版放置到下一個未被填充的viewport中。下一個可用的viewport取決於內容文件中所給予的個別行頁方向。作者**可以**覆蓋此項自動填充行為，透過在書脊*itemref*元素指定以下特性強制一份文件被置放在特定的viewport中。

***rendition:page-spread-center***
*rendition:page-spread-center*特性指定強制將內容文件置放於一個同步跨頁中。

***rendition:page-spread-left***
*rendition:page-spread-left*特性為*page-spread-left*特性的捷徑。

***rendition:page-spread-right***
*rendition:page-spread-right*特性為*page-spread-right*特性的捷徑。

*rendition:page-spread-left*特性指出該書脊項目**應該**被排版置放於跨頁的左手邊空格，以及*rendition:page-spread-right* **應該**被排版置放於右手邊空格。*rendition:page-spread-center*特性指出同步跨頁模式**應該**被覆蓋，而以單一viewport排版並且置放於螢幕的中央。

*rendition:page-spread-left*、*rendition:page-spread-right*以及*rendition:page-spread-center*特性適用於預先分頁與重排內容兩方，他們都只適用於閱讀系統創建同步跨頁。

*rendition:page-spread-* * 特性無論XHTML內容文件中*page-break-before*特性[CSSSnapshot]的值為何，都優先其處理。

> ##### 注意事項
> 
> *rendition:page-spread-center*並不改變viewport空間。特別指，其不只是整個跨頁在創造時的viewport。重點在於這樣在一般與置中頁面的比例能夠一致。

當重排的書脊項目跟在預先分頁的後面時，當在缺少一個*rendition:page-spread-* *的特性值時，重排項目**應該**由下一頁開始（如*page-progression-direction*定義）。如果重排書脊項目有一個*rendition:page-spread-* *，則**必需**要被尊重（例如，插入一個空白頁面）。

同樣的，當預先分頁的書脊項目跟在重排的後面時，當在缺少一個*rendition:page-spread-* *的特性值時，預先分頁項目應該由下一頁開始（如*page-progression-direction*定義）。如果預先分頁書脊項目有一個*rendition:page-spread-* *，則**必需**要被尊重（例如，插入一個空白頁面）。

儘管作者經常指定在特定的裝置方向使用跨頁，內容自身不呈現為真正的跨頁（例如，兩個接續的頁面需要被一起接連排版才可被閱讀，例如兩頁的地圖）。要指示兩個連續頁面顯示為真正的跨頁，作者**應該**使用*rendition:page-spread-left*及*rendition:page-spread-right*特性於鄰接的書脊項目中，並且忽略書脊項目的特性令單頁或雙頁呈現都同等能被接受。當閱讀系統遇到兩個書脊項目顯示為真正跨頁時，其**應該**創造中間沒有調整空白頁的跨頁。

只有一個* page-spread-* *特性能在書脊項目中宣告。

> ##### 注意事項
> 
> *rendition:page-spread-left* 和 *rendition:page-spread-right properties*是對 *page-spread-left* 和 *spread-right* 特性的捷徑。其允許使用單一用語供所有固定版面特性。作者可以使用兩種特性組合，但是較舊的閱讀系統可能只認得無字首的版本。EPUB書脊特性與會不再延伸供包裝顯示詮釋資料使用，所以無字首的*page-spread-center*不存在。

###### 4.3.4.5.2 範本

> ###### 範例35
> 
> 以下範例展示重排內容放在一個兩頁固定版面置中的盤中，意圖在任何裝置使用同步跨頁排版。注意作者指定跨頁置左而保留其他部分（重排）不定義。所以*rendition:spread*預設全域值初始為*auto*。
> 
> <spine page-progression-direction="ltr">
>     …
>     <itemref idref="center-plate-left"
>              properties="rendition:spread-both rendition:page-spread-left"/>
>     <itemref idref="center-plate-right"
>              properties="rendition:spread-both rendition:page-spread-right"/>
>     …
> </spine>

> ###### 範例36
> 
> 以下範例展示固定版面內容，當使用同步跨頁時，必須為置中盤而停止。請注意*rendition:spread*不需位置中盤項目宣告，*rendition:page-spread-center*特性語意上已經制定了同步跨頁需要終止。
> 
> <metadata>
>     <meta property="rendition:layout">pre-paginated</meta>
>     <meta property="rendition:spread">auto</meta>
> </metadata>
> <spine>
>     <itemref idref="center-plate" properties="rendition:page-spread-center"/>
> </spine>

##### 4.3.4.6 rendition:viewport特性 (不再推薦)

*rendition:viewport*特性允許作者提供*rendition:layout*設定為*pre-paginated*的XHTML及SVG內容文件之CSS初始容器區塊（initial containing block, ICB）[CSS21]。

不再推薦使用本特性，請參考其在[Publications301]的定義以獲得更多資訊。

## 5. EPUB導覽文件

### 5.1 導論

本章節為非規範性。

EPUB導覽文件是EPUB包裝的必要元件。其允許作者包含一份可供人以及機器讀取的全域導覽文件，以確保能為使用者增加可用性與無障礙輔助性。

EPUB導覽文件是一個XHTML內容文件，但卻有著對其結構額外的限制，以便於機器處理其內容。[HTML]*nav*元素包含特化的導覽用資訊，同時保持人能閱讀，以准許閱讀系統能處理導覽用介面。

但是EPUB導覽文件並非專屬於機器處理，因為他是一個XHTML內容文件，所以可以作為線性閱讀順序的一部分，為了避免重複出現不同的目次，專門用於機器處理的內容，例如頁面清單，可以使用hidden屬性來從視覺排版中隱藏。

請注意閱讀系統在從EPUB導覽文件的資訊中處理導覽介面時，可能會除去腳本、樣式與HTML格式。如果格式與功能為必要，那麼EPUB導覽文件也得要包含在書脊之中。對導覽文件使用漸進增強[ContentDocs32]技巧於腳本和樣式將可保持內容的醫治性，尤其在非瀏覽化脈絡之下。

### 5.2 內容適用性

一個符合規定的EPUB導覽文件**必需**符合以下領域的需求：

**文件特性**

- 其必需符合定義在XHTML內容文件——內容規定中對內容的限制規定。
- 其必需符合定義在EPUB導覽文件定義中特別對EPUB導覽文件的內容限制規定。
- 作為符合規定的XHTML內容文件，其**可以**包含在書脊之中。

### 5.3 閱讀系統適用性

一個符合規定的EPUB閱讀系統**必需**在處理EPUB導覽文件時，複合以下領域的需求：

- 當使用者要求時，其**必需**提供對EPUB導覽文件中*nav*元素之連結以及連結標籤的存取，也就是能讓使用者能啟動連結。
- 當一個連結啟動時，其**必需**由應用程式現在閱讀位置，跳到該連結所指示的標的位置。
- 無論EPUB導覽文件是否為書脊的一部分，其**必需**尊重以上需求。

### 5.4 EPUB導覽文件定義

#### 5.4.1 nav元素：限制

當一個在EPUB導覽文件中的*nav*元素包含*epub:type*屬性[ContentDocs32]，本規格限制了該元素的內容模型以及其子元素如下：

> ###### 內容模型
> 
> ***nav***
>    依此順序
>      *HTML標題內容[零或一]*
>      *ol[唯一]*
> 
> ***ol***
>    依此順序
>      *li[一或多]*
> 
> ***li***
>    依此順序
>       (*span*或*a*)*[唯一]*
>       *ol[視狀況需求]*
> 
> ***span* and *a***
>    依任何順序
>        *HTML段落型內容[一或多]*
>
> 請注意對於允許用於這些元素的屬性沒有任何限制。
> 
> 請參考以下定義獲得額外的需求

*nav*元素的內容模型被解譯如下：

- nav的ol子元素代表內容導覽中的主要層級
- 每一個在依序清單中的清單項目代表一個標題，結構或者其他相關項目。一個子*a*元素描述連結指向的目標，當一個*span*元素應用在標題上時，用於分割清單到可區分的群組（舉例，一份多項的插畫列表可以被區隔成多個清單，每章各一）。
- 子元素*a*或*span***必需**在除去所有子元素以及經過應用程式空白正規化規則處理後，提供長度不為零的文字標籤。儘管非文字的子元素**可以**直接顯示給使用者，但文字內容**必需**包含在*title*或者*alt*屬性中以供判斷是否符合這樣需求。
- 如果一個*a*或*span*元素包含不提供明確文字替代的HTML嵌入內容，其元素**必需**包含一個title屬性以及替代文字供連結標籤顯示。
- 透過*a*元素中*href*屬性提供的IRI參照**必需**遵守以下需求：
    - 在*toc nav*、*landmarks nav*及*page-list nav*中，其**必需**攪吸到一個頂級層級內容文件或其片段。
    - 對其他類型的*nav*，其也**可以**參照遠端資源。
- 一個*a*元素**可以**由一個*ol*序列清單跟隨，代表輔助內容，層級低於標題（例如該章所有子章節的標題）。
- 一個*span*元素**必需**由一個*ol*序列清單跟隨；其不能用在「leaf」*li*元素。
- 無論是由*a*或者*span*元素開始，每一個子清單**必需**遵從定義於本章節的內容需求以供建構主要導覽清單。

EPUB規格**可以**提供對EPUB導覽文件中nav元素於以上內容模型的定義，做出進一步的限制。

> ###### 範例37
> 
> 以下範例顯示導覽元素的基本範式：
> 
> <nav epub:type="…">
>   <h1>…</h1>
>   <ol>
>     <li>
>       <a href="chap1.xhtml">A basic leaf node</a>
>     </li>
>     <li>
>       <a href="chap2.xhtml">A linked heading</a>
>       <ol>
>         …
>       </ol>
>     <li>
>       <span>An unlinked heading</span>
>       <ol>
>         …
>       </ol>
>     </li>
>   </ol>
> </nav>

在本規格脈絡下，*nav*元素中列表項目的顯示樣式**必需**等同於*list-style: none*特性[CSSSnapshot]。閱讀系統在書脊外呈現導覽文件時**不得**在列表中顯示列表項目編號，無論是否支援CSS。作者**可以**指定不同的CSS列表樣式供文件在書脊中顯示。

#### 5.4.2 nav元素：類型

##### 5.4.2.1 導論

本章節為非規範性。

定義在EPUB導覽文件中的nav元素透過其*epub:type*屬性[ContentDocs32]的值在語義上進行區別。

本規格定義了三種導覽目的：

***toc***
識別該*nav*元素包含了目次。*toc nav*僅供導覽用途使用，必須要被包含在EPUB導覽文件中。

***page-list***
識別該*nav*元素包含了頁面列表，供EPUB出版品對照印刷書或者其他固定分頁的來源。

***landmarks***
識別該*nav*元素包含了各用途的列表。

額外的導覽類型可以被包含在EPUB導覽文件中，請見其他*nav*元素以獲得更多資訊。

##### 5.4.2.2 toc nav元素

*toc nav*元素定義了該內容解釋主要的導覽階層。其概念上呼應了印刷書的目次（即是，其提供了該出版品主要結構章節的導覽）。

*toc nav*的參照**必需**排序反映以下兩點：

- 參照EPUB內容文件在書脊內的順序；
- 目標元素在其所位於EPUB內容文件中的順序。

*toc nav*元素**必需**EPUB導覽文件中出現僅一次。

##### 5.4.2.3 page-list nav元素

*page-list nav*元素提供內容內的位置，呼應到顯示於印刷來源的頁面邊界的位置，使其能顯示在EPUB出版品中。

*page-list nav*元素在EPUB導覽文件中為**選擇性**，**不得**出現一次以上。

*page-list nav*中的頁面參照**必需**符合兩項順序，包括指向EPUB內容文件在書脊中的順序，以及在其所參照EPUB內容文件中的每一頁順序。

*page-list nav*元素**應該**僅包含一個*ol*子元素（即為，沒有巢狀子列表）。

*page-list*參照的目標**可以**使用pagebreak詞彙[EPUB-SSV]在參照EPUB內容文件中作為辨識。

##### 5.4.2.4 landmarks nav元素

*landmarks nav*元素識別該內容解釋中的基礎架構元件，以使閱讀系統可以讓使用者更有效率的存取他們。

*epub:type*屬性[ContentDocs32]在*landmarks nav*的*a*子元素中為**必需**。*landmarks nav*元素中每個連結目標的結構語意，由該屬性的值決定。

> ###### 範例38
> 
> 以下範例呈現一個*landmarks nav*元素，其結構語意來自[EPUB-SSV]。
> 
> <nav epub:type="landmarks">
>     <h2>Guide</h2>
>     <ol>
>         <li><a epub:type="toc" href="#toc">Table of Contents</a></li>
>         <li><a epub:type="loi" href="content.html#loi">List of Illustrations</a></li>
>         <li><a epub:type="bodymatter" href="content.html#bodymatter">Start of Content</a></li>
>     </ol>
> </nav>

*landmarks nav***不得**包含多個具備相同*epub:type*值的項目指向相同的資源或者斷片。

*landmarks nav*在EPUB導覽文件中為**選擇性**，**不可**出現一次以上。

##### 5.4.2.5 其他*nav*元素

EPUB導覽文件**可以**在前章節所定義的*toc*、*page-list*及*landmarks nav*元素外，包含一或多個附加的*nav*元素。這些附加的*nav*元素應該擁有一個*epub:type*屬性來提供機器可讀取的語意，且其第一個子元素**必需**擁有一個人類可讀的標題。

本規格對於任何附加的*nav*元素不給予任何限制：他們**可以**被用於代表任何資訊領域的導覽語意，以及他們**可以**包含具備同質或異質的連結標的。

> ###### 範例39
> 
> 以下範例呈現一個客製化的表格導覽元素
> 
> <nav aria-labelledby="lot">
>     <h2 id="lot">List of tables</h2>
>     <ol>
>         <li><span>Tables in Chapter 1</span>
>             <ol>
>                 <li><a href="chap1.xhtml#table-1.1">Table 1.1</a>
>                 </li>
>                 <li><a href="chap1.xhtml#table-1.2">Table 1.2</a></li>
>             </ol>
>         </li>
>     	…
>     </ol>
> </nav>

#### 5.4.3 hidden屬性

在某些案例中，作者會想要在內容流中隱藏部分的導覽資料（即為閱讀系統在排版主要書脊內容時）。舉個一般案例，就是分頁清單，通常不會被排成內容流的一部分，取而代之會透過特別打造的導覽使用者介面分別呈現給使用者。

所以*display*特性[CSSSnapshot] 可用於控制EPUB導覽文件在閱讀系統顯示區域中的視覺呈現，但並非所有閱讀系統都提供這樣的介面。為了跨所有閱讀系統對排版做出控制，作者**必需**使用[HTML] *hidden*屬性來只是哪些（如果有）導覽資料的部分要被排除在內容流的排版中。*hidden*屬性不影響內容流之外導覽資料如何顯示（例如閱讀系統所提供的專門導覽使用者介面）。

> ###### 範例40
> 
> 以下範例呈現一部分*page-list nav*元素，在根元素使用*hidden*屬性只是整個清單都要被排除在內容流的排版之外。
> 
> <nav epub:type="page-list" hidden="">
>     <h2>Pagebreaks of the print version, third edition</h2>
>     <ol>
>         <li><a href="frontmatter.xhtml#pi">I</a></li>
>         <li><a href="frontmatter.xhtml#pii">II</a></li> … <li><a href="chap1.xhtml#p1">1</a></li>
>         <li><a href="chap1.xhtml#p2">2</a></li> … </ol>
> </nav>

> ###### 範例41
> 
> 以下範例呈現一部分*toc nav*元素，其中*hidden*屬性用於限制內容流排出兩個第一層的樹狀項目
> 
> <nav epub:type="toc" id="toc">
>   <h1>Table of contents</h1>
>   <ol>
>     <li>
>       <a href="chap1.xhtml">Chapter 1</a>
>       <ol>
>         <li>
>           <a href="chap1.xhtml#sec-1.1">Chapter 1.1</a>
>           <ol hidden="">
>             <li>
>               <a href="chap1.xhtml#sec-1.1.1">Section 1.1.1</a>
>             </li>
>             <li>
>               <a href="chap1.xhtml#sec-1.1.2">Section 1.1.2</a>
>             </li>
>           </ol>
>          </li>
>          <li>
>            <a href="chap1.xhtml#sec-1.2">Chapter 1.2</a>
>          </li>
>        </ol>
>      </li>
>     <li>
>       <a href="chap2.xhtml">Chapter 2</a>
>     </li>
>   </ol>
> </nav>

## A. 包裝文件模式

一個供內容文件使用的非規範模式（schema）可由此取得：https://github.com/w3c/epubcheck/tree/master/src/main/resources/com/adobe/epubcheck/schema/30/package-30.nvdl.

使用此模式進行驗證，需要支援[NVDL]、[RelaxNG-Schema]、[ISOSchematron] 及[XMLSCHEMA-2]的處理器。

> ##### 注意事項
> 
> NVDL模式曾可以被multi-pass驗證取代，而僅使用嵌入的RELAX NG以及ISO Schematron模式。

> ##### 注意事項
> 
> 這些模式需要在本規格正常改版外更新並且校正。結論上來說，他們會隨時都可能改版。

## B. application/oebps-package+xml媒體類型

本章節為非規範性。

本附錄為EPUB包裝文件註冊了媒體類型application/oebps-package+xml。本註冊優先於[RFC4839]。

包裝文件是一個XML檔案，用來說明一本EPUB出版品的內容解釋。其定義了內容解釋中的資源並且提供詮釋資料資訊。包裝文件與其相關的規格由W3C的EPUB 3社群小組所維護並且定義。

**MIME媒體類型名稱：**
    *application*

**MIME子類型名稱：**
    *oebps-package+xml*

**必要參數：:**
    無。

**選擇性參數：**
    無。

**編碼考量：**
    包裝文件為使用UTF-8或UTF-16編碼的XML。

**安全性考量：**
    包裝文件包含符合於XML 1.0規格的完整形式XML
    近一步說明，有可能製作出惡意檔案，例如，包含形式不完整的資料。大多數XML解析器可以透過嚴格檢查適用性來保護自身免於這樣的攻擊。
    所有閱讀包裝文件的處理器應該嚴格地檢查其檔案大小並且驗證取得的資料。
    在EPUB包裝3.2規格中現在沒有提供加密、簽署以及驗證包裝文件格式的規範。

**互通性考量：**
    無。

**已發表規格：**
    本媒體類型註冊供EPUB包裝文件使用，如EPUB包裝3.2規格中所敘述，位於http://w3c.github.io/publ-epub-revision/epub32/spec/epub-packages.html.
    EPUB包裝3.2規格優於Open Packaging Format 2.0.1規格，其位於http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm，其也使用application/oepbs-package+xml媒體類型。

**使用該媒體類型的應用程式：**
    該媒體類型廣於應用於EPUB格式電子書的遞送。以下應用程式列表並非窮舉：

- Adobe Digital Editions
- Aldiko
- Azardi
- Apple iBooks
- Barnes & Noble Nook
- Bluefire Reader
- Calibre
- Google Play Books
- Kobo
- Microsoft Edge
- Readium

**額外資訊**
    **魔術數字（Magic number）：**
        無。
    **副檔名：**
        .opf
    **麥金塔檔案類型代碼：**
        TEXT
    **斷片識別碼：**
        連結類型的註冊由http://www.idpf.org/epub/linking/所維護。這些類型定義的客製化斷片識別碼可解析到application/oebps-package+xml文件。
    
**進一步資訊的聯絡人與郵件位址：**
    public-epub3@w3.org

**預計用途：**
    COMMON

**作者/變更管控**
    發布的規格是World Wide Web Consortium之EPUB 3社群小組的成果產品。W3C對本規格有變更的管控權。

## C. Meta特性用語

### C.1 概論

#### C.1.1 關於本用語

本章節為非規範性。

本用語中的特性可用於*meta*元素的*property*屬性。

#### C.1.2 參考

沒有字首的特性可以使用基礎IRI做為參照http://idpf.org/epub/vocab/package/meta/#.

### C.2 詮釋資料meta特性

以下表格定義了供*meta*元素的*property*屬性使用的特性。

除非在其「延伸」區塊有特別指出，定義在此章節的特性用於定義子表意：換句話說，一個有定義在此區塊特性的meta元素**必需**包含一個refines屬性參照到一個資源，或者附加的表意。

在每一個特性定義中，准許的值區塊指出值預期的類型（使用[XMLSCHEMA-2]資料類型），基數區塊指出該特性可以附加到另一個特性的次數，以及延伸區塊指出何種特性可供復加。

#### C.2.1 alternate-script

名稱： | *alternate-script*
------- | -------
說明： | *alternate-script*特性提供了一個替代表述，以相關的特性值在一種語言或者書寫方式，其由*xml:lang*屬性辨識。此特性一般附加在*creator*及*title*特性供國際化使用。
允許的值： | *xsd:string*
基數： | *零或多個*
延伸： | 所有特性

> ###### 範例42
> 
> 以下範例展示作者名以英文，並且提供日文替代。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator">Haruki Murakami</dc:creator>
>     <meta refines="#creator" property="alternate-script" xml:lang="ja">村上 春樹</meta>
>     …
> </metadata>

#### C.2.2 authority

名稱： | *authority*
------- | -------
說明： | *authority*特性指示參照元素的值來自何系統或者模式
允許的值： | - 一個保留的authority值[AuthorityRegistry]（在意大小寫）或者 - 一個絕對IRI[RFC3987]指示其模式。該IRI**應該**參照到一個資源以提供關於該模式的更多資訊。
基數： | *零或多個*
延伸： | *subject*

> ###### 範例43
> 
> 以下範例展示一個BISAC主題標題
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:subject id="subject01">FICTION / Occult &amp; Supernatural</dc:subject>
>     <meta refines="#subject01" property="authority">BISAC</meta>
>     …
> </metadata>

#### C.2.3 belongs-to-collection

名稱： | *belongs-to-collection*
------- | -------
說明： | *belongs-to-collection*特性指出EPUB出版品所屬於集合的名稱。一本EPUB出版品**可以**歸屬於一或多個集合。也可以鍊結到其他使用refines屬性的特性來指出某個集合是否為其他集合的一部分。為准許閱讀系統組織集合並且避免命名衝突（例如，不相關的集合分享同一個類似的名稱，或者發布一個集合的不同版本）。其識別碼**應該**提用用來識別集合副本的獨特性。*dcterms:identifier*特性必需用於此識別碼。集合可以更精準地透過附加一個*collection-type*特性來定義其特質。EPUB出版品在集合中的位置**可以**透過提供附加的*group-position*特性來提供。
允許的值： | *xsd:string*
基數： | *零或多個*
延伸： | 套用到該EPUB出版品，並且可以說明其他副本或自身

> ###### 範例44
> 
> 以下範例展示該出本版品屬於Harry Porter套書的一部分
> 
> <metadata>
>     …
>     <meta property="belongs-to-collection" id="c02">Harry Potter</meta>
>     <meta refines="#c02" property="collection-type">set</meta>
>     …
> </metadata>

#### C.2.4 collection-type

名稱： | *collection-type*
------- | -------
說明： | *collection-type*特性指出一個集合的形式或特質。當*collection-type*值來自一組代碼表或者其他正式的目錄時，*scheme*屬性**應該**附加已用於指認其來源。當沒有指定模式時，閱讀系統**應該**辨識以下集合類型值：<br />
*series*<br />
一系列相關作品被正式識別為群組；一般開放其結尾以便於隨時新增單獨作品。<br />
*set*<br />
一組結束的作品整體建構成一個單一智慧財產標的；一般一齊發布並且可以被當作一個單位販賣。
允許的值： | *xsd*:string
基數： | *零或一*
延伸： | *belongs-to-collection*

> ###### 範例45
> 
> 以下範例展示一本出版品屬於The New French Cuisine Masters系列。
> 
> <metadata>
>     …
>     <meta property="belongs-to-collection" id="c01">
>         The New French Cuisine Masters
>     </meta>
>     <meta refines="#c01" property="collection-type">series</meta>
>     …
> </metadata>

#### C.2.5 display-seq

名稱： | *display-seq*
------- | -------
說明： | *display-seq*特性指出按號碼編列的位置用於展示現在的特性相對於識別的詮釋資料特性。此特性僅適用於處理尚未被定義的重要規則（例如定義作者在文件順序中出現的前後）。
允許的值： | *xsd:unsignedInt*
基數： | *零或一*
延伸： | 所有特性

#### C.2.6 file-as

名稱： | *file-as*
------- | -------
說明： | *file-as*特性提供標準化形式供復加的特性用於分類。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | 所有特性

> ###### 範例46
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator01">Lewis Carroll</dc:creator>
>     <meta refines="#creator01" property="file-as">Carroll, Lewis</meta>
>     …
> </metadata>

#### C.2.7 group-position

名稱： | *group-position*
------- | -------
說明： | *group-position*特性提供數字編號位置，讓EPUB出版品在與其他屬於相同群組的相關作品排序時使用（無論是否全都是EPUB出版品）。<br />*group-position*特性可被附加到任何詮釋資料特性用以建構群組，但一般僅與*belongs-to-collection*特性關聯。<br />一本EPUB出版品可以屬於多於一個的群組。
允許的值： | 單一*xsd:unsignedInt*或者一系列由小數點分隔的數字（例如1或2.2.1）
基數： | *零或一*
延伸： | 所有特性

> ###### 範例47
> 
> 以下範例展示一本出版品是Lord of the Rings套書中的第二冊。
> 
> <metadata>
>     …
>     <meta property="belongs-to-collection" id="c01">
>         The Lord of the Rings
>     </meta>
>     <meta refines="#c01" property="collection-type">set</meta>
>     <meta refines="#c01" property="group-position">2</meta>
>     …
> </metadata>

> ###### 範例48
> 
> 以下範例展示使用小數點分隔值的*group-position*，該書為期刊的98輯第4期。
> 
> <metadata>
>     …
>     <meta property="belongs-to-collection" id="cygnus-x-1">Physical Review D</meta>
>     <meta refines="#cygnus-x-1" property="collection-type">series</meta>
>     <meta refines="#cygnus-x-1" property="group-position">98.4</meta>
>     …
> </metadata>

#### C.2.8 identifier-type

名稱： | *identifier-type*
------- | -------
說明： | *identifier-type*提供一個識別碼形式或者特質。當*identifier-type*值來自一組代碼表或者其他正式的目錄時，*scheme*屬性**應該**附加已用於指認其來源。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | *identifier*, *source*

> ###### 範例49
> 
> 以下範例展示如何使用ONIX代碼表數字值5定義一個識別碼為ISBN。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:identifier id="isbn-id">urn:isbn:9780101010101</dc:identifier>
>     <meta refines="#isbn-id" property="identifier-type" scheme="onix:codelist5">15</meta>
>     …
> </metadata>

#### C.2.9 meta-auth (不再推薦)

名稱： | *meta-auth*
------- | -------
說明： | *meta-auth*特性提供該對包裝詮釋資料負責的組織或者權威。不再推薦使用*meta-auth*特性。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | 所有特性

#### C.2.10 role

名稱： | *role*
------- | -------
說明： | *role*特性解釋了該作品的創作者或者貢獻者（例如，該人物為作者或者作品的編輯）。當*role*值來自一組代碼表或者其他正式的目錄時，*scheme*屬性**應該**附加已用於指認其來源。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | *contributor*, *creator*

> ###### 範例50
> 
> 以下範例展示如何使用MARC關係者用語來區分作品中的作者與插畫。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:creator id="creator01">Lewis Carroll</dc:creator>
>     <meta refines="#creator01" property="role" scheme="marc:relators">aut</meta>  
>     <dc:creator id="creator02">John Tenniel</dc:creator>
>     <meta refines="#creator02" property="role" scheme="marc:relators">ill</meta>
>     …
> </metadata>

#### C.2.11 source-of

名稱： | *source-of*
------- | -------
說明： | *source-of*特性指出由該EPUB出版品之內容解釋取得資源，所適用來源的特別面向。本規格定義了*pagination*值，供*dc:source*參照定義在內容中*pagebreak*特性的來源。
允許的值： | *pagination*
基數： | *零或一*
延伸： | *dc:source*

> ##### 注意事項
> 請參照[EPUBAccessibilityTechniques]以取得如何提供無障礙頁面導覽的資訊

> ###### 範例51
> 
> 以下範例展示EPUB出版品的ISBN識別碼與其來源印刷書的ISBN識別碼被一併提供
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:identifier id="isbn-id">urn:isbn:9780101010101</dc:identifier>
>     <meta refines="#isbn-id" property="identifier-type" scheme="onix:codelist5">15</meta>  
>     <dc:source id="src-id">urn:isbn:9780375704024</dc:source>
>     <meta refines="#src-id" property="identifier-type" scheme="onix:codelist5">15</meta>
>     <meta refines="#src-id" property="source-of">pagination</meta>
>     …
> </metadata>

#### C.2.12 term

名稱： | *term*
------- | -------
說明： | *term*特性提供了一個主題代碼。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | *subject*

> ###### 範例52
> 
> 以下範例展示供主題標題使用的BISAC代碼。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:subject id="subject01">FICTION / Occult &amp; Supernatural</dc:subject>
>     <meta refines="#subject01" property="authority">BISAC</meta>
>     <meta refines="#subject01" property="term">FIC024000</meta>
>     …
> </metadata>

#### C.2.13 title-type

名稱： | *title-type*
------- | -------
說明： | *title-type*特性提供了標題的形式或者特質。當*title-type*值來自一組代碼表或者其他正式的目錄時，*scheme*屬性**應該**附加已用於指認其來源。當沒有指定模式時，閱讀系統**應該**辨識以下標題類型值：*main*、*subtitle*、*short*、*collection*、*edition*及*expanded*。
允許的值： | *xsd:string*
基數： | *零或一*
延伸： | *title*

> ###### 範例53
> 
> 以下範例展示如何識別不同的標題類型。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     …
>     <dc:title id="t1">A Dictionary of Modern English Usage</dc:title>
>     <meta refines="#t1" property="title-type">main</meta>  
>     <dc:title id="t2">First Edition</dc:title>
>     <meta refines="#t2" property="title-type">edition</meta>  
>     <dc:title id="t3">Fowler's</dc:title>
>     <meta refines="#t3" property="title-type">short</meta>
>     …
> </metadata>

> ###### 範例54
> 
> 以下範例展示如何將複雜的標題"The Great Cookbooks of the World: Mon premier guide de cuisson, un Mémoire. The New French Cuisine Masters, Volume Two. Special Anniversary Edition"分層處理。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
>     <dc:title id="t1" xml:lang="fr">Mon premier guide de cuisson, un Mémoire</dc:title>
>     <meta refines="#t1" property="title-type">main</meta>
>     <meta refines="#t1" property="display-seq">2</meta>  
>     <dc:title id="t2">The Great Cookbooks of the World</dc:title>
>     <meta refines="#t2" property="title-type">collection</meta>
>     <meta refines="#t2" property="display-seq">1</meta>  
>     <dc:title id="t3">The New French Cuisine Masters</dc:title>
>     <meta refines="#t3" property="title-type">collection</meta>
>     <meta refines="#t3" property="display-seq">3</meta>  
>     <dc:title id="t4">Special Anniversary Edition</dc:title>
>     <meta refines="#t4" property="title-type">edition</meta>
>     <meta refines="#t4" property="display-seq">4</meta>  
>     <dc:title id="t5">The Great Cookbooks of the World: 
>         Mon premier guide de cuisson, un Mémoire. 
>         The New French Cuisine Masters, Volume Two. 
>         Special Anniversary Edition</dc:title>
>     <meta refines="#t5" property="title-type">expanded</meta>
>     …
> </metadata>

#### C.2.14 範例

> ###### 範例55
> 
> 以下範例展示一份內容解釋可能包含的一般精細化詮釋資料。
> 
> <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">  
>     <dc:identifier id="pub-id">urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809</dc:identifier>
>     <meta refines="#pub-id" property="identifier-type" scheme="xsd:string">uuid</meta>  
>     <dc:identifier id="isbn-id">urn:isbn:9780101010101</dc:identifier>
>     <meta refines="#isbn-id" property="identifier-type" scheme="onix:codelist5">15</meta>  
>     <dc:source id="src-id">urn:isbn:9780375704024</dc:source>
>     <meta refines="#src-id" property="identifier-type" scheme="onix:codelist5">15</meta>  
>     <dc:title id="title">Norwegian Wood</dc:title>
>     <meta refines="#title" property="title-type">main</meta>  
>     <dc:language>en</dc:language>  
>     <dc:creator id="creator">Haruki Murakami</dc:creator>
>     <meta refines="#creator" property="role" scheme="marc:relators" id="role">aut</meta>
>     <meta refines="#creator" property="alternate-script" xml:lang="ja">村上 春樹</meta>
>     <meta refines="#creator" property="file-as">Murakami, Haruki</meta>  
>     <meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>  
> </metadata>

## D. 詮釋資料連結用語

### D.1 概論

#### D.1.1 關於本用語

本章節為非規範性。

本用語中的特性可用於詮釋資料*link*元素的*rel*及*property*屬性。

#### D.1.2 參考

沒有字首的連結特性可以使用基礎IRI做為參照http://idpf.org/epub/vocab/package/link/#.

### D.2 連結關係

以下值可供*line*元素的*rel*屬性使用，以建立在*href*屬性中參照資源的關係。

#### D.2.1 acquire

名稱： | acquire
------- | -------
說明： | 關鍵字*acquire*用於EPUB預覽與辨識哪裡可以取得完整版本的EPUB出版品。
基數： | *零或多*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： |	*<link rel="acquire" href="http://example.org/book/9781448103706" media-type="text/html"/>*

#### D.2.2 alternate

名稱： | *alternate*
------- | -------
說明： | 關鍵字*alternate*為HTML供連結使用*alternate*關鍵字的子集合。其不同之處包括： 
- 不能與其他關鍵字匹配 
- 如果一個替代連結包含在包裝文件詮釋資料中，其指出了包裝文件在*media-type*屬性指定的格式的替代表現。
- 如果一個替代連結包含在*collecttion*元素的詮釋資料中[Packages]，其指出了*collecttion*在*media-type*屬性指定的格式的替代表現。
- 閱讀系統不需要為替代連結生成超連結。
基數： | *零或多*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： |	*<link rel="alternate" href="package.json" media-type="application/json-ld"/>*

#### D.2.3 marc21xml-record (不再推薦)

名稱： | *marc21xml-record*
------- | -------
說明： | 不再推薦使用關鍵字*marc21xml-record*。其由關鍵字*record*取代，在*media-type*屬性[Packages]中的值為"*application/marcxml+xml*"。
基數： | *零或一*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： | *<link rel="marc21xml-record" href="pub/meta/nor-wood-marc21.xml"/>*


#### D.2.4 mods-record (不再推薦)

名稱： | *mods-record*
------- | -------
說明： | 不再推薦使用關鍵字*mods-record*。其由關鍵字*record*取代，在*media-type*屬性[Packages]中的值為"*application/mods+xml*"。
基數： | *零或一*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： | *<link rel="mods-record" href="pub/meta/nor-wood-mods.xml"/>*

#### D.2.5 onix-record (不再推薦)

名稱： | *onix-record*
------- | -------
說明： | 不再推薦使用關鍵字*onix-record*。其由關鍵字*record*取代，在特性屬性[Packages]中的值為*onix*。
基數： | *零或一*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： |	*<link rel="onix-record" href="pub/meta/nor-wood-onix.xml"/>*

#### D.2.6 record

名稱： | *record*
------- | -------
說明： | 指示所參照的資源為一個詮釋資料紀錄。
當指定此關鍵字時，紀錄的媒體類別可透過其*media-type*屬性[Packages]確認。
在EPUB連結詮釋資料守則中，有一個常見連結詮釋資料紀錄類別的清單。
如果紀錄類型無法從其媒體類型確認時，可以在*properties*屬性[Packages]中，指定一個識別碼屬性。
基數： | *零或多*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： | *<link rel="record" href="book/52.atom" media-type="application/atom+xml;type=entry;profile=opds-catalog"/>*

#### D.2.7 voicing

名稱： | *voicing*
------- | -------
說明： | 指示參照的聲音檔案提供了該資源或者表態的口語呈現（一般來說，作者或者書名），透過*refines*屬性表示。
基數： | *零或多*
延伸： | 所有特性。當使用此值時，**必需**要有*refines*屬性。
範例： | 	*<link refines="#title" rel="voicing" media-type="audio/mpeg" href="title.mp3" />*

#### D.2.8 xml-signature (不再推薦)

名稱： | *xml-signature*
------- | -------
說明： | 不再推薦使用關鍵字*xml-signature*。也並未被其他連結方法所取代。識別XML簽名的方法將在未來版本的EPUB中描述。
基數： | *零或多*
延伸： | 所有特性
範例： |	*<link refines="#meta-authority-01" rel="xml-signature" href="../META-INF/signatures.xml#MAI-Signature"/>*

#### D.2.9 xmp-record (不再推薦)

名稱： | *xmp-record*
------- | -------
說明： | 不再推薦使用關鍵字*xmp-record*。其由關鍵字*record*取代，在特性屬性[Packages]中的值為*xmp*。
基數： | *零或一*
延伸： | 僅適用於EPUB出版品或者集合。當有*refines*屬性時**不得**使用。
範例： | *<link rel="xmp-record" href="pub/meta/nor-wood-xmp.xml"/>*

### D.3 連結特性

以下值可用於*link*元素的*properties*屬性，以建立參照資源所表達的紀錄類型。這些供紀錄格式所提供的值，不能被獨特識別為該媒體類別。

#### D.3.1 onix

名稱： | *onix*
------- | -------
說明： | *onix*特性指出所參照的資源為一個ONIX紀錄[ONIX]。
範例： | *<link rel="record" href="pub/meta/nor-wood-onix.xml" media-type="application/xml" properties="onix"/>*

#### D.3.2 xmp

名稱： | *xmp*
------- | -------
說明： | *xmp*特性指出所參照的資源為一個XMP紀錄[XMP]。
範例： | *<link rel="record" href="pub/meta/nor-wood-xmp.xml" media-type="application/xml" properties="xmp"/>*

## E. 宣告特性用語

### E.1 概論

#### E.1.1 關於本用語

本章節為非規範性。

本用語中的特性可用於宣告中*item*元素的*property*屬性。

#### E.1.2 參考

沒有字首的特性可以使用基礎IRI做為參照http://idpf.org/epub/vocab/package/item/#.

### E.2 宣告item特性

以下表格定義了供宣告中*item*元素的*property*屬性使用的特性。

適用區塊指出出版品資源類型**可以**被指定這些特性，基數區塊指出在整個包裝文件範圍內，該特性**必需**出現的次數，以及用法區塊指出使用狀態。

#### E.2.1 cover-image

名稱： | 	*cover-image*
------- | -------
說明： | *cover-image*特性說明了該出版品資源為出版品的封面圖片。
適用： | 所有點陣以及向量圖片類型[EPUB32]
基數： | *零或一*
用法： | 選擇性。 

#### E.2.2 mathml

名稱： | *mathml*
------- | -------
說明： | *mathml*特性說明了該出版品資源包含一或多個MathML標記副本。
適用： | EPUB內容文件
基數： | *零或多*
用法： | 僅有在符合說明中指定的範疇時，**必需**指定。

#### E.2.3 nav

名稱： | *nav*
------- | -------
說明： | *nav*特性說明了該出版品資源建構了該內容解釋的EPUB導覽文件。
適用： | EPUB導覽文件
基數： | *僅一*
用法： | 必需。

#### E.2.4 remote-resources

名稱： | *remote-resources*
------- | -------
說明： | *remote-resources*特性說明了該出版品資源包含一或多個內部參照，指向外於EPUB容器的其他出版品資源。要了解更多資訊，請參考出版品資源位置[EPUB32]。
適用： | 所有能夠做內部參照的出版品資源（例如，XHTML內容文件、SVG內容文件、CSS樣式表以及媒體層疊文件）。
基數： | *零或多*
用法： | 僅有在符合說明中指定的範疇時，**必需**指定。

#### E.2.5 scripted

名稱： | *scripted*
------- | -------
說明： | *scripted*特性說明了該出版品資源為使用腳本的內容文件（例如，包含腳本內容及/或HTML表單元素）。
適用： | EPUB內容文件
基數： | *零或多*
用法： | 僅有在符合說明中指定的範疇時，**必需**指定。

#### E.2.6 svg

名稱： | *svg*
------- | -------
說明： | *svg*特性說明了該出版品資源嵌入了一或多個SVG標記副本。
當SVG標記直接包含在資源中時，該特性**必需**被設定，當SVG由其他資源參照（例如，使用[HTML]*img*、*object*或者*iframe*元素）時**可以**被設定。
適用： | XHTML內容文件；該值已隱含在SVG內容文件中。
基數： | *零或多*
用法： | 僅有在符合說明中指定的範疇時，**必需**指定。

#### E.2.7 Usage

當一個*item*所參照的資源符合該定義時，*mathml*、*remote-resources*及*scripted*特性**必需**要被指定。這些特性不適用內容包含資源的迴圈（例如，透過HTML *iframe*元素）。例如，如果一個沒有腳本的XHtML內容文件嵌入了一個腳本內容文件，只有被嵌入的文件之宣告*item properties*屬性要被給予*scripted*值。

#### E.2.8 Examples

> 範例1 以下範例展示一個*manifest item*元素為EPUB導覽文件。
> 
> <item properties="nav" id="c1" href="c1.xhtml" media-type="application/xhtml+xml" />

> 範例2 以下範例展示一個*manifest item*元素為封面圖片。
> 
> <item properties="cover-image" id="ci" href="cover.svg" media-type="image/svg+xml" />

> 範例3 以下範例展示一個*manifest item*元素為有腳本的內容文件並且包含嵌入MathML。
> 
> <item properties="scripted mathml" id="c2" href="c2.xhtml" media-type="application/xhtml+xml" />

## F. 書脊特性用語

### F.1 概論

#### F.1.1 關於本用語

本章節為非規範性。

本用語中的特性可用於書脊中*itemref*元素的*property*屬性。

#### F.1.2 參考

特性可以使用基礎IRI做為參照http://idpf.org/epub/vocab/package/itemref/#.

### F.2 書脊itemref特性

以下表格定義了供宣告中*itemref *元素的*property*屬性[Packages]使用的特性。

#### F.2.1 page-spread-left

名稱： | *page-spread-left*
------- | -------
說明： | *page-spread-left*特性表示關聯的*item*元素的內容文件，其第一頁於兩頁跨頁時要顯示在左手端。

#### F.2.2 page-spread-right

名稱： | *page-spread-right*
------- | -------
說明： | *page-spread-right*特性表示關聯的*item*元素的內容文件，其第一頁於兩頁跨頁時要顯示在右手端。

#### F.2.3 範本

> 範例4 以下範例展示一個兩頁跨頁的地圖該如何在書脊中進行指示。
> 
> <spine>
> 	<itemref idref="title"/>
> 	<itemref idref="ps-1-l" properties="page-spread-left"/>
> 	<itemref idref="ps-1-r" properties="page-spread-right"/>
> 	<itemref idref="toc"/>
> 	…
> </spine>

## G. 謝詞與貢獻者

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

## H. 參考資料

### H.1 規範性文件

#### [AuthorityRegistry]

　　[EPUB Subject Authorities Registry](https://www.idpf.org/epub/registries/authorities/). URL: https://www.idpf.org/epub/registries/authorities/

#### [BCP47]

　　[Tags for Identifying Languages](https://tools.ietf.org/html/bcp47). A. Phillips; M. Davis. IETF. September 2009. IETF Best Current Practice. URL: https://tools.ietf.org/html/bcp47

#### [ContentDocs32]

　　[EPUB Content Documents 3.2](https://www.w3.org/publishing/epub3/epub-contentdocs.html). URL: epub-contentdocs.html

#### [CSS21]

　　[Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification](https://www.w3.org/TR/CSS2/). Bert Bos; Tantek Çelik; Ian Hickson; Håkon Wium Lie et al. W3C. 7 June 2011. W3C Recommendation. URL: https://www.w3.org/TR/CSS2/

#### [CSSSnapshot]

　　[CSS Snapshot](https://www.w3.org/TR/CSS/). URL: https://www.w3.org/TR/CSS/

#### [DateTime]

　　[Date and Time Formats](https://www.w3.org/TR/NOTE-datetime). W3C. 27 August 1998. W3C Note. URL: https://www.w3.org/TR/NOTE-datetime

#### [DC11]

　　[Dublin Core Metadata Element Set, Version 1.1](http://dublincore.org/documents/dces/). DCMI. 14 June 2012. DCMI Recommendation. URL: http://dublincore.org/documents/dces/

#### [DCTERMS]

　　[DCMI Metadata Terms](http://dublincore.org/documents/dcmi-terms/). DCMI Usage Board. DCMI. 14 June 2012. DCMI Recommendation. URL: http://dublincore.org/documents/dcmi-terms/

#### [EPUB-SSV]

　　[EPUB Structural Semantics Vocabulary](http://www.idpf.org/epub/vocab/structure/). IDPF. URL: http://www.idpf.org/epub/vocab/structure/

#### [EPUB32]

　　[EPUB 3.2](https://www.w3.org/publishing/epub3/epub-spec.html). URL: epub-spec.html

#### [HTML]

　　[HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [ISO8601]

　　[Representation of dates and times. ISO 8601:2004](http://www.iso.org/iso/catalogue_detail?csnumber=40874).. International Organization for Standardization (ISO). 2004. ISO 8601:2004. URL: http://www.iso.org/iso/catalogue_detail?csnumber=40874

#### [ISOSchematron]

　　[ISO/IEC 19757-3: Rule-based validation — Schematron](http://standards.iso.org/ittf/PubliclyAvailableStandards/c040833_ISO_IEC_19757-3_2006(E).zip). 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c040833_ISO_IEC_19757-3_2006(E).zip

#### [JSON-LD]

　　[JSON-LD 1.0](https://www.w3.org/TR/json-ld/). Manu Sporny; Gregg Kellogg; Markus Lanthaler. W3C. 16 January 2014. W3C Recommendation. URL: https://www.w3.org/TR/json-ld/

#### [MediaOverlays32]

　　[EPUB Media Overlays 3.2](https://www.w3.org/publishing/epub3/epub-mediaoverlays.html). URL: epub-mediaoverlays.html

#### [NVDL]

　　[ISO/IEC 19757-4: NVDL (Namespace-based Validation Dispatching Language)](http://standards.iso.org/ittf/PubliclyAvailableStandards/c038615_ISO_IEC_19757-4_2006(E).zip). 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c038615_ISO_IEC_19757-4_2006(E).zip

#### [OCF32]

　　[Open Container Format (OCF) 3.2](https://www.w3.org/publishing/epub3/epub-ocf.html). URL: epub-ocf.html

#### [ONIX]

　　[ONIX for Books](http://www.editeur.org/). URL: http://www.editeur.org/

#### [OPF2]

　　[Open Packaging Format 2.0.1](http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm). URL: http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm

#### [Packages]

　　[EPUB Packages 3](http://www.idpf.org/epub3/latest/packages). URL: http://www.idpf.org/epub3/latest/packages

#### [Publications301]

　　[EPUB Publications 3.0.1](http://www.idpf.org/epub/301/spec/epub-publications.html). URL: http://www.idpf.org/epub/301/spec/epub-publications.html

#### [RDFA-CORE]

　　[RDFa Core 1.1 - Third Edition](https://www.w3.org/TR/rdfa-core/). Ben Adida; Mark Birbeck; Shane McCarron; Ivan Herman et al. W3C. 17 March 2015. W3C Recommendation. URL: https://www.w3.org/TR/rdfa-core/

#### [RelaxNG-Schema]

　　[Information technology -- Document Schema Definition Language (DSDL) -- Part 2: Regular-grammar-based validation -- RELAX NG](http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip). ISO/IEC. 2008. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip

#### [RFC2046]

　　[Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types](https://tools.ietf.org/html/rfc2046). N. Freed; N. Borenstein. IETF. November 1996. Draft Standard. URL: https://tools.ietf.org/html/rfc2046

#### [RFC2119]

　　[Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

#### [RFC3987]

　　[Internationalized Resource Identifiers (IRIs)](https://tools.ietf.org/html/rfc3987). M. Duerst; M. Suignard. IETF. January 2005. Proposed Standard. URL: https://tools.ietf.org/html/rfc3987

#### [RFC4839]

　　[Media Type Registrations for the Open eBook Publication Structure (OEBPS) Package File (OPF)](https://tools.ietf.org/html/rfc4839). G. Conboy; J. Rivlin; J. Ferraiolo. IETF. April 2007. Informational. URL: https://tools.ietf.org/html/rfc4839

#### [RoleRegistry]

　　[EPUB Collection Roles Registry](http://www.idpf.org/epub/registries/roles). URL: http://www.idpf.org/epub/registries/roles

#### [TypesRegistry]

　　[EPUB Publication Types Registry](http://www.idpf.org/epub/vocab/package/types). URL: http://www.idpf.org/epub/vocab/package/types

#### [Unicode]

　　[The Unicode Standard](https://www.unicode.org/versions/latest/). Unicode Consortium. URL: https://www.unicode.org/versions/latest/

#### [XML]

　　[Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/

#### [XML-NAMES]

　　[Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/

#### [XMLSCHEMA-2]

　　[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/xmlschema-2/). Paul V. Biron; Ashok Malhotra. W3C. 28 October 2004. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema-2/

#### [XMP]

　　[Extensible metadata platform (XMP) specification -- Part 1](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=57421). Adobe Systems Incorporated. ISO/IEC. 15 February 2012. URL: http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=57421

### H.2 參考性文件

#### [CSS3-MediaQueries]

　　[Media Queries](https://www.w3.org/TR/css3-mediaqueries/). Florian Rivoal et al. W3C. 19 June 2012. W3C Recommendation. URL: https://www.w3.org/TR/css3-mediaqueries/

#### [EPUB32Changes]

　　[EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html). URL: epub-changes.html

#### [EPUB3Overview]

　　[EPUB 3 Overview](https://www.w3.org/publishing/epub3/epub-overview.html). URL: epub-overview.html

#### [EPUBAccessibility]

　　[EPUB Accessibility](http://www.idpf.org/epub/latest/accessibility). URL: http://www.idpf.org/epub/latest/accessibility

#### [EPUBAccessibilityTechniques]

　　[EPUB Accessibility Techniques](http://www.idpf.org/epub/latest/accessibility/techniques). URL: http://www.idpf.org/epub/latest/accessibility/techniques

#### [RoleExtensions]

　　[EPUB Collection Element Role Extensions](http://www.idpf.org/epub/extensions/roles). URL: http://www.idpf.org/epub/extensions/roles

#### [UAAG20]

　　[User Agent Accessibility Guidelines (UAAG) 2.0](https://www.w3.org/TR/UAAG20/). James Allan; Greg Lowney; Kimberly Patch; Jeanne F Spellman. W3C. 15 December 2015. W3C Note. URL: https://www.w3.org/TR/UAAG20/
