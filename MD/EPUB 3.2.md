# EPUB 3.2
最終社群小組規格 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-spec.html
**編輯**：
    Matt Garrish (DAISY Consortium)
    Dave Cramer (Hachette Livre)
**前任編輯**：
    Markus Gylling (International Digital Publishing Forum (IDPF))
    Tzviya Siegman (John Wiley & Sons)
**協助參與：**
    GitHub w3c/publ-epub-revision
    提出問題
    版本紀錄
    修改要求

Copyright © 1999-2019 International Digital Publishing Forum™ and W3C® (MIT, ERCIM, Keio, Beihang)

<hr />

EPUB是國際數位出版論壇（IDPF, International Digital Publishing Forum）的註冊商標

## 概要

EPUB® 3定義了供數位出版品及文件用以傳遞、交換使用的格式。EPUB格式提供了用以呈現、包裝、編碼有結構且在語意上強化的網頁內容——包含HTML、CSS、SVG以及其他資源——以一個單一檔案容易進行傳遞。此規格為本標準第二次主要改版。

EPUB 3廣泛地作為數位書籍（電子書）規格被採納，這次的改版持續增加本格式的能力來提供更廣泛為對出版品需求的支援，包括複雜版面、富媒體及互動性，和全球排版功能。可期待EPUB 3格式將被應用於更廣範圍的內容，如書籍、雜誌、教育、專業以及科學出版品上。

EPUB 3以模組化制定：其包含了一系列的規格來定義標準的核心特色與功能。本規格為本標準的主要開始點，但列於本規格中的所有規格都屬於EPUB 3的一部分。對於這些規格關鍵概念與定義的索引提供於本規格文末。

參考性的[EPUB3Overview]提供了EPUB 3的一般性導論。對於前版本的技術變更點則列於另一份參考性的[EPUB32Changes]。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 導論
1.1 規格
1.2 結構
1.3 術語
1.4 適用性
2. 適用領域
2.1 EPUB出版品
2.2 EPUB閱讀系統
3. 出版資源
3.1 核心媒體類型
3.1.1 導論
3.1.2 支援的媒體類型
3.1.3 外部資源
3.2 資源位置
3.3 XML適用性
A. 不支援的功能
A.1 不再支援的功能
A.2 遺存功能
B. 索引
C. 謝詞與貢獻者
D. 參考資料
D.1 規範性文件
D.2 參考性文件

<hr />

## 1. 導論

### 1.1 規格

EPUB 3標準原生使用模組化制定，核心功能以及機能定義於一系列子規格中。

本規格陳述該系列中最上層的規格。包含了EPUB出版品（使用本標準打造的產品），以及EPUB閱讀系統（用來閱讀EPUB出版品並將內容呈現給使用者的應用程式）的適用性需求。

其他組成EPUB 3的規格如以下：

- EPUB包裝 [Package32] ——定義了每一份內容解釋的必要項目

- EPUB內容文件 [Packages32]——定義了EPUB出版品中XHTML、SVG與CSS的規格

- EPUB媒體層疊 [MediaOverlays32]——定義了供文字與語音同步的格式以及處理模型

- EPUB開放容器格式 [OCF32]——定義了將一組相關的資源打包到單一檔案（ZIP）EPUB容器的檔案格式與處理模型

- EPUB無障礙功能 [EPUBAccessibility]——定義了EPUB出版品無障礙功能的適用範圍並探索其需求

本清單可是整體可視為EPUB的完整規格，也包含了可被引用為標準的功能。我們會週期性地以開發延伸規格的方式加入新功能。定義在標準核心改版外的功能與機能不會被正式地視為標準的一部分，但作者以及閱讀系統開發者仍可參考使用。

### 1.2 結構

本章節為非規範性。

本章節透過EPUB規範所定義的中心產品：EPUB出版品，來檢視EPUB規範的結構。

一本EPUB出版品包含一或多個內容解釋（Renditions），每一份都由稱為EPUB包裝（Package）所呈現。一份EPUB包裝包含所有內容排版所必要的資源。這些的關鍵檔案則是包裝文件，其中包括所有詮釋資料，閱讀系統可以用來對使用者顯示（例如在書架上顯示書名與作者名，或者處理詮釋資料來顯示該書是固定版面或者能夠重排）。其也包含了完整資源的宣告，也包括一份書脊（Spine）作為使用者依序閱讀內容時，該如何排列文件的順序清單。

一份EPUB包裝也包含了另一個關鍵檔案稱為EPUB導覽文件。該文件提供了關鍵導覽能力，像是目錄，能讓使用者迅速且輕鬆地巡覽內容。

EPUB包裝的需求定義在[Packages32]中。

EPUB出版品的資源以ZIP技術為基礎封存，其副檔名為*.epub*，用於傳遞使用。作為通用的ZIP封存檔，EPUB出版品可以被多種軟體程式解壓縮，簡化製作與使用的程序。

該容器格式不僅提供判斷ZIP壓縮後的內容是否為EPUB出版品（透過*mimetype*檔案）的手段，也提供了對於資訊性資源的通用命名目錄（*/META-INF*）。這些資源的關鍵是*container.xml*檔案，用於告知閱讀系統包裝文件所在。

容器格式定義於[OCF32]。

圖片1 以下範例將EPUB格式的結構以視覺化表現

EPUB出版品的結構與容器只是整體格式的一半，另一半則是該如何將內容顯示給使用者。本格是基於開放網頁平台而能得惠於：XHTML與SVG兩項，稱為EPUB內容文件，這些文件通常會指向其他更多的資源用於正確地排版顯示，包括影像、聲音與影片片段、腳本與樣式表。

關於製作EPUB內容文件的規則與基本需求，詳細資訊在[ContentDocs32]。而無障礙功能的需求則定義在[EPUBAccessibility]。

媒體層疊文件需匹配EPUB內容文件。其提供了宣告性的標注來讓EPUB內容文件中的文字可以和預錄好的聲音同步播放，結果可以提供文字會隨著朗讀進度被強調的伴讀體驗。媒體層疊文件定義在[MediaOverlays32]。

概念上非常簡單，一個EPUB出版品就只是一系列HTML頁面和其他獨立素材以ZIP包裝封存。關於EPUB出版品的主要功能與特色，可用提升閱讀體驗的額外資訊可由其他參考規格取得，而更一般性的EPUB 3功能導論請見資訊性質的[EPUB3Overview]。

### 1.3 術語

專屬於EPUB 3的術語在本文件中以括號（譯注：英文版為首字大寫。範例如「作者」，「閱讀系統」）。術語與定義的完整清單提供於[EPUB32]。

每章節術語第一次出現時才會連結至其定義。

#### 作者（Author）

為一本EPUB出版創作負責的人物（一或多位）或組織。作者不需要是內容的創作者。

#### 內容顯示區域（Content Display Area）

該區域位於顯示範圍內，用來顯示EPUB內容文件。內容顯示區域排除任何邊框、邊界、頁首、頁尾以及其EPUB閱讀系統可能會加入顯示範圍的裝置。

在同步跨頁的狀況下，顯示範圍包含了兩個內容顯示區域。

#### 核心媒體類型資源（Core Media Type Resource）

不需要提出回退的出版品資源（相對於外部資源）。

#### EPUB容器（EPUB Container）

基於ZIP的EPUB出版品包裝與傳遞格式，定義在OCF ZIP容器[OCF32]。

#### EPUB內容文件（EPUB Content Document）

出版品資源使用XHTML或SVG媒體類型，其中包含EPUB出版品的全部或者部分內容（即為文字、視覺及/或聲音內容）。這些資源需要遵從對應的XHTML或SVG定義，才能置放在書脊中，或者被其他EPUB內容文件所參照連結。

一份EPUB內容文件就是核心媒體類型資源，所以可以被包含在EPUB出版品而不需提供任何回退。

#### EPUB導覽文件（EPUB Navigation Document）

一份特化的XHTML內容文件，其中包含人讀與機讀的全域導覽資訊。EPUB導覽文件必須嚴格地符合EPUB導覽文件[Package32]的規格。

#### EPUB包裝（EPUB Package）

一個邏輯文件實體，包含了一系列有相互關係的資源以呈現一本EPUB出版品的內容解釋，如包裝文件所定義。

#### EPUB出版品（EPUB Publication）

一個或多個內容的集合，須符合規格，以EPUB容器包裝。

一本EPUB出版品一般代表了單一智慧財產或者藝術作品，但規格本身卻不限制內容的本質。

#### EPUB閱讀系統或閱讀系統（EPUB Reading System）

一個用來處理EPUB出版品的系統，用於向使用者顯示符合規格的內容。

#### 固定版面文件（Fixed-Layout Document）

一份EPUB內容文件在內容文件的書脊中直接被指定成預排版，如同內容解釋：排版屬性所定義[Package32]。

另一個面向是用於如何排列固定版面文件，如固定版面所定義[ContentDocs32]。

#### 外部資源（Foreign Resource）

非核心媒體類型資源的出版品資源。外部資源需要提供如外部資源中所定義的回退。

#### 本地資源（Local Resource）

位於EPUB容器中的資源。

參照出版品資源位置，以了解媒體類型與資源位置的特殊規則。

#### 宣告（Manifest）

所有出版品資源的列表，用於建構一本EPUB出版品的內容解釋。

想了解更多請參考宣告[Package32]。

#### 媒體層疊文件（Media Overlay Document）

一份XML文件，讓XHTML內容文件以及預錄的聲音旁白產生關聯，以提供同步播放體驗，定義在[MediaOverlays32]。

#### 包裝文件（Package Document）

一個出版品資源，用以解釋一份EPUB出版品的內容解釋，如包裝文件所定義[Package32]。包裝文件乘載了關於內容解釋的詮釋資訊，提供資源的宣告以及定義了預設閱讀順序。

#### 出版品資源（Publication Resource）

在一本EPUB出版品中的資源，其中包含內容，或者能助於至少一份內容解釋用以排列顯示內容使用。若缺少這份資源，EPUB出版品可能無法如作者所想像一般顯示內容。出版資源可包括：內容解釋的包裝文件、EPUB內容文件、CSS樣式表、聲音、影片、圖片、嵌入字型與腳本。

除去包裝文件自身，用於顯示內容解釋的出版品資源均列於內容解釋的宣告[Package32]，並且置放到EPUB容器檔案指定的位置中（除非指定到其他出版品資源位置）。

不屬於出版品資源的資源，例如：包裝文件連結[Packages32]的元素，以及被視為外連超連結或者被解析為遠端資源（例如在[HTML]中a元素裡href屬性所指定的連結）。

#### 發佈識別碼（Release Identifier）

發布識別碼在任何狀況下都可以讓EPUB出版品彼此做出比對，以確定是否為一致、為不同版本，或者沒有關聯。

想了解更多資訊，請參照發佈識別碼[Packages32]。

#### 遠端資源（Remote Resource）

位置位於EPUB容器之外的資源，一般位於線上。

請參考出版品資源位置已獲得媒體類型對資源位置的特殊規則。

#### 內容解釋（Rendition）

EPUB出版品的一種內容顯示方式，如EPUB包裝中所解釋。

#### 有腳本的內容文件（Scripted Content Document）

包含腳本的EPUB內容文件，或者XHTML內容文件包含[HTML]表單。

想了解更多資訊，請參照腳本[ContentDocs32]。

#### 書脊（Spine）

一份出版品資源的順序清單，一般資源為EPUB內容文件[Packages32]，表現了該份EPUB出版品內容解釋的預設閱讀順序。

想了解更多資訊，請參照書脊[Packages32]。

#### SVG內容文件（SVG Content Document）

一份符合SVG內容文件限制的EPUB內容文件[ContentDocs32]。

#### 同步跨頁（Synthetic Spread）

在設備螢幕上持續排版顯示兩個相鄰接的頁面。

#### 文字轉換語音（Text-to-Speech,TTS）

透過合成語音，將EPUB出版品的文字內容處理成人工聲音朗讀出來。

#### 主要層級內容文件（Top-level Content Document）

在書脊內被指定的EPUB內容文件，不管是直接指定或者透過回退鍊[Packages32]。

#### 獨特識別碼（Unique Identifier）

獨特識別碼是EPUB出版品的主要識別碼，定義於unique-identifier屬性[Packages32]。獨特識別碼可由同一本EPUB出版品中的一或多個內容解釋所共享。

內容明顯的改版、摘要等，則需要新的獨特識別碼。

#### 顯示範圍（Viewport）

EPUB閱讀系統將EPUB出版品視覺上顯示給使用者看的範圍。

#### XHTML內容文件（XHTML Content Document）

一份符合[HTML]中定義XHTML內容文件規範的EPUB內容文件[ContentDocs32]。

XHTML內容文件中所使用的XHTML語法定義於[HTML]。

### 1.4 適用性

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、不得（MUST NOT）、推薦（RECOMMENDED）、應該（SHOULD）、不應（SHOULD NOT）**應該以[RFC2119]之記述解釋。

## 2. 適用領域

### 2.1 EPUB出版品

一本EPUB出版品**必需**符合以下領域需求：

#### 包裝（Packages）

- **必需**包含一個以上的EPUB包裝，每一個包裝都**必需**符合定義於[Packages32]的要求。

#### 無障礙功能（Accessibility）

- **應該**符合定義於[EPUBAccessibility]的無障礙功能需求。

#### 出版品資源（Publication Resources）

- 所有出版品資源**必需**符合對核心媒體類型和外部資源的規定，並且放置在指定的出版品資源位置。

#### 容器（Container）

- **必需**以定義於[OCF32]的EPUB容器格式打包

### 2.2 EPUB Reading Systems

一個EPUB閱讀系統**必需**符合以下領域需求：

#### EPUB 3處理
 
- **必需**以定義於[OCF32]的方式處理EPUB容器。
- **必需**以定義於[Packages32]的方式處理EPUB包裝。
- **可以**隨意支援各種外部資源類型，但**必需**為不支援的外部資源提供回退，如外部支援中的定義。
- **應該**支援遠端資源，如資源位置所定義。
- **必需**以定義於XHTML內容文件——閱讀系統適用性[ContentDocs32]的方式處理XHTML內容文件。
- **必需**以定義於SVG內容文件——閱讀系統適用性[ContentDocs32]的方式處理SVG內容文件。
- 若提供顯示範圍，則**必需**以定義在CSS樣式表——閱讀系統適用性[ContentDocs32]的方式支援XHTML內容文件的視覺排版。
- 若提供顯示範圍，則**必需**支援圖片類的核心媒體類型資源。
- 若能夠播放預錄的聲音，則**必需**支援聲音核心媒體類型資源，且**應該**支援媒體層疊[MediaOverlays32]。
- 若支援文字轉換語音（TTS, text-to-Speech）功能，則**應該**支援XHTML內容文件中的發音辭典[ContentDocs32]、[CSS3Speech]以及SSML屬性[ContentDocs32]。

> ##### 注意事項
> 
> 推薦閱讀系統至少支援H.264[H264]與VP8[RFC6386]影片編碼之一，但這並非為支援性需求——一個閱讀程式可能支援其他影片編碼，或者完全不支援。作者與閱讀系統哎發者需要考量格式被接受的廣度、影片播放品質，以及使用該項技術的授權費，已做出瘸定該包含、實作那一種影片支援，或者兩者兼備

#### 無障礙功能

- **應該**符合對閱讀系統在[EPUBAccessibility]中的無障礙功能需求。

#### 向後支援性

- 在包裝文件版本屬性小於「3.0」時，**必需**嘗試處理EPUB出版品中任何提供的內容解釋。

- 版本號較舊的EPUB出版品不會一直如同預期一般顯示，除非以當時的規格進行處理。閱讀系統**應該**支援已那些規格定義的EPUB出版品。

#### 向前支援性

- 在包裝文件版本屬性大於「3.0」時，**必需**嘗試處理EPUB出版品中任何提供的內容解釋。

#### XML處理

- **必需**為適用的非驗證處理器[XML]。
- **必需**為適用的處理器，如[XML-NAMES]所定義。
- **必需**為適用的應用程式，如[XMLBase]所定義。

> ##### 注意事項
> 
> [HTML]與[SVG]移除了對[XMLBase]的支援，作者建議避免使用這項功能。

> ##### 注意事項
> 
> 一個合適的閱讀系統並不一定是單一功能的程式或者設備，可以能分散式系統的方式存在。

## 3. 出版品資源

### 3.1 核心媒體類型

#### 3.1.1 導論

一本EPUB出版品中的所有內容解釋一般包含許多出版品資源。這些資源可以分為兩項範疇：能被包含而無須提供回退（核心媒體類型資源），以及不能的（外部資源）。

作者可自由使用這兩種類型的資源來建構EPUB出版品，但是必須注意到一些閱讀系統可能不會處理所使用到的外部資源。

EPUB出版品設計供完善的閱讀系統處理使用，是故需要一套回退機制來確保使用外部資源不會對使用者消費資源造成影響。本章節列出一系列核心媒體類型資源以及用以保障內容完整性的回退機制。

#### 3.1.2 支援的媒體類型

出版品資源符合以下MIME媒體類型[RFC2046]規格者可以被包含在EPUB出版品中而無需回退。

以下表格個欄位呈現這些資訊：

- 媒體類型——MIME媒體類型[RFC2046]用於在宣告中呈現出版品資源[Packages32]。<br />如果列出一個以上的媒體類型時，第一個是偏好的媒體類型，建議使用偏好的媒體類型於所有新的EPUB出版品中。
- 內容類別定義——該核心媒體類型資源需要符合的規格。
- 適用範圍——出版品內容類型所適用的媒體類型以及內容類型定義。

媒體類型 | 內容類型定義 | 適用範圍
------- | ------- | -------
圖片 | 　 | 　
image/gif | [GIF] | 	GIF圖片
image/jpeg | [JPEG] | JPEG圖片
image/png | [PNG] | PNG圖片
image/svg+xml | 	SVG內容文件[ContentDocs32] | SVG文件
聲音 | 　 | 　
audio/mpeg	 | [MP3] | 	MP3聲音
audio/mp4 | [MPEG4-Audio], [MP4]	 | 使用MP4容器的AAC LC聲音
影片 | 　 | 　
EPUB 3能夠包含任何影片編碼的影片，而不需提供回退，所以沒有任何技術上成立的核心媒體類型資源。請參考EPUB出版品注意事項——閱讀系統適用性，以瞭解對EPUB出版品支援影片編碼的資訊性推薦。 | 　 | 　
樣式 | 　 | 
text/css	 | CSS Style Sheets<br />[ContentDocs32] | CSS樣式表
字型 | 　 | 　
EPUB 3能夠包含任何格式的字型資源，而不需提供回退，CSS已經定義了字型的回退機制。請參考EPUB內容文件確認EPUB出版品的支援需求。 | 　 | 
font/ttf<br />application/font-sfnt | [TrueType]	 | TrueType fonts
font/otf<br />application/font-sfnt<br />application/vnd.ms-opentype | [OpenType] | OpenType fonts
font/woff<br />application/font-woff | [WOFF] | WOFF fonts
font/woff2 | [WOFF2] | WOFF2 fonts
其他 | 　 | 　
application/xhtml+xml | XHTML Content Documents<br />[ContentDocs32]	 | XHTML內容文件使用XHTML語法 [HTML].
application/javascript<br />text/javascript | [RFC4329] | 腳本
application/x-dtbncx+xml | [OPF2] | 過去舊有的NCX
application/smil+xml | [MediaOverlays32] | EPUB媒體層疊文件application/pls+xml | [PRONUNCIATION-LEXICON] | 文字轉換語音 (TTS) 發音辭典

#### 3.1.3 外部資源

EPUB出版品中的外部資源如果不列在書脊的itemref元素[Packages32]，或者可以直接以原生格式顯示在EPUB內容文件中（例如，使用[HTML]嵌入內容或者[SVG]image以及foreignObject元素），**可以**被包含卻無需提供回退

> ##### 注意事項
> 
> 這項例外讓作者可以在EPUB容器內包含EPUB閱讀系統不會使用的資源。這項例外的主要案例可讓資料檔案隨著EPUB出版品移動，無論是供腳本在其所構成的EPUB內容文件使用，還是供外部程式使用（例如：科學期刊可能包含資料組，配合教學告知如何將其從EPUB容器中取出）

當一份外部資源包含在書脊中，或者直接在EPUB內容文件中以期原生格式顯示，就**必需**包含對核心媒體類型資源的回退。回退可以以下兩種形式擇一：

- 採該格式固有的回退機制（例如能夠提供多於一種的媒體類型，或者在該媒體類型無法顯示時，顯示取代的嵌入訊息）；
- 宣告回退 [Packages32]。

宣告回退是包裝文件的一項功能，可以創建回退鍊指向核心媒體類型資源。主要應用在創建對列於書脊中的外部資源的回退[Packages32]，尤其在缺少固有回退機制時（例如[HTML]的img元素）。

請參考[HTML]及[SVG]規格確認各種元素提供的固有回退機制。

### 3.2 資源位置

所有的出版品資源**必需**位於EPUB容器中，除了以下例外：

- 聲音資源**可以**位於EPUB容器之外。
- 影片資源**可以**位於EPUB容器之外。
- 由腳本所取得的資源**可以**位於EUB容器之外。
- 字型資源**可以**位於EPUB容器之外。

> ##### 範本1
> 
> 以下範本提供參考，如何將位於EPUB容器內的聲音檔案放在XHTML內容文件中
> 
> <audio src="audio/ch01.mp4" controls="controls"/>


> ##### 範本2
> 
> 以下範本提供參考，如何將位於EPUB容器外的聲音檔案放在XHTML內容文件中
> 
> <audio src="http://www.example.com/book/audio/ch01.mp4" controls="controls"/>

> ##### 注意事項 
> 
> 作者鼓勵使用位於EPUB容器內的本地聲音、影片與腳本資源，這樣可以讓讀者在不同的連線狀態下，都能夠存取完整的呈現。

> ##### 注意事項 
> 
> 本章節對出版品資源位置的規則適用於所有資源，無論是核心媒體類型資源還是外部資源。

> ##### 注意事項 
> 
> 將遠端資源包含在EPUB出版品的方式需要在宣告item元素中使用remote-resource屬性來指明。

### 3.3 XML Conformance

任何出版品資源若為基於XML的媒體類型，則**必需**符合以下限制：

- **必需**符合定義於文件適用性[XML-NAMES]的XML 1.0文件。
- 外部識別碼**不得**出現在文件類別宣告[XML]。
- **不得**使用XInclude [XInclude]。
- **必需**以UTF-8或UTF-16編碼[Unicode]。

以上限制適用於所有出版品資源，無論是核心媒體資源還是外部資源。

## A. 不支援的功能

本規格與其姐妹規格所包含的部分功能不再推薦使用，或者僅為了對舊版本支援為由而維持。本章節定義了這些指定功能的意義，以及對於這些功能的支援期待。

### A.1 不再支援的功能

不再支援的功能於本版本規格中不再推薦使用。不再支援的功能在閱讀系統及/或EPUB出版品中有所限制或者不再支援。如果功能被標註為不再支援，以下敘述為真：

- 強烈**推薦**作者不要在他們的EPUB出版品中使用該功能。
- 閱讀系統**可以**支援該功能。

> ##### 注意事項 
> 
> 建議開發者在添加新的支援時，考量會不會遇到不再支援功能的可能性。

驗證工具**應該**在檢查EPUB出版品時，應該提醒作者包含不再支援的功能。

### A.2 遺存功能

遺存功能是限制僅能用於早於EPUB3.0前版本內容中的功能。如果功能被標註為遺存，以下敘述為真：

- 作者**可以**為了相容性目的包含遺存功能。
- 閱讀系統**不可**在適用本版本的EPUB同時支援遺存功能。

驗證工具**不應**警告作者在EPUB出版品裡有遺存功能，由於包含功能本身對於向後相容性而言合法。但驗證工具**必需**在遺存功能不符合其定義或者破壞使用需求時警告作者。


## B. 索引

本章節為非規範性。

本索引指出EPUB 3中各項關鍵概念之定義所在，包含元素、屬性、特性之定義。

- accessibility [EPUBAccessibility]
    - accessible publications
    - authoring and consumption
    - discovery metadata
    - distribution concerns
    - optimized publications
- core media type resources
    - foreign resources
    - manifest fallbacks [Packages32]
    - supported media types
- core specifications
- CSS style sheets [ContentDocs32]
    - CSS snapshot support
    - prefixed properties
    - Reading System overrides
- EPUB Navigation Document [Packages32]
    - custom nav elements
    - hidden attribute
    - landmarks nav element
    - nav element restrictions
    - page-list nav element
    - toc nav element
- fixed layouts [Packages32]
    - content dimensions [ContentDocs32]
        - SVG initial containing block (viewBox)
        - XHTML initial containing block (viewport meta)
    - package metadata
        - rendition:layout property
        - rendition:orientation property
        - rendition:page-spread-center property
        - rendition:page-spread-left property
        - rendition:page-spread-right property
        - rendition:spread property
        - viewport rendering [ContentDocs32]
- Media Overlays Documents [MediaOverlays32]
    - basic playback behaviors
        - audio playback
        - content rendering
        - timing and synchronization
    - escapability
    - interaction with content documents
        - embedded audio and video
        - navigation
        - text-to-speech playback
    - loading
    - navigation document playback
    - packaging
        - attaching to content documents
        - metadata
            - active-class property
            - duration property
            - narrator property
            - playback-active-class property
    - playback granularity
    - relationship to content documents
        - embedded media
        - navigation
        - text-to-speech playback
    - skippability
    - smil element
        - body element
            - par element
                - audio element
                - text element
            - seq element
        - head element
            - metadata element
    - semantic inflection (epub:type)
    - structure
    - styling
- OCF abstract container [OCF32]
    - file and directory structure
    - file name requirements
    - META-INF directory
        - container.xml file
            - link element
            - rootfile element
        - encryption.xml file
            - EncryptedData element
            - EncryptedKey element
            - encryption element
            - listing obfuscated resources
            - order of compression and encryption
                - Compression element
            - restricted files
        - manifest.xml file
        - metadata.xml file
        - rights.xml file
        - signatures.xml file
            - container signature
            - signature restrictions
    - relative path references
- OCF ZIP container [OCF32]
    - encryption
        - restricted files
    - media type identification (mimetype)
    - obfuscation (was font obfuscation)
        - algorithm
        - identifying resources
        - key
    - ZIP requirements
- Package Document [Packages32]
    - collection element
        - linking resources
        - metadata
        - roles
    - default vocabularies
    - fixed layout properties — see also fixed layouts
    - identifiers
        - release identifier
        - unique identifier
        - unique-identifier attribute
    - layout properties
        - rendition:align-x-center property
        - rendition:flow property
    - metadata element
        - core metadata requirements
        - dc:identifier element
        - dc:language element
        - dc:title element
            - importance of order
        - dcterms:modified property (last modified date)
        - Dublin Core optional elements
            - contributors
            - creators
            - publication date
            - publication types
            - subjects
        - link element
            - link relationships
            - manifest requirements
            - linked metadata records
            - resource location
        - meta element
            - expressing properties
            - refines attribute
            - value scheme
    - manifest element
        - item element
            - fallbacks
            - media overlay association
            - media type
            - properties
            - resource inclusion requirements
    - NCX (legacy)
    - package element
        - prefix declarations
        - version number
    - property data type
    - reserved prefixes
    - shared attributes
    - spine element
        - itemref element
            - linearity
            - referencing manifest items
        - page progression
        - resource inclusion requirements
- registries
    - Collection Roles
    - Identifier Schemes
    - Optimized Publication Standards
    - Publication Types
    - Subject Authorities
- remote resources
- scripting [ContentDocs32]
    - contexts (container-constrained and spine-level)
    - epubReadingSystem object
        - description
        - hasFeature method
            - description
            - features
        - interface definition
        - properties
    - event model
    - security
- SVG Content Documents [ContentDocs32]
    - restrictions
    - semantic inflection
    - SVG version conformance
- terminology
- vocabularies
    - Accessibility
    - Link
    - Manifest Properties
    - Media Overlays Metadata
    - Meta Properties
    - Publication Rendering (rendition: properties)
    - Spine Properties
    - Structural Semantics
- XHTML Content Documents [ContentDocs32]
    - custom attributes
    - discouraged constructs (*rp* and *embed*)
    - embedded MathML
    - embedded SVG
        - application of CSS styles
    - foreign resource restrictions
    - HTML version conformance
    - pronunciation lexicons (PLS)
    - RDFa and microdata (semantic enrichment)
    - semantic inflection
        - default vocabulary
        - epub:type attribute
        - prefix declarations
        - reserved prefixes
    - Speech Synthesis Markup Language (SSML)
        - ssml:ph attribute
        - ssml:alphabet attribute
    - SVG
    - Unicode restrictions
- XML conformance

## C. 謝詞與貢獻者

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

## D. 參考資料

### D.1 規範性文件

#### [ContentDocs32]

   [EPUB Content Documents 3.2](https://www.w3.org/publishing/epub3/epub-contentdocs.html). URL: epub-contentdocs.html

#### [CSS3Speech]

   [CSS Speech Module](https://www.w3.org/TR/css3-speech/). Daniel Weck. W3C. 5 June 2018. W3C Note. URL: https://www.w3.org/TR/css3-speech/

#### [EPUBAccessibility]

   [EPUB Accessibility](http://www.idpf.org/epub/latest/accessibility). URL: http://www.idpf.org/epub/latest/accessibility

#### [GIF]

   [Graphics Interchange Format](https://www.w3.org/Graphics/GIF/spec-gif89a.txt). CompuServe Incorporated. 31 July 1990. URL: https://www.w3.org/Graphics/GIF/spec-gif89a.txt

#### [HTML]

   [HTML](https://www.w3.org/TR/html/). W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/

#### [JPEG]

   [JPEG File Interchange Format](https://www.w3.org/Graphics/JPEG/jfif3.pdf). Eric Hamilton. C-Cube Microsystems. Milpitas, CA, USA. September 1992. URL: https://www.w3.org/Graphics/JPEG/jfif3.pdf

#### [MediaOverlays32]

   [EPUB Media Overlays 3.2](https://www.w3.org/publishing/epub3/epub-mediaoverlays.html). URL: epub-mediaoverlays.html

#### [MP3]

   [Information technology -- Coding of moving pictures and associated audio for digital storage media at up to about 1,5 Mbit/s -- Part 3: Audio](https://www.iso.org/standard/22412.html). ISO/IEC. August 1993. Published. URL: https://www.iso.org/standard/22412.html

#### [MP4]

   [Information technology -- Coding of audio-visual objects -- Part 14: MP4 file format](https://www.iso.org/standard/75929.html). ISO/IEC. November 2018. Published. URL: https://www.iso.org/standard/75929.html

#### [MPEG4-Audio]

   [Information technology -- Coding of audio-visual objects -- Part 3: Audio](https://www.iso.org/standard/53943.html). ISO/IEC. September 2009. Published. URL: https://www.iso.org/standard/53943.html

#### [OCF32]

   [Open Container Format (OCF) 3.2](https://www.w3.org/publishing/epub3/epub-ocf.html). URL: epub-ocf.html

#### [OpenType]

   [OpenType specification](http://www.microsoft.com/typography/otspec/default.htm). Microsoft. URL: http://www.microsoft.com/typography/otspec/default.htm

#### [OPF2]

   [Open Packaging Format 2.0.1](http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm). URL: http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm

#### [Packages32]

   [EPUB Packages 3.2](https://www.w3.org/publishing/epub3/epub-packages.html). URL: epub-packages.html

#### [PNG]

   [Portable Network Graphics (PNG) Specification (Second Edition)](https://www.w3.org/TR/PNG/). Tom Lane. W3C. 10 November 2003. W3C Recommendation. URL: https://www.w3.org/TR/PNG/

#### [PRONUNCIATION-LEXICON]

   [Pronunciation Lexicon Specification (PLS) Version 1.0](https://www.w3.org/TR/pronunciation-lexicon/). Paolo Baggia. W3C. 14 October 2008. W3C Recommendation. URL: https://www.w3.org/TR/pronunciation-lexicon/

#### [RFC2046]

   [Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types](https://tools.ietf.org/html/rfc2046). N. Freed; N. Borenstein. IETF. November 1996. Draft Standard. URL: https://tools.ietf.org/html/rfc2046

#### [RFC2119]

   [Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

#### [RFC4329]

   [Scripting Media Types](https://tools.ietf.org/html/rfc4329). B. Hoehrmann. IETF. April 2006. Informational. URL: https://tools.ietf.org/html/rfc4329

#### [SVG]

   [SVG](https://www.w3.org/TR/SVG/). W3C. URL: https://www.w3.org/TR/SVG/

#### [TrueType]

   [Apple TrueType Reference Manual](https://www.w3.org/TR/SVG/). Apple. 2002. URL: https://developer.apple.com/fonts/TrueType-Reference-Manual/

#### [Unicode]

   [The Unicode Standard](https://www.unicode.org/versions/latest/). Unicode Consortium. URL: https://www.unicode.org/versions/latest/

#### [WOFF]

   [WOFF File Format 1.0](https://www.w3.org/TR/WOFF/). Jonathan Kew; Tal Leming; Erik van Blokland. W3C. 13 December 2012. W3C Recommendation. URL: https://www.w3.org/TR/WOFF/

#### [WOFF2]

   [WOFF File Format 2.0](https://www.w3.org/TR/WOFF2/). Vladimir Levantovsky; Raph Levien. W3C. 1 March 2018. W3C Recommendation. URL: https://www.w3.org/TR/WOFF2/

#### [XInclude]

   [XML Inclusions (XInclude) Version 1.0 (Second Edition)](https://www.w3.org/TR/xinclude/). Jonathan Marsh; David Orchard; Daniel Veillard. W3C. 15 November 2006. W3C Recommendation. URL: https://www.w3.org/TR/xinclude/

#### [XML]

   [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). Tim Bray; Jean Paoli; Michael Sperberg-McQueen; Eve Maler; François Yergeau et al. W3C. 26 November 2008. W3C Recommendation. URL: https://www.w3.org/TR/xml/

#### [XML-NAMES]

   [Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). Tim Bray; Dave Hollander; Andrew Layman; Richard Tobin; Henry Thompson et al. W3C. 8 December 2009. W3C Recommendation. URL: https://www.w3.org/TR/xml-names/

#### [XMLBase]

   [XML Base (Second Edition)](https://www.w3.org/TR/xmlbase/). Jonathan Marsh. W3C. 28 January 2009. W3C Recommendation. URL: https://www.w3.org/TR/xmlbase/

### D.2 參考性文件

#### [EPUB32Changes]

   [EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html). URL: epub-changes.html

#### [EPUB3Overview]

   [EPUB 3 Overview](https://www.w3.org/publishing/epub3/epub-overview.html). URL: epub-overview.html

#### [H264]

   [H.264 : Advanced video coding for generic audiovisual services](https://www.itu.int/ITU-T/recommendations/rec.aspx?rec=13189). 2017-04-13. URL: https://www.itu.int/ITU-T/recommendations/rec.aspx?rec=13189

#### [RFC6386]

   [VP8 Data Format and Decoding Guide](https://tools.ietf.org/html/rfc6386). J. Bankoski; J. Koleszar; L. Quillio; J. Salonen; P. Wilkins; Y. Xu. IETF. November 2011. Informational. URL: https://tools.ietf.org/html/rfc6386