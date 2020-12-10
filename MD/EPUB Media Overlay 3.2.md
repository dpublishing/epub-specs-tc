# EPUB媒體層疊3.2
最終社群小組規格 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-mediaoverlays.html
**編輯**：
    Marisa DeMeglio (DAISY Consortium)
    Daniel Weck (DAISY Consortium)
**協助參與：**
    GitHub w3c/publ-epub-revision
    提出問題
    版本紀錄
    修改要求

Copyright © 1999-2019 International Digital Publishing Forum™ and W3C® (MIT, ERCIM, Keio, Beihang)

<hr />

EPUB是國際數位出版論壇（IDPF, International Digital Publishing Forum）的註冊商標

## 概要

本規格定義了如何使用[SMIL3]（同步多媒體整合語言, Synchronized Multimedia Integration Language）、包裝文件、CSS樣式表與EPUB內容文件，令聲音表現能夠與EPUB內容文件同步。

媒體層疊可以讓文字與聲音同步，以增進無障礙輔助性供對傳統書籍文字使用上有困難的使用者。媒體層疊也提供因各種理由無法閱讀文字的讀者連續聆聽的體驗，且傳統嵌入聲音技術無法提供。甚至在某些方面提供了傳統思維無法提供的無障礙輔助性考量（例如，為了語言學習或能閱讀商售有聲書）。

本規格屬於組成[EPUB32]的規格群之一，其為基於XML與Web標準的數位出版品交換與遞送格式。要了解整體EPUB 3規格，需要與其他規格一併閱讀且理解。

可參考[EPUB32Changes]以了解本規格與其前版本的差異資訊。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
1.1 與其他規格的關係
1.1.1 與SMIL的關係
1.2 術語
1.3 適用性
1.4 命名空間字首對應
2. 媒體層疊文件定義
2.1 導論
2.2 內容適用性
2.3 閱讀系統適用性
2.4 媒體層疊文件定義
2.4.1 smil元素
2.4.2 head元素
2.4.3 metadata元素
2.4.4 body元素
2.4.5 seq元素
2.4.6 par元素
2.4.7 text元素
2.4.8 audio元素
3. 製作媒體層疊
3.1 導論
3.2 與EPUB內容文件的關係
3.2.1 結構
3.2.2 粒度（Granularity）
3.2.3 嵌入媒體
3.2.4 文字轉換語音
3.3 語意變化
3.4 連結樣式資訊
3.5 包裝
3.5.1 包含媒體層疊
3.5.2 包裝詮釋資料
4. 播放行為
4.1 載入媒體層疊
4.2 基本播放
4.2.1 時間與同步
4.2.2 處理聲音
4.2.3 處理EPUB內容文件元素
4.3 與EPUB內容文件互動
4.3.1 導覽
4.3.2 嵌入影音
4.3.3 文字轉換語音
4.4 可跳過性與可跳出性
4.4.1 可跳過性（Skippability）
4.4.2 可跳出性（Escapability）
5. EPUB導覽文件
A. 媒體層疊綱要
B. 時間值範本
C. 媒體層疊詮釋資料用語
C.1 概要
C.1.1 關於本用語
C.1.2 參考資料
C.2 媒體層疊特性
C.2.1 active-class
C.2.2 duration
C.2.3 narrator
C.2.4 playback-active-class
D. 謝詞與貢獻者
E. 參考資料
E.1 規範性文件
E.2 參考性文件

<br />

## 1. 導論

### 1.1 與其他規格的關係

本章節為非規範性。

#### 1.1.1 與SMIL的關係

本規格依賴於[SMIL3]之子集，其中EPUB媒體層疊元素與屬性定義於媒體層疊文件中的定義出自其延伸。

### 1.2 術語

專屬於EPUB 3的術語在本文件中以括號（譯注：英文版為首字大寫。範例如「作者」，「閱讀系統」）。術語與定義的完整清單提供於[EPUB32]。

每章節術語第一次出現時才會連結至其定義。

### 1.3 適用性

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、不得（MUST NOT）、推薦（RECOMMENDED）、應該（SHOULD）、不應（SHOULD NOT）**應該以[RFC2119]之記述解釋。

### 1.4 命名空間字首對應

為求方便，以下命名空間字首[XML-NAMES]用於本規格而無需另外宣告。若要使用其他字首在EPUB內容文件中，**必需**宣告。

prefix	 | URI
------- | -------
epub | 	http://www.idpf.org/2007/ops

## 2. 媒體層疊文件定義

### 2.1 導論

本章節為非規範性。

同步語音朗讀使用於主流電子書、教育工具以及供對印刷物有障礙者所用的電子書格式。在EPUB 3中，這些類型的書籍可以使用媒體層疊文件製作，以敘述供預先錄製的語音朗讀之時間點，以及如何與EPUB內容文件標注關聯。供媒體層疊使用的檔案格式定義如[SMIL3]的子集，其為W3C推薦標準，使用XML作為呈現同步多媒體資訊之用。

媒體層疊功能在設計上，對於不支援的EPUB閱讀系統顯示為透明。所以在EPUB出版品中包含媒體層疊不會影響到不支援媒體層疊閱讀系統對EPUB排版的能力，因為媒體層疊不會呈現。

本規格的未來版本可能會加入對影片媒體的支援（例如同步文字/手語書籍），但本版本僅支援與EPUB內容文件的聲音媒體同步。

### 2.2 內容適用性

媒體層疊文件**必需**符合以下領域需求：

**文件特性**

- 其**必需**符合定義於XML適用性[EPUB32]中對XML文件的適用性限制。
- 其**必需**合乎定義在附錄A媒體層疊綱要中的媒體層疊綱要，以及符合所有在媒體層疊文件定義中表述的適用性限制。
- 其**必需**在製作上反應所關聯的EPUB內容文件的結構，如在結構中所述。
- 其**可以**參照多於一個的EPUB內容文件，但是一份EPUB內容文件**不得**被多於一個的內容覆蓋文件所參照。
- 其**必需**緊貼嵌入媒體的需求。
- 其**應該**使用適當的語意標記，如在語意變化中說明。
- 其**必需**與EPUB出版品一起被包裝如包裝中所呈現。

**檔案特性**

- 媒體層疊檔案檔名**應該**使用副檔名*.smil*。

### 2.3 閱讀系統適用性

EPUB閱讀系統對於媒體層疊的支援為**選擇性**。閱讀系統若支援媒體層疊**必需**符合以下領域需求：

- 其**必需**處理媒體層疊文件符合所有閱讀系統適用性限制，如在媒體層疊文件定義中所表述。
- 其**必需**支援XHTML內容文件，也**可以**支援SVG內容文件。
- 其**必需**如在基本播放中所敘述之方式處理媒體層疊元素。
- 其**必需**在媒體層疊播放時允許使用者導覽，如在導覽中所討論。
- 其**必需**緊貼在EPUB內容文件中處理參照嵌入聲音與影片的規則，如在嵌入聲音與影片中所陳述。
- 支援文字轉換語音的閱讀系統**應該**合乎閱讀系統文字轉換語音適用性需求[EPUB32]。
- 其**應該**提供可跳過性與可跳出性功能，如在可跳過性與可跳出性中所敘述。

不支援媒體層疊的閱讀系統**必需**符合以下領域需求：

- 其**必需**忽略宣告*item*元素中的media-overlay屬性，以及宣告*item*元素，其*media-type*屬性值等同於*application/smil+xml.*。

### 2.4 媒體層疊文件定義

除另外指定的之外，本章所有定義的元素[XML]都屬於*https://www.w3.org/ns/SMIL*命名空間[XML-NAMES]。


#### 2.4.1 smil元素

*smil*元素為所有媒體層疊文件的根元素。

> ###### 元素名稱
> 
> 　　*smil*
> 
> ###### 用法
> 
> 　　*smil*元素為媒體層疊文件的根元素。
> 
> ###### 屬性
> 
> 　　*version[必需]*
> 　　  指定[SMIL3]規格的版本數字，表示媒體層疊所使用的版本。
> 　　  該屬性值必須為「3.0」。
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 　　  
> 　　*epub:prefix[選擇性]*
> 　　  宣告額外的詮釋資料用語字首。
> 　　  請參考語意變化以取得更多資訊。
> 
> ###### 內容模型
> 
> 　　依此順序
> 　　  head [0或1]
> 　　  body [唯一]

#### 2.4.2 head元素

*head*元素在媒體層疊文件中為詮釋資料容器。

> ###### 元素名稱
> 
> 　　*head*
> 
> ###### 用法
> 
> 　　*head*元素為*smil*文件**選擇性**的第一個子元素。
> 
> ###### 屬性
> 
> 　　無
> 
> ###### 內容模型
> 
> 　　  metadata [0或1]

由於本規格不定義任何必須出現於媒體層疊文件的詮釋資料特性，故*head*元素為**選擇性**。

#### 2.4.3 metadata元素

*metadata*元素表示媒體層疊文件的詮釋資料。*metadata*元素為一延伸點其允許包含使用任何詮釋資訊結構語言的詮釋資料。

> ###### 元素名稱
> 
> 　　*metadata*
> 
> ###### 用法
> 
> 　　作為*head*元素的子元素。
> 
> ###### 屬性
> 
> 　　無
> 
> ###### 內容模型
> 
> 　　[0或多個]來自任何命名空間的元素

本規格未定義任何**必需**出現在媒體層疊文件的詮釋資料特性；*metadata*元素供客製化詮釋資料需求使用。

#### 2.4.4 body元素

*body*元素為媒體層疊文件中包含表述的開始點。其包含了*par*與*seq*元素的主要序列。

> ###### 元素名稱
> 
> 　　*body*
> 
> ###### 用法
> 
> 　　*body*元素為*smil*元素**必需**的第二個子元素。
> 
> ###### 屬性
> 
> 　　*epub:type[選擇性]*
> 　　  結構語意表述用以對應在EPUB內容文件中呼應的元素。
> 　　  其值為由空白分隔的特性列表[Packages32]類別。請參考語意變化以獲得更多資訊。
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 　　  
> 　　*epub:textref[選擇性]*
> 　　  相對的IRI參照[RFC3987]以呼應EPUB內容文件，包含一個斷片識別碼用以參照特定的元素如[XPTRSH]。
> 
> ###### 內容模型
> 
> 　　以任何順序
> 　　  seq [0或多個]
> 　　  par [0或多個]
> 　　至少**必需**一個*par*或*seq*元素

#### 2.4.5 seq元素

*seq*元素包含需要被依序處理的媒體物件。

> ###### 元素名稱
> 
> 　　*seq*
> 
> ###### 用法
> 
> 　　一或多個*seq*元素**可以**作為*body*元素以及*seq*元素的子元素。
> 
> ###### 屬性
> 
> 　　*epub:type[選擇性]*
> 　　  結構語意表述用以對應在EPUB內容文件中呼應的元素。
> 　　  其值為由空白分隔的特性列表[Packages32]類別。請參考語意變化以獲得更多資訊。
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 　　  
> 　　*epub:textref[必需]*
> 　　  相對的IRI參照[RFC3987]以呼應EPUB內容文件，包含一個斷片識別碼用以參照特定的元素如[XPTRSH]。
> 　　  請參考語意變化以取得更多資訊。
> 
> ###### 內容模型
> 
> 　以任何順序
> 　　  seq [0或多個]
> 　　  par [0或多個]
> 　　至少**必需**一個*par*或*seq*元素

#### 2.4.6 par元素

*par*元素包含要被平行處理的媒體物件。

> ###### 元素名稱
> 
> 　　*par*
> 
> ###### 用法
> 
> 　　一或多個*oar*元素**可以**作為*body*元素以及*seq*元素的子元素。
> 
> ###### 屬性
> 
> 　　*epub:type[選擇性]*
> 　　  結構語意表述用以對應在EPUB內容文件中呼應的元素。
> 　　  其值為由空白分隔的特性列表[Packages32]類別。請參考語意變化以獲得更多資訊。
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 
> ###### 內容模型
> 
> 　　以任何順序
> 　　  text [唯一]
> 　　  audio [0或1]
> 　　*audio*元素為**選擇性**，僅當其對應的文字元素參照到聲音或者影片媒體（請見嵌入媒體）或者對應到文字內容供處理文字轉換語音（TTS）所用。

#### 2.4.7 text元素

*text*元素參照到EPUB內容文件中的元素。*text*元素一般參照到文字性質的元素，但也可以參照到其他EPUB內容文件的媒體元素（請見嵌入媒體）。

> ###### 元素名稱
> 
> 　　*text*
> 
> ###### 用法
> 
> 　　*par*‌元素的**必需**子元素。
> 
> ###### 屬性
> 
> 　　*src[必需]*
> 　　  相對的IRI參照[RFC3987]以呼應EPUB內容文件，包含一個斷片識別碼用以參照特定的元素如[XPTRSH]。
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 　　  
> ###### 內容模型
> 
> 　　空

#### 2.4.8 audio元素

*audio*元素表示聲音媒體的片段

> ###### 元素名稱
> 
> 　　*audio*
> 
> ###### 用法
> 
> 　　*par*元素的**必需**子元素，除非其對應的*text*元素參照到聲音或者影片媒體，或者對應到文字內容供處理文字轉換語音（TTS）所用，這些狀況則為**選擇性**（請見嵌入媒體）。
> 
> ###### 屬性
> 　　  
> 　　*id[選擇性]*
> 　　  元素的ID[XML]，在整份文件中**必需**為唯一。
> 　　  
> 　　*src[必需]*
> 　　  相對或絕對的IRI參照[RFC3987]至聲音檔案。該聲音檔案**必需**為列於核心媒體類型資源[EPUB32]表格中的聲音格式之一。
> 　　  
> 　　*clipBegin[選擇性]*
> 　　  一個時間值以指定物理媒體的時間點，呼應到該聲音片段的開始點。
> 　　  **必需**為[SMIL3]的時間值。
> 　　  請見附錄B，時間值範本。
> 　　  
> 　　*clipBegin[選擇性]*
> 　　  一個時間值以指定物理媒體的時間點，呼應到該聲音片段的結束點。
> 　　  **必需**為[SMIL3]的時間值。
> 　　  請見附錄B，時間值範本。
> 　　  時間邏輯上的時間點，其結束位置**必需**在指定於*clipBegin*屬性開始時間點之後。
> 
> ###### 內容模型
> 
> 　　空

## 3. 製作媒體層疊

### 3.1 導論

本章節為非規範性。

出版品中預先錄製好的配音可以一系列聲音片段呈現，個別對應到EPUB內容文件的部分。一個單獨的聲音片段，舉個例子，一般呈現單一句或者段落，但推測與其他片段或者文件中的文字沒有順序關係。媒體層疊解決了同步的問題，使用[SMIL3]標記以連結結構化聲音旁白到EPUB內容文件中對應的文字（或者其他媒體）。媒體層疊實際上為SMIL 3.0簡化了的子集以允許播放所定義的片段序列。

SMIL元素主要用於結構化媒體層疊的元素為*body*（用於主要序列）、*seq*（序列）以及*par*（平行）。（請參照媒體層疊文件定義以獲得更多這些與其他SMIL元素的資訊）

*par*元素為覆蓋的基本建構區塊，其呼應到EPUB內容文件的詞句。該元素提供了兩個關鍵資訊片段以供內容同步：１）聲音片段其包含對詞句的旁白；以及２）指出相關聯的EPUB內容文件斷片。*par*元素使用兩個媒體子元素以呈現該資訊：一個*audio*元素以及一個*text*元素。由於*par*元素平行處理其子元素，所以聲音片段以及EPUB內容文件斷片將會同時播放，結果為同步呈現。

*text*元素的*src*屬性透過其IRI參照對應相關連的詞語、句子，或者其他EPUB內容文件的斷片。*audio*元素的*src*屬性相同地參照對應聲音片段的位址，以及加入**選擇性**的*clipBegin*及*clipEnd*屬性以指出該片段中的特定時間點。

> ###### 範例 1
> 
> 以下範例呈現供詞句或句子的媒體層疊標記。
> 
> <par>                        
>     <text src="chapter1.xhtml#sentence1"/>
>     <audio src="chapter1_audio.mp3" clipBegin="23s" clipEnd="30s"/>
> </par>

*par*元素依序列配置在一起，以建構一系列的詞語或句子。並非所有EPUB內容文件中的元素都要在媒體層疊中呼應*par*元素，僅有與聲音旁白相關者需要。

> ###### 範例 2
> 
> 以下範例呈現基本的媒體層疊文件包含了一個詞句序列。其*body*元素作為整體文件的主要序列。
> 
> <smil xmlns="http://www.w3.org/ns/SMIL" 
>       version="3.0">
>     <body>
>         <par id="par1">
>             <text src="chapter1.xhtml#sentence1"/>
>             <audio src="chapter1_audio.mp3" clipBegin="0s" clipEnd="10s"/>
>         </par>
>         <par id="par2">
>             <text src="chapter1.xhtml#sentence2"/>
>             <audio src="chapter1_audio.mp3" clipBegin="10s" clipEnd="20s"/>
>         </par>
>         <par id="par3">
>             <text src="chapter1.xhtml#sentence3"/>
>             <audio src="chapter1_audio.mp3" clipBegin="20s" clipEnd="30s"/>
>         </par>
>     </body>
> </smil>

*par*元素也能加到*seq*元素中來定義更多複雜的結構，如部分或者章節（請見結構）。

### 3.2 與EPUB內容文件的關係

> ##### 注意事項
> 
> 於本章節中，EPUB內容文件假定為一份XHTML內容文件。儘管媒體層疊可被用於SVG內容文件，但播放行為可能不穩定，且無法保證其互通性。

#### 3.2.1 結構

媒體層疊文件的*body*包含兩個元素：*par*元素與*seq*元素。這些元素的順序**必需**符合EPUB內容文件的預設閱讀順序。

*par*元素代表詞句。每一個元素定義了一段文字與聲音元件，在播放時同步。

*seq*元素代表序列。其用於代表巢狀容器如章節、次要內容、標題、腳註等。其允許承繼這些容器結構並且在媒體層疊文件中被取得。

*seq*元素**必需**包含一個*epub:textref*屬性。該屬性的IRI[RFC3987]值**必需**參照EPUB內容文件中對應的結構元素。因為*seq*元素不提供同步程序，這項屬性允許閱讀系統能靜態匹配該元素到文字的位置上。

> 以下範例呈現一份具備巢狀*seq*元素的媒體層疊文件，代表一個有著小節標題與圖說的章節。
> 
> <smil xmlns="http://www.w3.org/ns/SMIL" xmlns:epub="http://www.idpf.org/2007/ops" version="3.0">
>     <body>
> 
>         <!-- a chapter -->
>         <seq id="id1" epub:textref="chapter1.xhtml#sectionstart" epub:type="chapter">
> 
>             <!-- the section title -->
>             <par id="id2">
>                 <text src="chapter1.xhtml#section1_title"/>
>                 <audio src="chapter1_audio.mp3"
>                        clipBegin="0:23:23.84"
>                        clipEnd="0:23:34.221"/>
>             </par>
> 
>             <!-- some sentences in the chapter -->
>             <par id="id3">
>                 <text src="chapter1.xhtml#text1"/>
>                 <audio src="chapter1_audio.mp3"
>                        clipBegin="0:23:34.221"
>                        clipEnd="0:23:59.003"/>
>             </par>
>             <par id="id4">
>                 <text src="chapter1.xhtml#text2"/>
>                 <audio src="chapter1_audio.mp3"
>                        clipBegin="0:23:59.003"
>                        clipEnd="0:24:15.000"/>
>             </par>
> 
>             <!-- a figure -->
>             <seq id="id7" epub:textref="chapter1.xhtml#figure">
>                 <par id="id8">
>                     <text src="chapter1.xhtml#photo"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:24:18.123"
>                            clipEnd="0:24:28.764"/>
>                 </par>
>                 <par id="id9">
>                     <text src="chapter1.xhtml#caption"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:24:28.764"
>                            clipEnd="0:24:50.010"/>
>                 </par>
>             </seq>
> 
>             <!-- more sentences in the chapter (outside the figure) -->
>             <par id="id12">
>                 <text src="chapter1.xhtml#text3"/>
>                 <audio src="chapter1_audio.mp3"
>                        clipBegin="0:25:45.515"
>                        clipEnd="0:26:30.203"/>
>             </par>
>             <par id="id13">
>                 <text src="chapter1.xhtml#text4"/>
>                 <audio src="chapter1_audio.mp3"
>                        clipBegin="0:26:30.203"
>                        clipEnd="0:27:15.000"/>
>             </par>
> 
>         </seq>
>     </body>
> </smil>

> ##### 注意事項
> 
> 群組化結構，如章節、圖說、表格與腳註於同一個*seq*元素的原因是如此一來他們開始與結束位置可以在播放時被識別。閱讀系統可以透過此針對該內容解釋的版面提供播放選項，例如跳過一段長圖說、關閉對換頁的處理（請見可跳過性與可跳出性），或者客製化閱讀模式也適應結構，如表格。

> ###### 範例 3
> 
> 以下範例顯示EPUB內容文件對應到前一份媒體層疊範本。
> 
> <html xmlns="http://www.w3.org/1999/xhtml" 
>       xmlns:epub="http://www.idpf.org/2007/ops" 
>       xml:lang="en" 
>      >
>     <head>
>         <title>Media Overlays Example of EPUB Content Document</title>
>     </head>
>     <body id="sec1">
>         <section id="sectionstart" epub:type="chapter">
>             <h1 id="section1_title">The Section Title</h1>
>             <p id="text1">The first phrase of the main text body.</p>
>             <p id="text2">The second phrase of the main text body.</p>
>             <figure id="figure">
>                 <img id="photo" 
>                      src="photo.png" 
>                      alt="a photograph for which there is a caption" />
>                 <figcaption id="caption">The photo caption</figcaption>
>             </figure>
>             <p id="text3">The third phrase of the main text body.</p>
>             <p id="text4">The fourth phrase of the main text body.</p>
>         </section>
>     </body>
> </html>

#### 3.2.2 粒度（Granularity）

本章節為非規範性。

媒體層疊*text*元素之*src*屬性透過其ID[XML]參照到EPUB內容文件元素上。故此，媒體層疊的粒度等級依附於EPUB內容文件如何被標記。如果最細的標記等級落在段落層級上，那麼就會是媒體層疊同步能夠發布的可能最細等級。同理，如果有著子段落標記，例如使用[HTML]*span*元素來代表詞句或句子，則可以在媒體層疊中提供更細的力度。越細的粒度月可以讓使用者得到更精準的同步播放結果，無論在依字或詞句導覽時，還是在搜尋文字時，但也會增加媒體層疊文件的檔案容量。

#### 3.2.3 嵌入媒體

任何與媒體層疊相關連的EPUB內容文件**可以**包含嵌入媒體像是影片、聲音或者圖片。該媒體層疊*text*元素可以用於透過其ID[XML]值來用於參照這些嵌入媒體。

當一個*text*元素參照嵌入媒體其包含聲音時，其匹配的*audio*元素可以為**選擇性**。

作者**應該**避免使用腳本來控制參照的嵌入EPUB內容文件媒體播放，這可能會與媒體層疊播放行為產生衝突。

#### 3.2.4 文字轉換語音

本規格允許在預錄的聲音斷片外，使用文字轉換語音（TTS）。當媒體層疊*text*元素沒有對應的聲音元素參照到目標EPUB內容文件元素時，該參照元素的內容**必需**適於透過TTS處理。例如，其可以為文字性質的EPUB內容文件元素，或者包含文字的回退。

### 3.3 語意變化

為了表達語意變化，*epub:type*屬性[ContentDocs32]可以添加到媒體層疊*par*、*seq*與*body*元素。

媒體層疊*epub:type*屬性的值限制尚須與EPUB內容文件中的*epub:type*屬性一致。請參考語意變化[ContentDocs32]以了解細節。

*epub:type*屬性可使閱讀系統行為適用於所指出的語意類型。這些行為的範例為可跳過性與可跳出性及註解。

> ###### 範例4
> 
> 以下範例呈現包含圖說的媒體層疊語意標記。
> 
> <smil xmlns="http://www.w3.org/ns/SMIL" 
>       xmlns:epub="http://www.idpf.org/2007/ops"
>       version="3.0">
>     <body>
>         <seq id="id1" epub:textref="chapter1.xhtml#figure" epub:type="figure">
>             <par id="id2">
>                 <text src="chapter1.xhtml#figuretitle"/>
>                 <audio src="chapter1_audio.mp3" clipBegin="0:24:15.000" clipEnd="0:24:18.123"/>
>             </par>
>             <par id="id3">
>                 <text src="chapter1.xhtml#figurecaption"/>
>                 <audio src="chapter1_audio.mp3" clipBegin="0:24:18.123" clipEnd="0:24:38.530"/>
>             </par>
>             <par id="id4">
>                 <text src="chapter1.xhtml#figuretext1"/>
>                 <audio src="chapter1_audio.mp3" clipBegin="0:24:38.530" clipEnd="0:25:00.515"/>
>             </par>
>         </seq>
>     </body>
> </smil>

本規格採用用語相關機制定義於用語關聯[ContentDocs32]且無變更。來自預設用語的術語**必需**在覆蓋文件中以無字首的方式使用。

媒體層疊**可以**使用額外的用語，透過*epub:prefix*屬性在根*smil*元素中進行定義。

### 3.4 連結樣式資訊

正在播放的EPUB內容文件元素之視覺表現資訊**可以**透過CSS樣式表中作者定義的class來表述。這些作者定義的class名稱**應該**在包裝文件的詮釋資料中使用詮釋資料特性*active-class*及*playback-active-class*來進行宣告。這些class名稱才可被閱讀系統發現。

*active-class*與*playback-active-class*特性**不得**與*refines*屬性[Packages32]一起使用，由於這些通常會被套用於整份內容解釋。

本範例展示作者如何連結樣式資訊與正在播放的EPUB內容文件。

> ##### 注意事項
> 
> 儘管本範本使用class名稱-epub-media-overlay-active與-epub-media-overlay-playing，但任何class名稱都可使用。選擇的class名稱可使用任何支援的CSS功能。

> ###### 範例5
> 
> 作者定義的CSS class名稱，使用詮釋資料特性*active-class*與*playback-active-class*在包裝文件中宣告。
> 
> <meta property="media:active-class">-epub-media-overlay-active</meta>
> <meta property="media:playback-active-class">-epub-media-overlay-playing</meta>
> 
> CSS樣式表包含作者定義的class名稱：
> 
> /* emphasize the active element */
> .-epub-media-overlay-active {
>     background-color: yellow;
>     color: black !important;
> }
> 
> /* fade out the inactive text */
> html.-epub-media-overlay-playing * {
>     color: gray;
> }
> 
> 相關的EPUB內容文件摘要：
> 
> <html>
>     …
>     <span id="txt1">This is the first phrase.</span>
>     <span id="txt2">This is the second phrase.</span>
>     <span id="txt3">This is the third phrase.</span>
>     …
> </html>

本範本中，閱讀系統可以套用作者定義的*-epub-media-overlay-active* class到每一個在EPUB內容文件中的文字元素，在播放時會變得有效。反過來說，當元素不再播放時，將會移除其class名稱。使用者將會看到每一個EPUB內容文件元素在播放時將會套用黃色背景的樣式。

閱讀系統也可以套用作者定義的*-epub-media-overlay-playing* class，當媒體層疊開始時，將會套用到該EPUB內容文件的文件元素。當播放結束時，class名稱將會被移除。以XHTML內容文件為例，class名稱將會套用到*html*元素。對SVG內容文件而言，將會套用到*svg*元素。使用者將會在媒體層疊播放時，看到所有未在作用的文字元素變成灰色。當播放停止，所有元素的顏色又會回到其預設值。

### 3.5 包裝

#### 3.5.1 包含媒體層疊

當EPUB內容文件整體或者部分被媒體層疊參照時，其宣告*item*元素[Packages32]**必需**包含一個*media-overlay*屬性。其屬性**必需**為對應的媒體層疊文件在宣告*item*中的ID[XML]。

*media-overlay*屬性不得被套用在宣告*item*元素中未被參照的EPUB內容文件上。

供媒體層疊文件使用的宣告項目**必需**媒體類型為*application/smil+xml*。

> ###### 範例6
> 
> 以下範例呈現包裝文件中EPUB內容文件與其相關連媒體層疊在宣告中的項目。
> 
> <manifest>
>    <item id="ch1" 
>          href="chapter1.xhtml" 
>          media-type="application/xhtml+xml" 
>          media-overlay="ch1_audio"/>
>    
>    <item id="ch1_audio" 
>          href="chapter1_audio.smil" 
>          media-type="application/smil+xml"/>
>    …
> </manifest>

#### 3.5.2 包裝詮釋資料

包裝文件**必需**在*meta*元素以*duration*特性中包含整個內容解釋的音檔長度。

此外每一個EPUB內容文件與相關媒體層疊的音檔長度也**必需**提供。refines屬性[Packages32]用於連結每一段長度宣告到呼應的宣告*item*[Packages32]。

作者也**可以**在包裝文件中包含旁白*narrator*的資訊，也可以將作者定義的CSS class名稱套用到正在播放的EPUB內容文件元素上。

> ###### 範例7
> 
> 以下範例呈現包裝文件中與媒體層疊的詮釋資料
> 
> <metadata>
>    …
>    <meta property="media:duration" refines="#ch1_audio">0:32:29</meta>
>    <meta property="media:duration" refines="#ch2_audio">0:34:02</meta>
>    <meta property="media:duration" refines="#ch3_audio">0:29:49</meta>
>    <meta property="media:duration">1:36:20</meta>
>    <meta property="media:narrator">Joe Speaker</meta>
>    <meta property="media:active-class">-epub-media-overlay-active</meta>
>    <meta property="media:playback-active-class">-epub-media-overlay-playing</meta>
>    …
> </metadata>

> ##### 注意事項
> 
> 字首*media*：在[Packages32]中保留，供於包裝的詮釋資料中包含這些特性所用。

## 4. 播放行為

### 4.1 載入媒體層疊

當EPUB閱讀系統載入包裝文件時，其**必需**參考宣告*item*元素中*media-overlay*屬性已發現EPUB內容文件中對應的媒體層疊。播放**必需**開始於媒體層疊元素所對應到所欲對應的EPUB內容文件的開始點。請注意EPUB內容文件的開始可以對應到一份媒體層疊的開始元素或者中間的元素。當媒體層疊文件結束播放時，閱讀系統**應該**載入下一個EPUB內容文件（如在包裝文件書脊中指定）同時載入其對應的媒體層疊文件，提供內容。

### 4.2 基本播放

#### 4.2.1 時間與同步

閱讀系統**必需**序列中*body*元素中緊接的子元素。*seq*元素的子元素**必需**被依序處理，當最後一個子元素結束播放時，播放完成。*par*元素的子元素**必需**被平行處理（每一個都需要同時開始），當所有子元素結束播放時，播放完成。當*body*元素的最後一個子元素結束播放時，媒體層疊文件的播放結束。

#### 4.2.2 處理聲音

當在呈現媒體層疊的*audio*元素時，閱讀系統**必需**播放*src*屬性中參照的聲音資源，片段的時間點透過所給予的*clipBegin*屬性開始，並透過所給予的*clipEnd*屬性結束。**必需**注意以下規則：

- 當*clipBegin*未被指定時，其值預想為「0」。
- 當*clipEnd*未被指定時，其值預想為物理媒體的完整長度。
- 當*clipEnd*超過物理媒體的完整長度時，其值預想為物理媒體的完整長度。

使用者可控制的聲音播放選項**應該**包含倍速調整，但在變更播放比例時不可以使音調失真，推薦的範圍為半速與倍速。

#### 4.2.3 處理EPUB內容文件元素

當呈現媒體層疊*text*元素時，閱讀系統**應該**確保透過*src*屬性參照於EPUB內容文件中的元素在可視範圍中可見。當媒體層疊播放時，閱讀系統有Viewport的話**應該**在EPUB內容文件中添加於詮釋資料特性中所給予的*active-class*及*playback-active-class*之class名稱到適當的元素上。反之，在播放狀態改變時class名稱**應該**被移除，如連結樣式資訊所解釋。

*active-class*及*playback-active-class*詮釋資料特性為**選擇性**，當沒有時，閱讀系統行為由實裝端指定。

### 4.3 與EPUB內容文件互動

#### 4.3.1 導覽

由於媒體層疊與EPUB內容文件緊密結合，所以閱讀系統可以很簡單地基於目前媒體層疊播放的位置來尋找到EPUB內容文件中的位置。當使用者中斷同步播放並且導覽轉移到EPUB出版品的其他部分時，同步播放**必需**從該點繼續。例如，當在EPUB內容文件中指定的頁數為預期的位置時，須從媒體層疊中相同位置的點開始播放。

相同的方法允許在使用者選擇EPUB導覽文件中導覽點時同步播放媒體層疊。閱讀系統載入供該檔案的媒體層疊並且尋找正確的點來開始播放，其基於導覽點目標的ID[XML]。

> ##### 注意事項
> 
> 媒體層疊文件可以直接與導覽文件相關，以提供對其內容的同步播放，且無論該XHTML內容文件是否包含於書脊中。請見EPUB導覽文件以了解更多資訊。

> ##### 注意事項
> 
> 媒體層疊文件元素可以與EPUB內容文件架構，例如表格，相關連。閱讀系統需要確保媒體層疊播放在使用者導覽表格之行及列時保持同步。閱讀系統也可以在處理表格內容前播放對應的表格標題。

#### 4.3.2 嵌入影音

EPUB內容文件與媒體層疊關聯的話，**可以**自身包含嵌入的影片與聲音媒體，其**可以**透過媒體層疊元素指向。不像文字與圖片，影片與聲音媒體具備自有的播放長度。結果上，當閱讀系統按照媒體層疊處理同步化時，相關EPUB內容文件中預設嵌入聲音與影片媒體的播放行為需要被取代。

請注意以下規則僅套用到相關連EPUB內容文件中參照的[HTML]*video*與*audio*元素。也就是說，規則僅套用到在媒體層疊中*text*元素所指向的元素（即為，透過*src*屬性）。沒有被媒體層疊元素所參照的嵌入媒體並非這些規則的標的。

- 所有在EPUB內容文件中受參照的嵌入聲音與影片媒體**必需**使其公開的播放介面不啟動（一般為：播放/暫停控制，時間軸，音量等）。此項行為為必要，以避免在媒體層疊定義中所排定的播放序列與透過使用者互動或者執行腳本的任意播放行為相互干擾。做為結果，當閱讀系統在播放模式時，其**應該**：

    - 隱藏頁面上所有獨立影音使用者介面控制列，其取代定義在[HTML]中*controls*屬性的預設行為。

    - 避免嵌入於EPUB內容文件的腳本啟動JavaScript影音播放API（即為，寫成部分預設行為）。也**推薦**內容製作者不要嵌入腳本供控制播放嵌入影音媒體。已經發佈的媒體層疊因此可以取得對同步呈現的完整控制，而無須面對任何受到腳本啟動客製化行為的風險。

- 所有EPUB內容文件中參照的嵌入影音媒體**必需**初始化到「停止」狀態，並且準備尤其內容流的零點位置播放（最好能顯示使用[HTML]*poster*屬性指定的圖片）。這項需求取代由[HTML]*autoplay*屬性所定義的預設行為。

- 當EPUB內容文件元素啟動時，需套用CSS樣式表的視覺強調規則，無論該元素之*src*屬性所參照的內容類型（例如，在詮釋資料特性*active-class*定義的CSS class名稱**應該**被套用在其刊載EPUB內容文件中可見的影音播放器控制項上）

- 除了媒體層疊啟動時對文字斷片以及圖片的預設行為外，影音播放**必需**按照指定的媒體層疊同步長度開始以及停止（根據標準[SMIL3]計時模型）。會有兩種可能的狀態：

    - 當在*par*母容器中，媒體層疊*text*元素沒有匹配的*audio*時，被參照的EPUB內容文件中影音媒體**必需**播放到其結束，於該點*text*元素的生命週期終結。在這案例中，*text*元素所默認的播放長度（以及靠該母*par*容器推斷）為其參照的影音片段。

    - 當在*par*母容器中，媒體層疊*text*元素有匹配的*audio*時，被參照的EPUB內容文件中影音媒體**必需**受到其匹配的audio播放長度所限制。在這案例中，母*par*容器實際的播放長度為其子聲音片段，而忽略*text*元素所指向的影音媒體自身的播放長度。這樣的行為結果會讓嵌入影音媒體播放提早結束（在到達其完整播放長度前），或者在結束平行媒體層疊聲音結束前結束（在這案例中，最後播放的影片影格**應該**在母*par*容器真正結束前保持可見）。這項行為等同於媒體層疊audio元素所隱含乘載的[SMIL3]*endsync*屬性行為。  更進一步，閱讀系統應該對每一個獨立聲音軌顯示音量等級的使用者控制條（例如，來自媒體層疊的*audio*元素，或者來自EPUB內容文件中嵌入的影音媒體），如此一來聲音輸出可以調整到符合聆聽者需求。請注意音檔的層疊一般為製作時的考量：內容製作者通常會為了說明用途在影片軌上添加一層聲音資訊。**推薦**在製作階段對於聲音層疊狀態進行仔細檢查，而閱讀系統**並不需要**以特殊手段處理多重音量等級。

- 當*text*元素於媒體層疊中結束啟動狀態，並且其指向到嵌入影音媒體，被參照的媒體**必需**被重置到初始的「停止」狀態，準備被從其內容流的零點位置準備被播放（最好能顯示使用[HTML]*poster*屬性指定的圖片）。

#### 4.3.3 文字轉換語音

當媒體層疊*text*元素沒有匹配的*audio*元素，參照目標EPUB內容文件的文字時，支援文字轉換語音（TTS）的閱讀系統**應該**使用TTS處理受參照的文字。

如同閱讀系統適用性需求，提供在目標EPUB內容文件的語音相關資訊**應該**被用於播放聲音流作為媒體層疊處理的一部分。請參照閱讀系統文字轉換語音適用性需求[EPUB32]。

媒體層疊*text*元素的生命週期呼應到相關語音合成的朗讀時間。該*text*元素所默認的長度（或者由從母*par*元素推測）透過文字轉換語音引擎處理而決定，所以在製作時無法提早知道（要素如語音速度、暫停以及其他音律參數都會影響到聲音輸出）。

### 4.4 可跳過性與可跳出性

#### 4.4.1 可跳過性（Skippability）

當在閱讀時，使用者也許會希望開啟或關閉某些內容的功能，例如腳註、頁碼或者其他類型的次要內容。這項功能稱為可跳過性。閱讀系統**應該**使用媒體層疊元素中*epub:type*屬性所提供的語意資訊來判斷何時提供使用者跳過功能的選項。

> ###### 範例8
> 
> 以下範例呈現有換頁的媒體層疊文件。閱讀系統可以提供使用者選項來開啟及關閉換頁/頁碼告知，這些聽起來顯得複雜。
> 
> <smil xmlns="http://www.w3.org/ns/SMIL" 
>       xmlns:epub="http://www.idpf.org/2007/ops"
>       version="3.0">
>     <body>
>         <!-- a paragraph -->
>         <par id="id1">
>             <text src="chapter1.xhtml#para1"/>
>             <audio src="chapter1_audio.mp3"
>                    clipBegin="0:23:22.000"
>                    clipEnd="0:24:15.000"/>
>         </par>
> 
>         <!-- a page number -->
>         <par id="id2" epub:type="pagebreak">
>             <text src="chapter1.xhtml#pgbreak1"/>
>             <audio src="chapter1_audio.mp3"
>                    clipBegin="0:24:15.000"
>                    clipEnd="0:24:18.123"/>
>         </par>
> 
>         <!-- another paragraph -->
>         <par id="id3">
>             <text src="chapter1.xhtml#para2"/>
>             <audio src="chapter1_audio.mp3"
>                    clipBegin="0:24:18.123"
>                    clipEnd="0:25:28.530"/>
>         </par>
>     </body>
> </smil>

> ###### 範例9
> 
> 以下範例呈現一份有換頁的EPUB內容文件。
> 
> <html … >
>     …
>     <body>
>         <p id="para1">This is the paragraph before the pagebreak … </p>
>         
>         <span id="pgbreak1" epub:type="pagebreak"/>
>         
>         <p id="para2">This is the paragraph after the pagebreak …</p>
>     </body>
> </html>

以下非窮舉清單呈現來自[EPUB-SSV]的術語，閱讀系統可以依此提供可跳過性選項：

- footnote（註解）
- endnote（腳註）
- pagebreak（換頁）

支援可跳過性的閱讀系統，**不應**推斷其基於*epub:type*的值。

#### 4.4.2 可跳出性（Escapability）

可跳出的項目為巢狀結構，例如表格以及列表，使用者也許希望能夠跳過，直接從巢狀結構的下一個點開始繼續閱讀。可跳出性功能不同於可跳過性，差別在於其非啟動或者關閉整個類型的項目，但提供了可離開的選項（即為，使用者可以在選擇跳出前聽到一部分內容）。

閱讀系統**應該**允許跳出巢狀結構。閱讀系統**必需**透過*epub:type*屬性的值來判斷巢狀內容的開始，以及**應該**提供使用者選項以跳過對該結構的播放並且無論接著的內容為何，都能繼續播放。

> ###### 範例10
> 
> 以下範例呈現供EPUB內容文件的媒體層疊文件包含了一個段落，一個表格以及另一個段落。支援可跳出性的閱讀系統將提供使用者選項來中斷對表格的播放，並且從下一個段落開始繼續播放。
> 
> <smil xmlns="http://www.w3.org/ns/SMIL" 
>       xmlns:epub="http://www.idpf.org/2007/ops"
>       version="3.0">
>     <body>
>         <!-- a paragraph, part of the regular document text -->
>         <par id="id1">
>             <text src="c01.xhtml#para1"/>
>             <audio src="chapter1_audio.mp3"
>                    clipBegin="0:23:22.000"
>                    clipEnd="0:24:15.000"/>
>         </par>
> 
>         <!-- a table with two nested rows -->
>         <seq id="id2" epub:textref="c01.xhtml#t1" epub:type="table">
>             <seq id="id3" epub:textref="c01.xhtml#tr1" epub:type="table-row">
>                 <par id="id4" epub:type="table-cell">
>                     <text src="c01.xhtml#td1"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:24:15.000"
>                            clipEnd="0:24:18.123"/>
>                 </par>
>                 <par id="id5" epub:type="table-cell">
>                     <text src="c01.xhtml#td2"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:24:18.123"
>                            clipEnd="0:25:28.530"/>
>                 </par>
>                 <par id="id6" epub:type="table-cell">
>                     <text src="c01.xhtml#td3"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:25:28.530"
>                            clipEnd="0:25:45.515"/>
>                 </par>
>             </seq>
>             <seq id="id7" epub:textref="c01.xhtml#tr2" epub:type="table-row">
>                 <par id="id8" epub:type="table-cell">
>                     <text src="c01.xhtml#td4"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:25:45.515"
>                            clipEnd="0:26:45.700"/>
>                 </par>
>                 <par id="id9" epub:type="table-cell">
>                     <text src="chapter1.xhtml#td5"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:26:45.700"
>                            clipEnd="0:28:02.033"/>
>                 </par>
>                 <par id="id10" epub:type="table-cell">
>                     <text src="chapter1.xhtml#td6"/>
>                     <audio src="chapter1_audio.mp3"
>                            clipBegin="0:28:02.033"
>                            clipEnd="0:28:52.207"/>
>                 </par>
>             </seq>
>         </seq>
> 
>         <!-- another paragraph -->
>         <par id="id11">
>             <text src="c01.xhtml#para2"/>
>             <audio src="chapter1_audio.mp3"
>                    clipBegin="0:28:52.207"
>                    clipEnd="0:30:01.000"/>
>         </par>
>     </body>
> </smil>

以下非窮舉清單呈現來自[EPUB-SSV]的術語，閱讀系統可以依此提供可跳出性選項：

- table（表格）
- table-row（表格行）
- table-cell（表格內容）
- list（列表）
- list-item（列表項目）
- figure（圖片組）

## 5. EPUB導覽文件

EPUB導覽文件為XHTML內容文件，所以可以與聲音媒體層疊相關聯。不像傳統的XHTML內容文件，然而，閱讀系統必須將EPUB導覽文件呈現給使用者，儘管不被包含在書脊中（請見EPUB導覽文件—閱讀系統適用性[Packages32]）。結果而言，連結到媒體層疊的方法可能會按照以下脈絡而受到變更：

- 當包含在書脊中，播放EPUB導覽文件的媒體層疊遵循與其他XHTML內容文件相同的適用性需求。
- 當在以顯示脈絡，其允許使用者存取並且啟動連結時，閱讀系統**可以**實作額外顯示行為，在導覽連結受到存取時提供聲音回饋。

> ##### 注意事項
> 
> 指定實作細節超乎本規格的目標。DAISY媒體層疊播放需求文件提供了供作者的最佳範例，也提供了給閱讀系統開發者的建議。

## A. 媒體層疊綱要

供媒體層疊使用的綱要可由*https://github.com/w3c/epubcheck/tree/master/src/main/resources/com/adobe/epubcheck/schema/30/media-overlay-30.nvdl*取得。

使用本綱要進行驗證需要支援[NVDL]、[RelaxNG-Schema]、[ISOSchematron]及[XMLSCHEMA-2]的處理器。

> ##### 注意事項
> 
> NVDL綱要層可以被使用嵌入RELAX NG及獨立ISO Schematron綱要的多通道驗證所替代。

## B. 時鐘值範本

本章節為非規範性。

以下為允許使用的時鐘值範例：

- *5:34:31.396* = 5小時，34分，31秒以及396毫秒
- *124:59:36* = 124小時，59分以及36秒
- *0:05:01.2* = 5分，1秒以及200毫秒
- *0:00:04* = 4秒
- *09:58* = 9分以及58秒
- *00:56.78* = 56秒以及780毫秒
- *76.2s* = 76.2秒 = 76秒以及200毫秒
- *7.75h* = 7.75小時 = 7小時以及45分
- *13min* = 13分
- *2345ms* = 2345毫秒
- *12.345* = 12秒以及345毫秒

## C. 媒體層疊詮釋資料用語

### C.1 概要

#### C.1.1 關於本用語

本章節為非規範性。

用語中的特性可用於*meta*元素中的*property*屬性[Packages32]。

#### C.1.2 參考資料

本用語中供參考的基本IRI為*http://www.idpf.org/epub/vocab/overlays/#*.

字首「*media:*」保留供[Packages]與本詞彙中的特性一起使用，並且無須在包裝文件中宣告。

### C.2 媒體層疊特性

#### C.2.1 active-class

名稱：| *active-class*
------- | -------
說明：| 作者定義的CSS class名稱，套用於目前正在播放的EPUB內容文件元素。
允許的值： | *xsd:string*
基數： | 	*零或一*
範例： | 	*<meta property="media:active-class">-epub-media-overlay-active</meta>*

#### C.2.2 duration

名稱：| *duration*
------- | -------
說明：| 全部或者指定的媒體層疊之播放長度。指定的播放長度由聲音片段在製作時計算，所以需排除從外部資源而來的直播以及語音合成。
允許的值： | **必需**為[SMIL3]時鐘值
基數： | 對整個內容解釋，或對每個媒體層疊都為唯一
範例： | *<meta property="media:duration">1:36:20</meta>*

#### C.2.3 narrator

名稱：| *narrator*
------- | -------
說明：| 配音員名字
允許的值： | *xsd:string*
基數： | *零或一*
範例： | *<meta property="media:narrator">Joe Speaker</meta>*

#### C.2.4 playback-active-class

名稱：| *playback-active-class*
------- | -------
說明：| 作者定義的CSS class名稱，套用於播放時啟動中的EPUB內容文件元素。
允許的值： | *xsd:string*
基數： | *零或一*
範例： | 	<*meta property="media:playback-active-class">-epub-media-overlay-playing</meta>*

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

#### [ContentDocs32]

　　[EPUB Content Documents 3.2](https://www.w3.org/publishing/epub3/epub-contentdocs.html). URL: epub-contentdocs.html

#### [EPUB-SSV]

　　[EPUB Structural Semantics Vocabulary](http://www.idpf.org/epub/vocab/structure/). IDPF. URL: http://www.idpf.org/epub/vocab/structure/

#### [EPUB32]

　　[EPUB 3.2](https://www.w3.org/publishing/epub3/epub-spec.html). URL: epub-spec.html

#### [HTML]

　　[HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [ISOSchematron]

　　[ISO/IEC 19757-3: Rule-based validation — Schematron](http://standards.iso.org/ittf/PubliclyAvailableStandards/c040833_ISO_IEC_19757-3_2006(E).zip). 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c040833_ISO_IEC_19757-3_2006(E).zip

#### [NVDL]

　　[ISO/IEC 19757-4: NVDL (Namespace-based Validation Dispatching Language)](http://standards.iso.org/ittf/PubliclyAvailableStandards/c038615_ISO_IEC_19757-4_2006(E).zip). 2006-06-01. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c038615_ISO_IEC_19757-4_2006(E).zip

#### [Packages]

　　[EPUB Packages 3](http://www.idpf.org/epub3/latest/packages). URL: http://www.idpf.org/epub3/latest/packages

#### [Packages32]

　　[EPUB Packages 3.2](https://www.w3.org/publishing/epub3/epub-packages.html). URL: epub-packages.html

#### [RelaxNG-Schema]

　　[Information technology -- Document Schema Definition Language (DSDL) -- Part 2: Regular-grammar-based validation -- RELAX NG](http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip). ISO/IEC. 2008. URL: http://standards.iso.org/ittf/PubliclyAvailableStandards/c052348_ISO_IEC_19757-2_2008(E).zip

#### [RFC2119]

　　[Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

#### [RFC3987]

　　[Internationalized Resource Identifiers (IRIs)](https://tools.ietf.org/html/rfc3987). M. Duerst; M. Suignard. IETF. January 2005. Proposed Standard. URL: https://tools.ietf.org/html/rfc3987

#### [SMIL3]

　　[Synchronized Multimedia Integration Language (SMIL 3.0)](https://www.w3.org/TR/SMIL3/). Dick Bulterman. W3C. 1 December 2008. W3C Recommendation. URL: https://www.w3.org/TR/SMIL3/

#### [XML]

　　[Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/

#### [XML-NAMES]

　　[Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/

#### [XMLSCHEMA-2]

　　[XML Schema Part 2: Datatypes Second Edition](https://www.w3.org/TR/xmlschema-2/). Paul V. Biron; Ashok Malhotra. W3C. 28 October 2004. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema-2/

#### [XPTRSH]

　　[XPointer Shorthand Notation](https://www.w3.org/TR/2003/REC-xptr-framework-20030325/). 25 March 2003. URL: https://www.w3.org/TR/2003/REC-xptr-framework-20030325/

### E.2 參考性文件

#### [EPUB32Changes]

　　[EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html). URL: epub-changes.html
