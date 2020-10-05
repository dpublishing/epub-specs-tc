# EPUB內容文件 3.2
社群小組規範完整版 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-contentdocs.html
**編輯**：
    Dave Cramer (Hachette Book Group)
    Matt Garrish (DAISY Consortium)
**前任編輯**：
    Elika J. Etemad (Invited Expert)
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

本規格定義使用於EPUB®出版品脈絡下的HTML、SVG以及CSS的規範。

本規格屬於組成[EPUB32]的規格群之一，其為基於XML與Web標準的數位出版品交換與遞送格式。要了解整體EPUB 3規格，需要與其他規格一併閱讀且理解。

可參考[EPUB32Changes]以了解本規格與其前版本的差異資訊。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
1.1 與其他規格的關係
1.1.1 與HTML的關係
1.1.2 與SVG的關係
1.1.3 與CSS的關係
1.2 術語
1.3 適用性
1.4 命名空間字首對應
2. XHTML內容文件
2.1 導論
2.2 內容適用性
2.3 閱讀系統適用性
2.4 HTML延伸
2.4.1 語意變化
2.4.1.1 導論
2.4.1.2 epub:type屬性
2.4.1.3 用語關聯
2.4.1.3.1 預設用語
2.4.1.3.2 保留字首
2.4.1.3.3 prefix屬性
2.4.1.4 處理需求
2.4.2 語意豐富化
2.4.2.1 導論
2.4.2.2 RDFa
2.4.2.3 Microdata
2.4.3 SSML屬性
2.4.3.1 導論
2.4.3.2 ssml:ph屬性
2.4.3.3 ssml:alphabet屬性
2.4.4 內容切換（不再推薦）
2.4.5 epub:trigger元素（不再推薦）
2.4.6 客製化屬性
2.5 HTML歧異與限制
2.5.1 嵌入MathML
2.5.1.1 導論
2.5.1.2 內容適用性
2.5.1.3 閱讀系統適用性
2.5.2 嵌入SVG
2.5.2.1 嵌入SVG與CSS
2.5.3 Unicode限制
2.5.4 不推薦的架構
2.5.4.1 rp元素
2.5.4.2 embed元素
2.5.5 外部資源限制
2.5.6 表單遞送
3. SVG內容文件
3.1 導論
3.2 內容適用性
3.3 對SVG的限制
3.4 閱讀系統適用性
3.5 語意變化
4. CSS樣式表
4.1 導論
4.2 內容適用性
4.3 閱讀系統適用性
4.4 有字首的特性
4.4.1 CSS Writing Modes
4.4.2 CSS Text Level 3
4.4.3 CSS Text Decoration Level 3
4.5 閱讀系統覆蓋
5. 腳本
5.1 腳本脈絡
5.2 內容適用性
5.3 閱讀系統適用性
5.4 安全性考量
5.5 事件模型考量
6. 固定版面
6.1 導論
6.2 內容適用性
6.3 閱讀系統適用性
6.4 Viewport排版
6.5 初始容器區塊空間
6.5.1 以HTML表達
6.5.2 以SVG表達
7. 發音辭典
7.1 導論
7.2 EPUB出版品適用性
7.2.1 範本
7.3 內容適用性
7.4 閱讀系統適用性
A. JavaScript epubReadingSystem物件
A.1 介面定義
A.2 說明
A.3 特性
A.4 手段
A.4.1 hasFeature
A.4.1.1 說明
A.4.1.2 功能
B. 謝詞與貢獻者
C. 參考資料
C.1 規範性文件
C.2 參考性文件

<br />

## 1. 導論

### 1.1 與其他規格的關係

本章節為非規範性。

#### 1.1.1 與HTML的關係

本規格並不參照特定版本的W3C[HTML]，而參照無標注日期的版本，如此一來將會一直指向最新的推薦版本。這項作法確保可以讓EPUB持續跟上HTML標準的變化腳步。作者與閱讀系統開發者會需要持續追蹤HTML的變革，以確保他們的流程與系統保持更新。

隨著HTML進化，可能有些功能在前一版有效，但後來變得過時或者被移除。W3C期望像這樣的變化能夠對作者造成最小限度的干擾，但考量到向後不相容的改版，於是重新考量使用無標注日期的參照版本。

本規格的XHTML規範定義繼承所有語意、結構與處理行為在[HTML]中的定義，除非另有指定。

此外，本規格定義了一系列對W3C HTML文件模式的延伸，讓作者可以包含在XHTML內容文件中。

本規格不要求EPUB閱讀程式支援腳本、HTML表單或者HTML DOM。本規格中的閱讀系統適用性僅預期能夠處理適用的EPUB內容文件。如同對腳本和HTML表單的支援為非強制，合適的閱讀系統可能不需要為具完整適用性的HTML使用者端。

#### 1.1.2 與SVG的關係

本規格並不參照特定版本的[SVG]，而參照無標注日期的版本。當在參照中有任何矛盾或疑義，最新的推薦版本為權威性參考資料。

這項作法確保EPUB能夠一直保持與SVG標準的同步發展。作者與閱讀系統開發者會需要持續追蹤SVG標準的變革，以確保他們的流程與系統保持更新。

隨著SVG進化，可能有些功能在前一版有效，但後來變得過時或者被移除。W3C期望像這樣的變化能夠對作者造成最小限度的干擾，但考量到向後不相容的改版，於是重新考量使用無標注日期的參照版本。

#### 1.1.3 與CSS的關係

EPUB 3支援的CSS定義比照CSS工作小組Snapshot [CSSSnapshot]。EPUB 3也維護一些有字首的CSS特性，以確保對全球語言的穩定支援。

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
ssml | 	https://www.w3.org/2001/10/synthesis

## 2. XHTML內容文件

### 2.1 導論

本章節定義了[HTML]的規範供創建XHTML內容文件使用。符合本規範的XML文件副本為核心媒體類型資源，並且在本規格中稱為XHTML內容文件。

除非另有指定，本規格繼承[HTML]規格所有語意、結構以及處理行為的定義。

### 2.2 內容適用性

一份XHTML內容文件**必需**符合以下所有領域的需求：

**文件特性**

- 其**必需**為一份[HTML]文件，並且合乎XHTML語法。

- 其**必需**合乎定義在XML適用性[EPUB32]中對XML文件的各種適用性限制。

- 所有文件使用的架構都定義於[HTML]，其**必需**合乎定義在該規格中關於這些架構的適用性要求，除非在HTML歧異與限制中被特別覆蓋。

- 其**可以**包含定義在HTML延伸中對[HTML]文法的延伸，且**必需**合乎所有定義於其中的內容適用限制。

> ##### 注意事項
> 
> 推薦EPUB出版品遵從[EPUBAccessibility]中適用於XHTML內容文件的無障礙輔助性需求。請參照無障礙輔助性[EPUB32]。

**檔案特性**

- XHTML內容文件檔案名稱**應該**使用副檔名*.xhtml*。

### 2.3 閱讀系統適用性

一個合規的EPUB閱讀系統**必需**符合所有以下處理XHTML內容文件的需求：

- 除非在本規格中額外定義為可覆蓋，其**必需**使用定義在[HTML]中的語意來處理XHTML內容文件，並且鼓勵適用所有定義於其中的使用者端適用性限制。

- 其**必需**符合所有定義在HTML延伸中的閱讀系統適用性要求。

- 其**必需**識別並且行為上採用定義於HTML歧異與限制中的限制。

- 其**必需**符合所有定義在腳本內容文件 — 閱讀系統適用性中的適用性需求。

- 其**必需**支援對XHTML內容文件的視覺化排版，如在CSS樣式表 — 閱讀系統適用性中的定義。

- 其**應該**識別嵌入的ARIA標記以及支援任何存在ARIA角色、狀態以及特性的呈現，如平台無障礙輔助性APIs[WAI-ARIA]。

### 2.4 HTML延伸

本章節定義在[HTML]文件模型下，EPUB 3 XHTML內容文件的延伸。

> ##### 注意事項
> 
> 儘管[HTML]允許使用者端支援中立的延伸，但除非這些延伸列於本章節，不然並非EPUB 3所支援的功能。

#### 2.4.1 語意變化

##### 2.4.1.1 導論

本章節為非規範性。

語意變化是在一份XHTML內容文件中，附加一個元素額外為了特殊目的及/或性質意義的過程。*epub:type*屬性在XHTML內容文件中用於表達特殊領域的語意，在[HTML]用語之外，這樣的變化包含了補充意義。

適用語意是為了加強包含他們元素的意義；他們的存在不會覆蓋其性質（例如，該屬性可以被用於指示*section*為該作品中的一章，但並非設計用來在適當的列表架構外，把*p*元素轉為列表項目）。

語意詮釋資料是在出版工作流程以及作者定義的目的下來強化內容的使用。其可讓閱讀系統了解更多關於文件中內容的結構，本規格對這些語意沒有特別定義其行為。處理行為可任閱讀系統決定。

本規格透過使用屬性軸來定義處理語意變化的方法：與其添加新元素，*epub:type*屬性可以對既存語意進行擴充，變化成想要的語意。也定義了一套機制來識別外部用語能夠提供對這些屬性的控制值。

##### 2.4.1.2 epub:type屬性

> **屬性名稱**
>     *type*
> 
> **命名空間**
>     *http://www.idpf.org/2007/ops*
> 
> **用法**
>     全域屬性。可以在所有元素中指定。
> 
> **值**
>     由空白分隔的特性列表[Packages32]值，其限制定義在語意關聯中。
>     空白的字元組定義於[XML]。

*epub:type*屬性出現在元素中會改變其語意。其值為一或多個由空白分隔的術語，來自於文件副本中關聯的外部用語基幹，如用語連結所定義。

變化的語意**必需**為乘載的元素表達一個次級語意。對於語意中立的元素而言，如同[HTML]*div*及*span*元素，變化的語意**不得**附加已經由既存元素所攜帶的意義（例如，一個*div*代表一段落或者區塊）。閱讀系統**必需**忽略與乘載元素相衝突的語意變化。

[HTML]*head*元素包含了該文件的詮釋資料，在此元素表達的結構化語意或者任何子元素沒有任何意義。閱讀系統**必需**忽略這樣的語意。

###### 範例

> ###### 範例1
> 
> 以下範例表示如何在[HTML]*section*元素中使用*epub:type*屬性標示為前（preamble）。
> 
> <html … xmlns:epub="http://www.idpf.org/2007/ops">
>     …
>     <section epub:type="preamble">
>         …    
>     </section>
>     …
> </html>

> ###### 範例2
> 
> 以下範例表示在[HTML]定義清單中使用*epub:type*屬性添加語彙集（glossary）語意。
> 
> <html … xmlns:epub="http://www.idpf.org/2007/ops">
>     …
>     <dl epub:type="glossary">
>         …    
>     </dl>        
>     …
> </html>

> ###### 範例3
> 
> 以下範例表示使用*epub:type*屬性來添加換頁（pagebreak）語意。
> 
> <html … xmlns:epub="http://www.idpf.org/2007/ops">
>    …
>   <p> … <span epub:type="pagebreak" id="p234"/> … </p>    
>    … 
> </html>

##### 2.4.1.3 用語關聯

本規格採用用語關聯機制，其定義於用語關聯機制[Packages32]，以及以下調整：

###### 2.4.1.3.1 預設用語

供內容文件使用的預設用語定義為[EPUB-SSV]。無字首的術語其不屬於[EPUB-SSV]**可以**被包含，但不建議使用。要添加客製化語意，建議使用字首作為偏好方式。

###### 2.4.1.3.2 保留字首

作者**可以**使用以下保留字首於*epub:type*屬性而無需宣告。

> ⚠️警告
> 
> 儘管保留字首是為了製作上的便利，依賴他們會導致互通性問題。例如，驗證工具經常會拒絕新的字首直到工具更新。強烈建議作者宣告所有使用的字首以避免這樣的問題。
> 

Prefix	 | IRI
------- | -------
msv | http://www.idpf.org/epub/vocab/structure/magazine/#
prism | http://www.prismstandard.org/specifications/3.0/PRISM_CV_Spec_3.0.htm#

###### 2.4.1.3.3 prefix屬性

*prefix*屬性定義沒有改變，但該屬性當使用於EPUB內容文件時，其命名空間為http://www.idpf.org/2007/ops 。

*prefix*屬性僅能用於[HTML]的根*html*元素。

##### 2.4.1.4 處理需求

一個閱讀系統**必需**以以下方式處理*epub:type*屬性：

- **可以**與定義於預設用語中的無、部分、全部術語的行為關聯。
- **可以**與其他用語中的術語的行為關聯。
- **必需**忽略無法識別的術語。

當閱讀系統遇到與*epub:type*之值產生關聯的行為和一個元素原生行為產生衝突時，該元素的關聯行為**必需**優先。

#### 2.4.2 語意豐富化

##### 2.4.2.1 導論

本章節為非規範性。

不像語意變化用於在標記中加強結構，語意豐富化為內容添加了意義層，而可以供機器處理使用。

[Microdata]及[RDFA-CORE]規格兩方定義了一系列屬性可以用於XHTML內容文件來豐富內容的語意。

##### 2.4.2.2 RDFa

[RDFA-CORE]屬性允許用於XHTML內容文件，但所有使用情形**必需**符合定義在[[!HTML+RDFA]]中的需求。

[RDFA-CORE]規格定義了當使用RDFa屬性時，[HTML]內容模型的變化。變化後的內容模型在XHTML內容文件中合乎規定。

EPUB閱讀系統對於屬性處理模型[RDFA-CORE]的支援為**選擇性**。

##### 2.4.2.3 Microdata

[Microdata]屬性允許用於XHTML內容文件，但所有使用情形**必需**符合定義在該規格中的需求。

[RDFA-CORE]規格定義了當使用RDFa屬性時，[HTML]內容模型的變化。變化後的內容模型在XHTML內容文件中合乎規定。

EPUB閱讀系統對於屬性處理模型[RDFA-CORE]的支援為**選擇性**，如轉換為JSON[Microdata]一般。

#### 2.4.3 SSML屬性

##### 2.4.3.1 導論

W3C語音合成標注語言[SSML]是一種用來協助文字轉語音（Text-to-Speech, TTS）引擎用來合成朗讀的語言。由於SSML設計上作為獨立的文件類型，其也定義了適用在其他標記語言中的語意。

本規格重編[SSML]*phoneme*元素為兩種屬性） — *ssml:ph*與*ssml:alphabet* — 並讓他們可以與XHTML內容文件共用。

具備文字轉語音相容性的閱讀系統**應該**支援SSML屬性其定義如下：

> ##### 注意事項
> 
> 要了解更多EPUB 3與合成朗讀相關的功能，請參考文字轉語音[EPUB3Overview]。

##### 2.4.3.2 ssml:ph屬性

*ssml:ph*屬性指定該文字一個音素的/語音學的發音，由附加其屬性的元素所表達。

> **屬性名稱**
> *ph*
> 
> **命名空間**
> *https://www.w3.org/2001/10/synthesis*
> 
> **用法**
> 全域屬性。**可以**指定於所有元素，期能在邏輯上關聯於一個發音（例如，包含文字資訊的元素）。
> 
> **不得**指定在一個已經有該項屬性元素的子元素。
> 
> **值**
> 一個音素的/語音學表述，語法上合規並且尊重使用的音素的/語音學字母表

本屬性繼承所有[SSML]*phoneme*元素*ph*屬性的語意，並且有以下附加：

- 當*ssml:ph*屬性一個包含文字節點子項目的元素，相對應的文件文字，其發音是用在字串上時，結果會依文件順序連結到子項目文字節點上。指定的語音學發音因此**必需**邏輯上對應到該元素完整的文字資料區域（例如，並非只是內容的獨立部分）。

閱讀系統同時支援SSML屬性以及PLS文件**必需**對這兩種結構定義優先規則。

##### 2.4.3.3 ssml:alphabet屬性

*ssml:alphabet*屬性指定該文字一個音素的/語音學的發音字母表，其為用於*ssml:ph*屬性的值。

> **屬性名稱**
> *alphabet*
> 
> **命名空間**
> *https://www.w3.org/2001/10/synthesis*
> 
> **用法**
> 全域屬性。**可以**指定於所有元素。
> 
> **值**
> 用於*ssml:ph*（繼承）值的發音字母表名稱。

本屬性繼承所有[SSML]*phoneme*元素*alphabet*屬性的語意，並且有以下附加：

- *ssml:alphabet*屬性的值繼承於文件樹。*ssml:ph*屬性值該使用哪一個發音字母表決定於第一個出現的*ssml:alphabet*屬性，該元素中出現ssml:ph屬性，跟隨著最接近的上層元素。

> ##### 注意事項
> 
> 儘管[SSML]規格中提供一份字母表的註冊參考，但卻還沒發表。由於W3C聲音瀏覽工作組的章程已經過期，不期待這樣的註冊會被發表。所以作者需要參考閱讀系統支援文件來判斷有哪些支援的字母表值。一些常見的字母表包括x-JEITA (以及 x-JEITA-IT-4002和x-JEITA-IT-4006)和x-sampa。

閱讀系統支援本規格之SSML屬性功能**應該**支援IPA字母表[IPA]，其表示為值"*ipa*"。

#### 2.4.4 內容切換（不再推薦）

*switch*元素提供了簡單機制讓作者能夠調整顯示給使用者的內容，該機制不依存於閱讀系統的腳本相容性。

不再推薦使用*switch*元素。請參考在[ContentDocs301]中的定義以獲得用法資訊。

#### 2.4.5 epub:trigger元素（不再推薦）

*trigger*元素能啟動所創建由標記定義的使用者介面供控制多媒體物件，例如聲音或者影片的播放，無論腳本或者非腳本脈絡。

不再推薦使用*trigger*元素。請參考在[ContentDocs301]中的定義以獲得用法資訊。

#### 2.4.6 客製化屬性

閱讀系統**可以**提供未定義在本規格中的功能來加強對EPUB出版品的排版。為了活用這項實驗功能，提供者**可以**定義客製化屬性供XHTML內容文件使用。

客製化屬性**可以**在一份XHTML內容文件的任何元素中，這些屬性來自一個外部的命名空間，其定義如命名空間[XML-NAMES]，且不能對應到以下的URIs：

- http://www.w3.org/1999/xhtml

- http://www.idpf.org/2007/ops

客製化屬性，以及與其相關聯的行為，**不得**改動一份EPUB出版品的一致性。內容**必需**能在沒有任何資訊缺失或者明顯變形的狀況下讓使用者能夠閱讀，無論閱讀系統是否會進行排版。

> ##### 注意事項
> 
> 為使客製化屬性能夠跨閱讀系統提供互通性，強烈建議提供者將實作的任何延伸記錄在[AttributeExtensions]中。

### 2.5 HTML歧異與限制

本章節定義了EPUB 3 XHTML內容文件與所適用[HTML]文件模式的歧異與限制。

#### 2.5.1 嵌入MathML

##### 2.5.1.1 導論

本章節為非規範性。

XHTML內容文件支援嵌入[MATHML3]，但限制其用途為完整MathML標記語言中受限制的子集。

設計該子集的目的是為了降低閱讀系統的門檻並且有助於無障礙輔助性，且能獲得對[HTML]使用者端的相容性。

> ##### 注意事項
> 
> 在宣告*item*元素中*mathml*特性指出該XHTML內容文件包含嵌入MathML。

##### 2.5.1.2 內容適用性

任何在XHTML內容文件中出現的MathML標記，**必需**符合MathML規格[MATHML3]中所表述的規則，以及以下額外限制：

**MathML顯示**
  math元素**必需**僅包含顯示用的MathML，*annotation-xml*為例外。

**MathML內容**
  內容MathML**可以**以MathML標記包含在XHTML內容文件中，當顯示時，語意元素中**必需**有一個*annotation-xml*子元素。

  當內容MathML在前述狀態中被包含時，其*annotation-xml*元素之編碼屬性**必需**被設置為功能上等同的值*MathML-Content*或者*application/mathml-content+xml*，及其命名屬性**必需**被設定為*contentequiv*。

**不再推薦的MathML**
  在[MATHML3]中元素與屬性若被標註為不再推薦，則**不得**被包含在XHTML內容文件的MathML標記中。

##### 2.5.1.3 閱讀系統適用性

適用的EPUB閱讀系統**必需**以下領域對在XHTML內容文件中支援MathML的需求：

- 其**必需**一個MathML顯示輸入相容的排版器，如[MATHML3]規格所定義。

- 其**可以**支援在*annotation-xml*元素中內容MathM的排版。

- 當有Viewport時，其**必需**支援MathML顯示的視覺排版。

> ##### 注意事項
> 
> EPUB閱讀系統可以選擇使用第三方資料庫，如MathJax來提供MathML排版支援。

#### 2.5.2 嵌入SVG

XHTML內容文件支援嵌入SVG文件斷片[SVG]，可透過參照（透過參照嵌入，例如，由一個*img*或者*object*元素）以及透過包含（在XHTML內容文件中直接透過包含一個svg元素嵌入）。

對在XHTML中嵌入SVG的內容適用性限制如同對SVG內容文件的中對SVG限制的定義。

閱讀系統**必需**如定義在SVG內容文件 — 閱讀系統適用性一般處理XHTML內容文件中的嵌入SVG。

> ##### 注意事項
> 
> 宣告*item*元素[Packages32]中的*svg*特性指出一份XHTML內容文件中包含嵌入SVG。

##### 2.5.2.1 嵌入SVG與CSS

若要為在XHTML內容文件中對以參照方式嵌入的SVG給予樣式，閱讀系統**不得**套用包含文件的CSS樣式規則到參照的SVG文件。

若要為在XHTML內容文件中對以包含方式嵌入的SVG給予樣式，閱讀系統**必需**套用包含文件的CSS規則到包含的SVG元素。

> ##### 注意事項
> 
> 透過參照加入SVG處理上視為分開的文件，且可各自包含自己的CSS樣式規則如一份SVG內容文件可以做到的程度。請注意當遇到如一個[HTML]*object*元素參照一個外部的[HTML]元素時，也須保持一致。

#### 2.5.3 Unicode限制

本章節列出對於Unicode字元組的限制。

**私用字元與嵌入字體**
  任何包含的字元其指向的碼點包含在定義於[Unicode]的私用區（Private Use Area, PUA）**必需**出現在一個有樣式或者屬性的字串，其目的為包含對一個嵌入字體[CSS-Fonts-3]的參照，該字體需包含該碼點的適當字形。

#### 2.5.4 不推薦的架構

本章節為非規範性。

##### 2.5.4.1 rp元素

[HTML]*rp*元素之目的是提供對於無法辨識ruby標註之舊版閱讀系統一個回退機制（即為，在*ruby*標註前後加入括號）。不過EPUB 3閱讀系統都重視ruby並且能提供回退機制，故不再推薦使用*rp*元素。

##### 2.5.4.2 embed元素

由於[HTML]*embed*元素未包含明確機制以提供給不支援腳本的閱讀系統回退，故不鼓勵作者使用本元素，尤其當參照的資源包含腳本時。可使用包含明確回退相容性的[HTML] *object*元素取代。

#### 2.5.5 外部資源限制

外部資源**可以**透過有明確回退機制的元素進行參照，明確回退機制能夠在不支援外部資源時，提供替代呈現。例如，多數[HTML]嵌入內容元素提供了替代排版的選項，例如在一項資源無法被排版時，可以指定多重來源或者允許嵌入HTML內容。核心媒體類型資源或者嵌入HTML內容在外部資源被參照時，其元素**必需**提供明確的回退機制。

[HTML]重排內容**可以**嵌入*audio*及*video*元素供排版，但對無法辨識這些元素的舊版閱讀系統而言（例如EPUB 2閱讀系統），不需要回退到核心媒體類型資源上。

由於各式各樣的來源都能被透過[HTML]*img*元素產生關聯，以下的回退狀態可供適用：

- 當為一個*picture*元素的子元素時：
    - 其**必需**在其*src*中，和若指定其*srcset*屬性時，參照核心媒體類型資源；以及
    - 每一個匹配的*source*元素**必需**在其*src*和*srcset*屬性中，參照一個核心媒體類型資源，除非在其**type**屬性中指定一個媒體類型，其非核心媒體類型。。
- 此外，**可以**參照外部資源，並在其*src*及*srcset*屬性中提供宣告回退[Packages32]定義。

以下[HTML]元素可以參照外部資源[EPUB32]，且無需提供對核心媒體類型資源的回退：

- *link* — 當其*rel*屬性有值"*pronunciation*"時
- *track*
- *video* — 包含在任何*source*子元素

外部資源**可以**在以上三元素中被參照，且無需提供對核心媒體類型資源的回退。

> ##### 注意事項
> 
> 請參照宣告回退[Packages32]以獲得對沒有明確機制元素，例如[HTML]*iframe*，
提供回退的資訊。

#### 2.5.6 表單遞送

閱讀系統對遞送[HTML]表單的支援為**選擇性**。一個閱讀系統可以，例如，透過限制對網路的存取來避免提交。

## 3. SVG內容文件

有些[SVG]的功能並未受到閱讀系統的完整支援，或者在閱讀系統運行的所有平台上支援不一致。當使用這些功能時，作者需要考量到潛在的風險以避免互通性及文件保存性遇到的潛在危機。

### 3.1 導論

本章節為非規範性。

可縮放向量圖形（Scalable Vector Graphics, SVG）[SVG]定義了一個格式，供顯示向量圖形與文字的最終形式。

儘管一本EPUB出版品一般使用XHTML內容文件作為最上層文件類型，但也允許使用SVG內容文件。SVG一般僅用於某些特殊環境，例如作為頁面圖像的最終形式，僅供特別類型的內容顯示（例如，漫畫書脈絡下的封面）。

本章節定義了[SVG]的規範。一個符合本規範的XML文件副本為核心媒體類別資源，以及在本規格中稱為SVG內容文件。

> ##### 注意事項
> 
> 本章節定義的適用性需求供SVG內容文件使用。若想要知道嵌入SVG的適用性需求，請見XHTML內容文件中的嵌入SVG。

### 3.2 內容適用性

一份SVG內容文件**必需**符合以下領域需求：

**文件特性**

- 其**必需**符合定義在XML適用性[EPUB32]中對XML文件的適用性限制。

- 其**可以**包含對外部資源的參照，但須提供對核心媒體類型資源的回退。

- 其**必需**為一個SVG文件斷片[SVG]，並且符合SVG限制中所有內容適用性限制。


> ##### 注意事項
> 
> 推薦EPUB出版品跟從[EPUBAccessibility]中的無障礙輔助性需求於SVG內容文件。請見無障礙輔助性[EPUB32]。

**檔案特性**

- SVG內容文件檔案名稱**應該**使用副檔名*.svg*。

### 3.3 對SVG的限制

本規格限制了SVG內容文件，以及在XHTML內容文件中嵌入SVG的內容模型如下：

- [SVG]*foreignObject***必需**符合以下規定：
    - 其**必需**包含[HTML]重排內容，或僅一個[HTML]*body*元素

> ##### 注意事項
> 
> 對於嵌入SVG而言，[HTML]定義中，限制SVG不允許有一個body元素。

   - 其內容**必需**為合規的文件斷片，符合定義在XHTML內容文件 - 內容適用性中的XHTML內容文件模型。
   - 其*requiredExtensions*在出現時，**必需**設定為"*http://www.idpf.org/2007/ops*"。
 
- [SVG]*title*元素**必需**僅包含合規的XHTML內容文件語法內容。

### 3.4 閱讀系統適用性

一個合規的EPUB閱讀系統在處理SVG內容文件及XHTML內容文件中的嵌入SVG時，**必需**符合以下領域需求：

- 除非在本規格中額外定義為可覆蓋，其**必需**使用定義在[SVG]規格中的語意來處理SVG內容文件，並且推薦符合所有在該規格中表述的適用性限制。

- 其**必需**符合在腳本化內容文件 - 閱讀系統適用性中定義的適用性規定。

- 當有Viewport時，其**必需**按照定義如樣式[SVG]，使用CSS來支援SVG的排版，以及其**應該**支援所有定義在特性索引[SVG]中的特性。對嵌入SVG而言，其**必需**符合定義在嵌入SVG與CSS中的限制。

- 其**應該**讓使用者能在SVG元素中進行選擇與搜尋。

- 當在XHTML內容文件斷片出現時，其**必需**辨識*requiredExtensions*屬性的值"*http://www.idpf.org/2007/ops*"（即為，當該屬性包含在*foreignObject*元素，或其*switch*子元素中）。

### 3.5 語意變化

定義在XHTML語意變化中的語法與語意在SVG內容文件中，繼承供*epub:type*及*epub:prefix*屬性使用。

*epub:prefix*屬性僅能用於SVG內容文件的根*svg*元素而合規。用於嵌入SVG的字首**必需**要在[HTML]根元素中宣告，如同XHTML語意變化中所定義。

## 4. CSS樣式表

### 4.1 導論

本章節為非規範性。

CSS為開放網頁平台不可欠的一部分。讀者、出版商以及文件作者預期CSS「能運作」，如同期望HTML能夠運作一般。

在過去，EPUB定義了一份CSS規格以只是對於一些特性的強制支援，並且提供了許多其他特性有字首的版本。儘管CSS工作組不再推薦使用這些有字首的特性，本規格依然需要維護一些有字首的特性以避免破壞既存的內容。但除了定義在本章節的少數例外外，EPUB依從W3C定義的CSS。

### 4.2 內容適用性

一份合規的CSS樣式表**必需**符合以下領域需求：

- 其**可以**包含任何CSS特性，除了以下例外：
    - 其**不得**使用*direction*特性[CSS-Writing-Modes-3]。改用[HTML] *dir*屬性來設定行文基本方向。
    - 其**不得**使用*unicode-bidi*特性[CSS-Writing-Modes-3]。改用[HTML] *bdo*元素以及*dir*屬性來控制行文的雙向性。
- 其**可以**包含定義在CSS樣式表 - 有字首的特性中的有字首特性。
- 其**必需**使用UTF-8或UTF-16編碼[Unicode]。

> ##### 注意事項
> 
> 請注意，一些閱讀系統可能不支援所有想要的CSS功能。特別是以下所列容易出問題：
>
> - 閱讀系統建構的分頁可能與樣式表造成不好的結果。分頁有時使用列來處理，會導致可見區域尺寸的值不正確。固定與絕對定位特別容易出錯。
> - 有些種類的螢幕在顯示動畫與轉場時表現不佳（即為，反應速度慢的）。

### 4.3 閱讀系統適用性

一個合規的EPUB閱讀系統在處理CSS樣式表時，**必需**符合以下領域需求：

- 其**必需**支援說明在[CSSSnapshot]中對CSS的官方定義。

- 其**應該**支援[CSSSnapshot]中所有可適用的模組，至少需支援為候選推薦（Candidate Recommendation）狀態[W3CProcess]（並且廣泛受到實作）。

- 其**必需**透過*@font-face*規則支援[TrueType]、[OpenType]、[WOFF]及[WOFF2]字型資源。

- 其**必需**支援所有定義在CSS樣式表 - 有字首的特性中的所有有字首特性。

- 除了支援以上定義的CSS特性外，其使用者端樣式表**應該**支援[HTML]推薦的預設排版。

- 其**應該**尊重定義在閱讀系統覆蓋中的作者CSS與使用者樣式。

建議閱讀系統開發者實作與主流瀏覽器相同等級的CSS支援。

### 4.4 有字首的特性

強烈推薦作者使用無字首的特性，以及閱讀系統支援最新的CSS規格。來自[ContentDocs301]，廣為使用的有字首的特性於本版恢復，但對其他特性的支援卻已經移除。作者建議在可以使用的狀況下，使用CSS原生解決方式替代移除的特性。

作者現在使用這些有字首的特性時，在有支援的狀況下建議使用無字首版本，這些特性預期在下一次EPUB的主要版本中不再支援。

#### 4.4.1 CSS Writing Modes

以下表格列出[CSS-Writing-Modes-3]具*-epub-的字首特性。值的欄指出該特性接受的值。過往EPUB映射的欄指出曾於之前版本EPUB 3使用的值/特性。星號(＊)表示舊的值或者特性已經不再推薦。最後一欄解釋如何基於[CSS-Writing-Modes-3-20151215]實作有字首的特性。

特性 | 值 | 過往EPUB映射 | 映射到[CSS-Writing-Modes-3-20151215]
------- | ------- | ------- | -------
-epub-text-orientation | upright | upright | upright
-epub-text-orientation | mixed | vertical-right* | mixed
-epub-text-orientation | sideways-right | sideways-right | sideways
-epub-text-orientation | sideways-right | rotate-right* | sideways
-epub-text-orientation | sideways | rotate-normal* | sideways
-epub-text-orientation | sideways | sideways | sideways
-epub-text-orientation | mixed | mixed | mixed
-epub-writing-mode | horizontal-tb | horizontal-tb | horizontal-tb
-epub-writing-mode | vertical-rl | vertical-rl | vertical-rl
-epub-writing-mode | vertical-lr | vertical-lr | vertical-lr
-epub-text-combine* | -epub-text-combine-horizontal: none | none | text-combine-upright: none
-epub-text-combine* | -epub-text-combine-horizontal: all | horizontal | text-combine-upright: all
-epub-text-combine* | Error | horizontal <number> | text-combine-upright: digits <number>

#### 4.4.2 CSS Text Level 3

特性 | 值 | 映射到[CSS-Text-3-20160119]
------- | ------- | -------
-epub-hyphens | none｜manual｜auto | No Change
-epub-hyphens | all | Not Supported
-epub-line-break	auto｜loose｜normal｜strict | No Change
-epub-text-align-last | auto｜start｜end｜left｜right｜center｜justify | No Change
-epub-word-break | normal｜keep-all｜break-all | No Change
text-transform | -epub-fullwidth | text-transform: full-width

#### 4.4.3 CSS Text Decoration Level 3

特性 | 值 | 映射到[CSS-Text-Decor-3]
------- | ------- | -------
-epub-text-emphasis-color | <color> | No Change
-epub-text-emphasis-position | [ over｜under ] && [ right｜left ] | No Change
-epub-text-emphasis-style | none | [ [ filled｜open ] || [ dot｜circle｜double-circle｜triangle｜sesame ] ] | <string> | No Change
-epub-text-underline-position | auto | [ under|| [ left｜right ] ] | No Change
-epub-text-underline-position | alphabetic | text-underline-position: auto

特性值語法定義在元件化值的組合[CSS-Values-3]。

### 4.5 閱讀系統覆蓋

EPUB閱讀系統**應該**適用作者寫在EPUB內容文件中的樣式表。如果閱讀系統允許，使用者**應該**能在想要的時候，能覆蓋作者提供的樣式表。EPUB閱讀系統**不應**在沒有嚴格需求下，覆蓋作者樣式表。

如果閱讀系統需要覆蓋作者樣式表，其**應該**透過一個使用者端樣式表來保存其層疊，利用*getOverrideStyle*方式[DOM-Level-2-Style]，或者[HTML]*style*屬性。

強烈建議閱讀系統開發者公開發表所使用的使用者端樣式表以及如何與作者樣式表互動。

## 5. 腳本

### 5.1 腳本脈絡

EPUB內容文件**可以**利用定義在本規格與相關規格([HTML]及[SVG])中的機制來包含腳本。當一份EPUB內容文件包含腳本時，在本規格中稱為腳本化文件。本標籤也套用到包含[HTML]*forms*副本的XHTML內容文件。

本規格定義了兩個脈絡，腳本**可以**出現：

This specification defines two contexts in which scripts MAY appear:

**書脊層級（spine-level）**
    在最上層內容文件中包含[HTML腳本]或者[SVG]腳本元素的副本。

**容器限制（container-constrained）**
    不能為以下兩者：
- 一個[HTML]腳本元素的副本包含在一份XHTML內容文件中，又嵌入於其上層XHTML內容文件，透過[HTML]*iframe*元素。
- 一個[SVG]腳本元素的副本包含在一份SVG內容文件中，又嵌入於其上層XHTML內容文件，透過[HTML]*iframe*元素。

在這兩個以上定義的脈絡，無論JavaScript代碼是直接嵌入在script元素，或者透過其*src*屬性進行參照，在執行脈絡下沒有區別。

腳本應用在哪一個脈絡中決定了其權利與限制，閱讀系統該如何處理。請參照內容適用性與閱讀系統適用性以了解一些特別的優先需求（並非所有的閱讀系統都提供相同的腳本功能性）。

#### 範例

> ###### 範例4
> 
> 請參考範例包裝文件：
> 
> <package …>
>     …
>     <manifest>
>         …
>         <item id="chap01" 
>             href="scripted01.xhtml" 
>             media-type="application/xhtml+xml"
>             properties="scripted"/>
>         <item id="inset01" 
>             href="scripted02.xhtml" 
>             media-type="application/xhtml+xml"
>             properties="scripted"/>
>         <item id="slideshowjs" 
>             href="slideshow.js" 
>             media-type="text/javascript"/>
>     </manifest>
>     
>     <spine …>
>         <itemref idref="chap01"/>
>         …
>     </spine>
>     …
> </package>
> 
> 以及參考檔案scripted01.xhtml:
> 
> <html …>
>     <head>
>         …
>         <script type="text/javascript">
>             alert("Reading System name: " + navigator.epubReadingSystem.name);
>         </script>
>     </head>
>     <body>
>         …
>         <iframe src="scripted02.xhtml" … />
>         …
>     </body>
> </html>
> 
> 以及參考檔案scripted01.xhtml:
> 
> <html …>
>     <head>
>         …
>         <script type="text/javascript" href="slideshow.js"></script>
>     </head>
>     <body>
>         …
>     </body>
> </html>
> 
> 由這些範例，以下為真：
> 
> - 在*scripted01.xhtml*的*head*中，*script*元素包含代碼，其為書脊層級腳本，因為該文件在書脊中受到參照；
> - 在*scripted02.xhtml*的*script*元素中包含代碼，其為容器限制腳本，因為其出現的HTML檔案透過*iframe*元素包含在*scripted01.xhtml*中。

### 5.2 內容適用性

**容器限制腳本（Container-constrained scripts）**

- 一個容器限制腳本**不得**包含修改該EPUB出版品之其他內容，或其母內容文件的DOM的程序，以及**不得**包含操弄其包含矩形尺寸的程序。

**書脊層級腳本（Spine-level scripts）**

- EPUB內容文件包含書籍層級腳本**必需**使用漸進強化技巧，其目的在本規格中遵從以下定義：當文件透過沒有腳本支援的閱讀系統排版，或者腳本支援關閉時，其最高層級內容文件必須保持一致，依然可以被使用者閱讀而沒有任何資訊丟失或者明顯的瑕疵。

**無障礙輔助性（Accessibility）**

- EPUB內容文件包含腳本**應該**使用相關的[WAI-ARIA]無障礙輔助性技巧以確保內容依然可以被所有使用者閱讀。

**回退（Fallbacks）**

- EPUB內容文件包含腳本**可以**為內容提供回退，無論是使用明確回退機制（例如可讓[HTML]*object*與*canvas*元素使用的）或者，當無法適用明確回退時，可使用宣告層級回退[Packages32]。

- 作者必須確保腳本僅用於產生核心媒體類型資源或者斷片之類[EPUB32]。

> ##### 注意事項
> 
> 宣告*item*元素中的*scripted*特性指出一份EPUB內容文件為腳本化內容文件

### 5.3 閱讀系統適用性

支援腳本的閱讀系統**必需**符合以下領域的需求：

- 其**應該**在重排EPUB內容文件中支援容器限制腳本。
- 其**應該**在固定版面文件中支援書脊層級腳本。
- 其**應該**在重排EPUB內容文件中支援書脊層級腳本，而該文件使用定義在[Packages32]中*rendition:flow*特性的"*scrolled-doc*"或"*scrolled-continuous*"顯示模式。相同地，如果其在重排EPUB內容文件中支援書脊層級腳本，其**必需**實作"*scrolled-doc*"顯示模式，並且**應該**實作"*scrolled-continuous*"顯示模式。
- 其**可以**在其他脈絡下支援腳本，但本規格對這樣的腳本不另外敘述。結果來說在其他脈絡下使用腳本可能在跨閱讀系統時不會保持一致。
- 其**可以**依據[HTML]腳本客戶端將腳本化內容文件排版成具互動性。
- 其**不得**允許容器限制腳本修改該EPUB出版品之其他內容，或其母內容文件的DOM，以及**不得**允許其操弄其包含的矩形尺寸（注意，儘管腳本並非為容器限制腳本，閱讀系統**可以**對操弄施予限制（可參照DOM操弄功能））。
- 其**可以**在執行腳本時，對其行為提供額外的限制（例如，限制網路存取）。
- 其**必需**實作JavaScript *navigator*延伸物件*epubReadingSystem*，如附錄A所定義的JavaScript epubReadingSystem Object。其也**必需**支援DOM操弄與版面變更功能，定義在容器限制腳本脈絡下的功能。

一個不支援腳本的閱讀系統**必需**符合以下領域的需求：

- 其**必需**處理腳本化內容的回退，如腳本化內容文件中回退所定義。

> ##### 注意事項
> 
> 閱讀系統可以在排版腳本化內容文件的同時，關閉其他EPUB功能及/或提供不同的排版與使用者體驗（例如，關閉分頁）
> 
> 作者對使用容器限制模型腳本的選擇可以進一步確保在腳本化與無腳本內容間使用者經驗一致（例如翻頁行為一致）。
> 
> 建議作者在能使用時使用宣告式技術，以增進其EPUB出版品的互通性、長期保存性與無障礙輔助性，並且避免使用包含式腳本。

### 5.4 安全性考量

本章節為非規範性。

所有的EPUB作者以及EPUB閱讀程式開發者得要注意到當閱讀系統執行腳本化內容時發生的安全性問題。由於目前閱讀系統與瀏覽器所使用的腳本模型一樣，在網頁脈絡下的相同問題也需要納入考量。

每一個閱讀系統都得要分辨是否在特殊文件中的腳本是否該被信任。推薦所有的腳本都被以不受信任對待（並且潛在為惡意），所有維度的攻擊都要被檢查並且受到保護，尤其以以下需求更需要受考量：

- 對runtime環境的攻擊（例如從使用者硬碟中偷取檔案）；
- 對閱讀系統自身的攻擊（例如竊取使用者書單或者造成非預期的行為）；
- 由一個內容文件攻擊另一個（例如竊取從不同文件產生的資料）；
- 透過非加密的腳本攻擊一份文件的加密部分（例如注入惡意腳本擷取保護的內容）；
- 對區域網路的攻擊（例如竊取在防火牆後伺服器的資料）；

提供以下建議作為處理不受信任腳本的指南：

- 閱讀系統行為上需要將每一份內容文件視為一個獨特的網域（domain），如瀏覽器為基礎的安全性大量基於文件URL與網域。採用這樣的做法可以將每一份文件和網際網路網域互相孤立，所以可以限制對外部URL、cookies、DOM儲存等的存取。 啟用腳本與網路存取的閱讀程式需要考量包括手段來警示使用者正在存取網路及/或允許他們關閉之。

> ##### 注意事項
> 
> 實務上，閱讀系統可以在文件間共享網域，但依然需要維持文件間的孤立。
> 
> 如果一份文件受到加密而其他沒有，或者不同的加密密鑰用於該文件的不同部分，一個獨特單一文件的網域也許不足以提供充分的保護。

- 如果閱讀系統允許保留持續性資料，該資料則需要被視為敏感資料。腳本可以透過cookies或DOM儲存來保存持續性資料，但是閱讀系統可以阻擋這樣的嘗試。允許儲存資料的閱讀系統需要確保資料不會受到其他不相關文件的存取（例如其他文件以欺騙的方式偽裝）。特別是，使用匹配文件識別碼（或者類似的詮釋資料）並非有效的手段來控制對持續性資料的存取。 允許本地儲存的閱讀系統也需要提供手段讓使用者來檢查、關閉或者刪除這些資料。當對應的EPUB出版品刪除時，這些資料也需要受到銷毀。

注意，適用以上推薦項目並不保證能夠抵抗所有列出的可能攻擊；開發者需要檢查閱讀系統脈絡下所有潛在的脆弱性。

### 5.5 事件模型考量

本章節為非規範性。

閱讀系統需要遵從DOM事件模型如[HTML] ，並在執行和與這些事件連結的預設事件時，忽略對腳本環境的UI事件。閱讀系統實作者需要確保腳本不能關閉重要功能（例如導覽）以延伸其影響讓潛在惡意腳本能衝擊該閱讀系統。結果上來說腳本環境需要能夠取消所有事件的預設動作，有些事件還是不能被忽略或者不能被取消。

作者在為他們的EPUB出版品加入腳本功能時，需要為各種具廣泛可能的閱讀系統實作負責（即為，並非所有裝置都具備物理鍵盤，許多狀態下軟鍵盤僅供文字輸入元素啟動）。結果上來說，不推薦僅使用鍵盤事件；推薦常時提供替代方式來啟動想要的行為。

## 6. 固定版面

### 6.1 導論

本章節為非規範性。

本章節定義了規則供固定版面文件 — 在包裝文件中標記為*pre-paginated*的EPUB內容文件，之表述與空間特性的解釋。

本規格不定義如何初始化容器區塊[CSS2]，置放於閱讀系統內容顯示區域中。

> ##### 注意事項
> 
> 請參考固定版面特性[Packages32]以了解更多關於如何指定內容解釋或獨立書脊項目，要被排版成預先分頁內容（即為有固定寬與高空間的頁面）。

### 6.2 內容適用性

一份合規的固定版面文件**必需**符合以下領域需求：

   其**必需**指定其初始容器區塊[CSS2]如在初始容器區塊空間中所定義。

### 6.3 閱讀系統適用性

一個合規的EPUB閱讀系統在處理固定版面文件時，**必需**符合以下領域需求：

- 其**應該**對該文件分配出完整內容顯示區域，如Viewport排版所定義。
- 其**必需**使用在*viewport meta*標籤所表述的空間來對XHTML內容文件進行排版，如同在於HTML中表述ICB所定義。
- 其**必需**使用定義在於SVG中表述ICB的方式給予空間來排版SVG內容文件。

### 6.4 Viewport排版

當對固定版面文件進行排版時，預設目的為內容顯示區域**應該**佔據盡可能多的可用Viewport區域。閱讀系統**不得**插入額外的內容如邊框、邊界，頁首或頁尾到Viewport中。

> ##### 注意事項
> 
> 閱讀系統控制小工具對使用者出現為實作者控制，並且不包含在以上行為預期中。

### 6.5 初始容器區塊空間

#### 6.5.1 以HTML表達

對XHTML固定版面文件而言，初始容器區塊[CSS2]空間**必需**在一個*viewport meta*標籤中表述，使用語法定義在[CSS-Device-Adapt-1]。在本版本的規格中，只有寬度（width）與高度（height）表述**必需**要被閱讀系統所辨識。

> ###### 範例5
> 
> 以下範例表示一個*viewport meta*標籤。
> 
> <head>
>    …
>    <meta name="viewport" content="width=1200, height=600"/>
>    …
> </head>

閱讀系統**必需**固定XHTML內容到初始容器區塊(ICB)，透過*viewport meta*標籤所宣告的空間中 — 定位在初始容器區塊外的內容不應該被看見。當ICB長寬比與閱讀系統內容顯示區域的長寬比不匹配時，閱讀系統**可以**將ICB放置於顯示區塊內以適於使用者介面；換言之，可能會在內容的一側（或兩端）出現橫向塊狀空間。

#### 6.5.2 以SVG表達

對SVG固定版面文件而言，ICB空間**必需**透過*viewBox*屬性[SVG]表述。

> ###### 範例6
> 
> 以下範例表示在SVG內容文件中使用一個*viewBox*屬性來宣告長寬比為寬844像素、高1200像素。
> 
> <svg xmlns="http://www.w3.org/2000/svg"
>      version="1.1" 
>      viewBox="0 0 844 1200">
>    …
> </svg>

## 7. 發音辭典

### 7.1 導論

本章節為非規範性。

W3C發音辭典規格（Pronunciation Lexicon Specification, PLS) [PRONUNCIATION-LEXICON]定義了基於XML的發音辭典的語法與語意，可供自動語音辨識以及文字轉語音（Text-to-Speech, TTS) 引擎使用。

以下章節定義了當PLS文件包含在EPUB出版品時的適用性領域，以及PLS文件與XHTML內容文件建立關聯的規則。

> ##### 注意事項
> 
> 若想要了解更多EPUB 3與語音合成相關的資訊，請參照文字轉語音[EPUB3Overview]。

### 7.2 EPUB出版品適用性

一本EPUB出版品合規的內容解釋包含PLS文件時**必需**符合以下領域需求：

- PLS文件**可以**與XHTML內容文件進行關聯。每一份XHTML內容文件**可以**包含零或多個PLS文件關聯。
- PLS文件與XHTML內容文件產生關聯時**必需**透過使用[HTML]*link*元素其*rel*屬性設定為"*pronunciation*"並且其*type*屬性設定為媒體類型"*application/pls+xml*"。
- *link*元素的*hreflang***應該**在每個連接中都要指定，以及其值在相關的[PRONUNCIATION-LEXICON]受指定時**必需**與該發音字典語言匹配。，
- PLS文件**必需**符合定義在PLS文件 - 內容適用性中的內容適用性領域。
- PLS文件**必需**如同EPUB包裝 - 適用性[Packages32]中的定義被表述及定位。

#### 7.2.1 範本

> ###### 範例7
> 
> 以下範例表示兩個PLS文件（一為中文，另一為蒙古文）與一份XHTML內容文件關聯。
> 
> <html … >    
>     <head>
>         …
>         <link rel="pronunciation" type="application/pls+xml" hreflang="zh" href="../speech/zh.pls"/>
>         <link rel="pronunciation" type="application/pls+xml" hreflang="mn" href="../speech/mn.pls"/>
>     </head>        
>     …
> </html>

### 7.3 內容適用性

一份PLS文件**必需**符合以下領域需求：

**文件特性**
  
- 其**必需**符合定義在XML適用性[EPUB32]中對XML文件的使用性限制。
- 其**必需**為合規的RELAX NG模式PLS文件，其URI在*https://www.w3.org/TR/2008/REC-pronunciation-lexicon-20081014/* [PRONUNCIATION-LEXICON]。

**檔案特性**

- PLS文件檔名**應該**使用副檔名*.pls*。

### 7.4 閱讀系統適用性

閱讀系統具備文字轉語音（TTS）能力**應該**支援PLS文件。

合規的EPUB閱讀系統處理PLS文件時**必需**符合以下領域需求：

- 閱讀系統支援文字轉語音（TTS）**應該**支援[PRONUNCIATION-LEXICON]。
- 其**必需**如[PRONUNCIATION-LEXICON]之定義處理PLS文件
- 其**必需**套用提供的發音程序給所有該XHTML內容文件中其語言[HTML]符合該發音辭典關聯[PRONUNCIATION-LEXICON]的文字節點。語言標籤的配對演算法定義在[BCP47]。
- 當在提供的語言中對提供的字串目標指定多於一個的發音規則，其**必需**給予最後出現的規則優先順序，如此一來任何預先定義的發音規則能被覆蓋。
- 如果其也支援SSML屬性，則**必需**讓任何透過*ssml:ph*屬性提供的發音程序優先，當一個元素包含*ssml:ph*屬性[SSML]，當文字素元素[PRONUNCIATION-LEXICON]與文字節點匹配。

## A. JavaScript epubReadingSystem物件

### A.1 介面定義

本規格延伸[HTML]*Navigator*物件如下：

> #####WebIDL 
> 
> [Exposed=(Window)]
> interface EpubReadingSystem {
>     [Unforgeable] readonly attribute DOMString name;
>     [Unforgeable] readonly attribute DOMString version;
>     boolean hasFeature(DOMString feature, optional DOMString version);
> };
> 
> partial interface Navigator {
>     [Unforgeable, SameObject] readonly attribute EpubReadingSystem epubReadingSystem;
> };

[WEBIDL] 標記法。

> ##### 注意事項
> 
> 本規格不定義一個*epubReadingSystem*特性延伸供*WorkerNavigator*物件[WebWorkers]使用。閱讀系統因此不需要面對在Workers腳本脈絡中遇到*epubReadingSystem*物件，作者也不可依賴其存在。

### A.2 說明

*Navigator.epubReadingSystem*物件提供了一個介面，可以讓腳本化內容文件能夠查詢使用者閱讀系統的資訊。

該物件顯露閱讀系統的特性（名稱與版本），並且提供*hasFeature*手段能用於決定功能是否受到支援。

> ###### 範例8
> 
> JavaScript功能範例展示目前閱讀系統的名稱。
> 
> alert("Reading System name: " + navigator.epubReadingSystem.name);

閱讀系統**必需**在所有載入的腳本化內容文件的*navigator*物件中顯露*epubReadingSystem*物件，包含任何巢狀容器限制腳本脈絡。閱讀系統**必需**確保*epubReadingSystem*物件可被使用，不晚於*DOMContentLoaded*事件被啟動[HTML]。

> ##### 注意事項
> 
> 閱讀系統實作可以在腳本化內容文件中創建複製的*epubReadingSystem*物件副本，以助於技術上實現的理由。在這些狀況中，閱讀系統需要確保該物件的狀態 — 如反映其特性與手段的值 — 在跨所有複製的副本中維持一致。

### A.3 特性

以下特性**必需**在取得關於閱讀系統資訊時提供。

名稱 | 說明
------- | -------
*name* | 返回一個*String*值用來表示閱讀系統的名稱（如"*iBooks*","*Kindle*"）。
*version* | 返回一個*String*值用來表示閱讀系統的版本（如"*1.0*","*2.1.1*"）。
*layoutStyle* | 不再推薦使用*layoutStyle*特性。請參考其在[ContentDocs301]定義已取得用法資訊。

### A.4 手段

#### A.4.1 hasFeature

##### A.4.1.1 說明

*hasFeature*手段返回一個布林值指出是否指定功能的任何版本受到支援，或者當指定的功能無法被辨識時為*undefined*。

包含**選擇性**的*version*參數供查詢可能隨著時間變得不相容的客製化功能。返回的值指出是否只支援特定版本的功能。

作者**不應**在使用查詢本規格定義的功能時包含*version*參數 — 這些功能是為無版本。如果閱讀系統支援定義在本規格中的功能，其**必需**忽略任何提供的*version*參數而回以*true*值。

> ###### 範例9
> 
> JavaScript功能範例展示是否現在的閱讀系統支援使用腳本對DOM進行操弄。
> 
> var feature = "dom-manipulation";
> 
> var conformTest = navigator.epubReadingSystem.hasFeature(feature);
> 
> alert("Feature " + feature + " supported?: " + conformTest);

##### A.4.1.2 功能

以下表格列出一系列功能，支援*epubReadingSystem*物件的閱讀系統**必需**辨識（例如，提供返回值）。對這些功能的支援為**選擇性**。

名稱 | 說明
------- | -------
*dom-manipulation*	 | 腳本**可以**對文件的DOM進行結構變更（僅適用於書脊層級腳本）。
*layout-changes* | 腳本**可以**變更屬性與CSS樣式來影響內容排版（僅適用於書脊層級腳本）。
*touch-events*	 | 該裝置支援觸控事件，以及閱讀系統傳達觸控事件到內容上。
*mouse-events*	 | 該裝置支援滑鼠事件，以及閱讀系統傳達滑鼠事件到內容上。
*keyboard-events* | 該裝置支援鍵盤事件，以及閱讀系統傳達鍵盤事件到內容上。
*spine-scripting* | 指出是否閱讀系統支援書脊層級腳本（即為，如此一來容器限制腳本可以決定是否運作，取決於對最上層內容文件對腳本的支援，在嘗試之前了解是否能成功）。

閱讀程式開發者**可以**添加額外的功能，但是本規格的未來版本可能擴充本清單，將會使客製化功能產生衝突或者變得不相容。

## B. 謝詞與貢獻者

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

## C. 參考資料

### C.1 規範性文件

#### [BCP47]

  [Tags for Identifying Languages](https://tools.ietf.org/html/bcp47). A. Phillips; M. Davis. IETF. September 2009. IETF Best Current Practice. URL: https://tools.ietf.org/html/bcp47

#### [ContentDocs301]

  [EPUB Content Documents 3.0.1](http://www.idpf.org/epub/301/spec/epub-contentdocs.html). URL: http://www.idpf.org/epub/301/spec/epub-contentdocs.html

#### [CSS-Device-Adapt-1]

  [CSS Device Adaptation Module Level 1](https://www.w3.org/TR/css-device-adapt-1/). Rune Lillesveen; Florian Rivoal; Matt Rakow. W3C. 29 March 2016. W3C Working Draft. URL: https://www.w3.org/TR/css-device-adapt-1/

#### [CSS-Fonts-3]

  [CSS Fonts Module Level 3](https://www.w3.org/TR/css-fonts-3/). John Daggett; Myles Maxfield; Chris Lilley. W3C. 20 September 2018. W3C Recommendation. URL: https://www.w3.org/TR/css-fonts-3/

#### [CSS-Text-3-20160119]

  [CSS Text Level 3 (20160119)](https://drafts.csswg.org/date/2016-01-19T17:23:23/css-text/). Elika J. Etemad et al.URL: https://drafts.csswg.org/date/2016-01-19T17:23:23/css-text/

#### [CSS-Text-Decor-3]

  [CSS Text Decoration Module Level 3](https://www.w3.org/TR/css-text-decor-3/). Elika Etemad; Koji Ishii. W3C. 3 July 2018. W3C Candidate Recommendation. URL: https://www.w3.org/TR/css-text-decor-3/

#### [CSS-Values-3]

  [CSS Values and Units Module Level 3](https://www.w3.org/TR/css-values-3/). Tab Atkins Jr.; Elika Etemad. W3C. 31 January 2019. W3C Candidate Recommendation. URL: https://www.w3.org/TR/css-values-3/

#### [CSS-Writing-Modes-3]

  [CSS Writing Modes Level 3](https://www.w3.org/TR/css-writing-modes-3/). Elika Etemad; Koji Ishii. W3C. 24 May 2018. W3C Candidate Recommendation. URL: https://www.w3.org/TR/css-writing-modes-3/

#### [CSS-Writing-Modes-3-20151215]

  [CSS Writing Modes Level 3](https://www.w3.org/TR/2015/CR-css-writing-modes-3-20151215/). Elika Etemad; Koji Ishii. W3C. 15 December 2015. W3C Candidate Recommendation. URL: https://www.w3.org/TR/2015/CR-css-writing-modes-3-20151215/

#### [CSS2]

  [CSS 2](https://www.w3.org/TR/CSS2/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/CSS2/

#### [CSSSnapshot]

  [CSS Snapshot](https://www.w3.org/TR/CSS/). URL: https://www.w3.org/TR/CSS/

#### [DOM-Level-2-Style]

  [Document Object Model (DOM) Level 2 Style Specification](https://www.w3.org/TR/DOM-Level-2-Style/). Chris Wilson; Philippe Le Hégaret. W3C. 13 November 2000. W3C Recommendation. URL: https://www.w3.org/TR/DOM-Level-2-Style/

#### [EPUB-SSV]

  [EPUB Structural Semantics Vocabulary](http://www.idpf.org/epub/vocab/structure/). IDPF. URL: http://www.idpf.org/epub/vocab/structure/

#### [EPUB32]

  [EPUB 3.2](https://www.w3.org/publishing/epub3/epub-spec.html). URL: epub-spec.html

#### [HTML]

  [HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [IPA]

  [IPA Chart](https://www.internationalphoneticassociation.org/content/full-ipa-chart). International Phonetic Association. 2005. URL: https://www.internationalphoneticassociation.org/content/full-ipa-chart

#### [MATHML3]

  [Mathematical Markup Language (MathML) Version 3.0 2nd Edition](https://www.w3.org/TR/MathML3/). David Carlisle; Patrick D F Ion; Robert R Miner. W3C. 10 April 2014. W3C Recommendation. URL: https://www.w3.org/TR/MathML3/

#### [Microdata]

  [HTML Microdata](https://www.w3.org/TR/microdata/). Charles McCathie Nevile; Dan Brickley; Ian Hickson. W3C. 26 April 2018. W3C Working Draft. URL: https://www.w3.org/TR/microdata/

#### [OpenType]

  [OpenType specification](http://www.microsoft.com/typography/otspec/default.htm). Microsoft. URL: http://www.microsoft.com/typography/otspec/default.htm

#### [Packages32]

  [EPUB Packages 3.2](https://www.w3.org/publishing/epub3/epub-packages.html). URL: epub-packages.html

#### [PRONUNCIATION-LEXICON]

  [Pronunciation Lexicon Specification (PLS) Version 1.0](https://www.w3.org/TR/pronunciation-lexicon/). Paolo Baggia. W3C. 14 October 2008. W3C Recommendation. URL: https://www.w3.org/TR/pronunciation-lexicon/

#### [RDFA-CORE]

  [RDFa Core 1.1 - Third Edition](https://www.w3.org/TR/rdfa-core/). Ben Adida; Mark Birbeck; Shane McCarron; Ivan Herman et al. W3C. 17 March 2015. W3C Recommendation. URL: https://www.w3.org/TR/rdfa-core/

#### [RFC2119]

  [Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

#### [SSML]

  [Speech Synthesis Markup Language (SSML) Version 1.1](https://www.w3.org/TR/speech-synthesis11/). Daniel Burnett; Zhi Wei Shuang. W3C. 7 September 2010. W3C Recommendation. URL: https://www.w3.org/TR/speech-synthesis11/

#### [SVG]

  [SVG](https://www.w3.org/TR/SVG/). W3C. URL: https://www.w3.org/TR/SVG/

#### [TrueType]

  [Apple TrueType Reference Manual](https://developer.apple.com/fonts/TrueType-Reference-Manual/). Apple. 2002. URL: https://developer.apple.com/fonts/TrueType-Reference-Manual/

#### [Unicode]

  [The Unicode Standard](https://www.unicode.org/versions/latest/). Unicode Consortium. URL: https://www.unicode.org/versions/latest/

#### [W3CProcess]

  [World Wide Web Consortium Process Document](https://www.w3.org/2015/Process-20150901/). Charles McCathie-Nevile.1 September 2015. URL: https://www.w3.org/2015/Process-20150901/

#### [WAI-ARIA]

  [Accessible Rich Internet Applications (WAI-ARIA) 1.0](https://www.w3.org/TR/wai-aria/). James Craig; Michael Cooper et al. W3C. 20 March 2014. W3C Recommendation. URL: https://www.w3.org/TR/wai-aria/

#### [WEBIDL]

  [Web IDL](https://heycam.github.io/webidl/). Boris Zbarsky. W3C. 15 December 2016. W3C Editor's Draft. URL: https://heycam.github.io/webidl/

#### [WOFF]

  [WOFF File Format 1.0](https://www.w3.org/TR/WOFF/). Jonathan Kew; Tal Leming; Erik van Blokland. W3C. 13 December 2012. W3C Recommendation. URL: https://www.w3.org/TR/WOFF/

#### [WOFF2]

  [WOFF File Format 2.0](https://www.w3.org/TR/WOFF2/). Vladimir Levantovsky; Raph Levien. W3C. 1 March 2018. W3C Recommendation. URL: https://www.w3.org/TR/WOFF2/

#### [XML]

  [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/

#### [XML-NAMES]

  [Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/

### C.2 參考性文件

#### [AttributeExtensions]

  [EPUB Custom Attribute Extensions for Content Documents](http://www.idpf.org/epub/extensions/attributes). URL: http://www.idpf.org/epub/extensions/attributes

#### [EPUB32Changes]

  [EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html). URL: epub-changes.html

#### [EPUB3Overview]

  [EPUB 3 Overview](https://www.w3.org/publishing/epub3/epub-overview.html). URL: epub-overview.html

#### [EPUBAccessibility]

  [EPUB Accessibility](http://www.idpf.org/epub/latest/accessibility). URL: http://www.idpf.org/epub/latest/accessibility

#### [WebWorkers]

  [Web Workers](https://www.w3.org/TR/workers/). Ian Hickson. W3C. 24 September 2015. W3C Working Draft. URL: https://www.w3.org/TR/workers/