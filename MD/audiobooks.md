# 有聲書
W3C推薦規格 10 November 2020

**本版本：**
    https://www.w3.org/TR/2020/REC-audiobooks-20201110/
**最新發佈版本：**
    https://www.w3.org/TR/audiobooks/
**最新編輯草稿：**
    https://w3c.github.io/audiobooks/
**實作報告：**
    https://www.w3.org/publishing/groups/publ-wg/implementation/results.html
**之前的版本：**
    https://www.w3.org/TR/2020/PR-audiobooks-20201001/
**編輯：**
    Wendy Reid (Rakuten/Kobo)
    Matt Garrish (DAISY Consortium)
**協助參與：**
    GitHub w3c/audiobooks
    提出問題
    版本紀錄
    修改要求

請由勘誤表確認發表後回報的各項錯誤或問題。

也可見翻譯。

本文件也供此非規範性格式使用：EPUB。

Copyright © 2019-2020 W3C® (MIT, ERCIM, Keio, Beihang). 適用於W3C之責任、商標以及許可之文件授權規則。

<hr />

## 概要

本規格說明了創建有聲書時的需求，使用了出版品宣告規格中的子規格。

## 本文件狀態

本章解釋了本文件在其發布時的狀態。其他文件可以取代本文件。

當下W3C出版品清單以及本技術報告的最新改版可於W3C技術報告索引下找到 https://www.w3.org/TR/。

本文件由出版工作小組發布為推薦規格。

推薦使用GitHub Issues對本規格進行討論。此外，你也可以將意見寄送到我們的郵寄列表。請寄送到 public-publ-wg@w3.org （郵件紀錄）。

W3C推薦規格為一份規格，其經過了密集的共識建立，並且受到了W3C及其會員的承認。本規格受到廣泛的採納，W3C推薦本作為網頁標準。本推薦規格的未來更新可能會包含新的功能。

本文件由基於2017年8月1日W3C專利政策，由一個小組運作而產生。W3C維護一份公開的專利披露清單，其由該小組提交已建立連結，該頁面也包含了如何披露專利的程序。任何個人其擁有實際對專利的知識並且相信擁有基本宣告必需按照W3C專利政策第六章規定揭露其資訊。

本文件由2020年9月12日W3C進程文件所管控。

## 目錄

1. 導論
2. 術語
3. 適用性
4. 建構程序
4.1 主要進入頁面（Primary Entry Page）
4.2 目錄
5. 宣告
5.1 導論
5.2 需求
5.3 宣告脈絡
5.4 出版品適用性
5.5 出版品類型
5.6 特性
5.6.1 創作者
5.6.2 長度
5.7 預設閱讀順序
5.8 資源清單
5.9 有聲書預覽
5.10 包裝
5.11 無障礙輔助性
6. 處理宣告
7. 使用者代理處理機讀目錄
8. 安全與隱私考量
9. 使用者代理對有聲書之行為
9.1 開啟及導覽有聲書的內容
9.2 有聲書的播放性
9.3 有聲書包裝以及離線
9.4 有聲書無障礙輔助性
10. 變更紀錄
A. 宣告範例
A.1 簡單的有聲書
A.2 有補充內容的有聲書
B. 目錄範例
B.1 有目錄的主要進入頁面
B.2 簡單的目錄
B.3 有媒體斷片的目錄
C. 謝詞
D. 參考資料
D.1 規範性文件
D.2 參考性文件

<hr />

## 1. 導論

本章節為非規範性。

有聲書是聲音資源的集合，其按照閱讀順序、詮釋資料以及資源集合為一組，全都包含在一份宣告之中。本有聲書可以在開放網頁平台上使用，或者作為包裝的實體存在。

本規格目的為對有聲書在網頁以及在企業間的遞送模型進行標準化。其應該促進於不同的為了供消費有聲書的使用者代理架構間通用。主要的目標是協助目前少受到標準化助力的出版界能夠更為明確，無論是在開放網頁平台或者新的使用者代理上開啟有聲書。本規格不描繪何種檔案類別或者格式應該受到內容創作者所使用，僅提供宣告格式供遞送使用。

本規格不定義使用者代理如何去處理有聲書。關於使用者代理該提供何種努力以提供對使用者閱讀經驗的強化細節，則定義在[pwp-ucr]中。

## 2. 術語

特別供出版界使用具有特殊意涵的術語在本文件中為首字大寫（中文版則加上括號，如「閱讀系統」）。這些術語及其定義的完整清單則提供在[pub-manifest]中。

每一章節術語僅在第一次出現時，連結到其定義。

此外，以下術語定義供本規格使用：

**補充內容 Supplemental Content**
    補充內容為任何與有聲書內容相關的內容，但對於該出版品的完整體驗而言並非必要。補充內容的範例包含相片、圖表，或者與在該有聲書中提及與主題相關的資料。

## 3. 適用性

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

關鍵字：**可以（MAY）、必需（MUST）、不得（MUST NOT）、推薦（RECOMMENDED）、需要（REQUIRED）、應該（SHOULD）**應該以BCP 14 [RFC2119] [RFC8174]之記述解釋，同時也僅於在出現時以全大寫（中文為粗體）顯示。

## 4. 建構程序

### 4.1 主要進入頁面（Primary Entry Page）

**主要進入頁面（Primary Entry Page）**為一份HTML資源，其表示有聲書期盼的開始資源，以及在其宣告中提供被發現性。一般用於介紹該有聲書並且提供對內容的存取。

主要進入頁面**必需**包含對宣告或者嵌入宣告[pub-manifest]的連結。其也**應該**包含目錄。

有聲書**必需**包含一份主要進入頁面，除非在包裝允許替代的宣告發現性。當存在時，該頁面**必需**包含在資源清單中。

### 4.2 目錄

目錄提供了一份階層清單的連結，可供反應有聲書及其任何可能包含補充內容之主要章節的結構大綱。

目錄透過其資源之一中的[HTML]元素（一般為nav元素）表述。該元素**必需**透過其role屬性[html]值"*doc-toc*" [dpub-aria-1.0]作為識別。

當目錄位於主要進入頁面時，目錄**必需**為該文件的第一個元素—在文件樹狀順序[don]中—及其role值。此外，宣告**應該**識別出包含該結構的資源。

當有聲書包含額外資源（例如補充內容）時：

- **應該**包含目錄；

- 目錄**應該**包含對任何資源的連結；以及

- 所有連結**應該**參照到出版品資源[pub-manifest]。
 

> ##### 注意事項
> 
> 當包含補充內容時，請注意使用者可能無法存取到該內容，除非透過目錄連結。強烈建議提供對所有的內容的連結就算不在預設閱讀順序中。

> ##### 注意事項
> 
> 若要了解更多供目錄結構與格式的指南，請參考出版品宣告 - 機讀目錄 [pub-manifest]。

## 5. 宣告

### 5.1 導論

本章節為非規範性。

有聲書宣告由一組特性所定義，其解釋了使用者代理所需要用於處理以及呈現有聲書的基本資訊。這些特性在出版品宣告[pub-manifest]中進行分類。這些特性於本章節中為來自出版品宣告中的延伸。

> ##### 注意事項
> 
> 有聲書宣告由特別「型態」的[json-ld11]所定義。其型態也非正式地透過一個JSON綱要[json-schema]所定義，其表達了定義於本規格中的限制。該綱要維護於https://www.w3.org/ns/pub-schema/audiobooks/。

### 5.2 需求

有聲書特性與資源關係的表述需求如以下定義：


> ##### 注意事項
> 
> 特性清單使用於[schema.org] 與 [pub-manifest]解釋的特性正式名稱。也包含了在括號中的描述性標籤，當這些特性不明確時用以說明。

**需要：**

- *conformsTo*
- *@context*
- *readingOrder*
- *name* (出版品標題)

**推薦：**

- *abridged*
- *accessibilityFeature*
- *accessibilityHazard*
- *accessibilitySummary*
- *accessMode*
- *accessModeSufficient*
- *author*
- *cover*
- *duration*
- *dateModified*
- *datePublished*
- *id* (標準識別碼)
- *inLanguage* (出版品語言)
- *readBy*
- *readingProgression*
- *resources*
- *type*
- *url* (位址)

> ##### 注意事項
> 
> 有些特性為潛性需求，他們可能在沒有明確被寫出時可由替代資訊所取得。請參考內在表述資料模型[pub-manifest]以獲得更多資訊（有聲書呈現在*type*術語上僅有預設值不同）。

### 5.3 宣告脈絡

有聲書宣告必須由設定JSON-LD脈絡 [json-ld]開始。其脈絡由以下主要元件所構成：

- [schema.org] 脈絡: *https://schema.org*
- 出版品脈絡: *https://www.w3.org/ns/pub-context*

> ###### 範例 1：脈絡宣告
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     …
> }

為了在宣告詮釋資料中支援全球語言與書寫方向，也可以在脈絡中加入語言與方向宣告[pub-manifest]：

> ###### 範例 2：宣告法文作為宣告的預設語言
> 
> {
>     "@context" : [
>         "https://schema.org",
>         "https://www.w3.org/ns/pub-context",
>         {"language":"fr"}
>     ]
>     …
> }

### 5.4 出版品適用性

在*conformsTo*術語[pub-manifest]中表述適用性的URL**必需**為"*https://www.w3.org/TR/audiobooks/*"。

> ###### 範例 3：設定出版品適用於有聲書
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/"
>     …
> }

### 5.5 出版品類型

**出版品類型**由*type*術語[pub-manifest]所定義。

> ###### 範例 4：設定出版品的類型為有聲書
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "type"     : "Audiobook"
> 		…
> }

如果未定義*type*，則預設值推測為A*udiobook*[schema.org]。

### 5.6 特性

#### 5.6.1 創作者

**創作者**為對製作該有聲書的個人或負責的單位。有聲書子規格可使用定義在[pub-manifest]的創作者完整清單。

創作者清單包含兩個推薦的有聲書創作者：

- author
- readBy

> ###### 範例 5：書籍作者
> 
> {
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "@context" : ["https://schema.org","https://www.w3.org/ns/pub-context"],
>     "type" : "Audiobook",
>     …
>     "url" : "https://publisher.example.org/janeeyre",
>     "author" : {
>         "type" : "Person",
>         "name" : "Charlotte Bronte"
>     }
> }

> ###### 範例 6：有聲書的作者與朗讀者
> 
> {
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/";
>     "@context": ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     …
>     "url"	: "https://publisher.example.org/janeeyre",
>     "author" : {
>         "type": "Person",
>         "name": "Charlotte Bronte"
>     }
>     "readBy" : {
>         "type": "Person",
>         "name": "Ivan Herman",
>         "id"	: "https://www.w3.org/People/Ivan/"
>     }
> }

#### 5.6.2 長度

**長度**是有聲書中聲音資源的時長。duration特性完整定義於出版品宣告[pub-manifest]。

長度**應該**要作為宣告的一部分表述整個有聲書的長度，並且**應該**在預設閱讀順序中以項目等級呈現。

當內容創作者同時指定整本有聲書的長度以及在預設閱讀順序中項目等級長度時，資源等級長度**應該**與在閱讀順序中所有長度的和相等。


> ###### 範例 7：以秒表示有聲書的長度
> 
> {
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "@context" : ["https://schema.org","https://www.w3.org/ns/pub-context"],
>     …
>     "url" : "https://publisher.example.org/janeeyre",
>     "author" : {
>          "type"  : "Person",
>          "name"  : "Charlotte Bronte"
>     },
>     "duration" : "PT12345.235S"
> }

### 5.7 預設閱讀順序

**預設閱讀順序**[pub-manifest]為有聲書中所有聲音資源的指定進行順序。

預設閱讀順序**必需**包含至少一個聲音資源，其**可以**透過*type*指定為*LinkedResource* [pub-manifest]。預設閱讀順序**不得**包含非聲音的資源。

聲音資源整體可透過一個URL[url]所參照，或者對於內容其多數章節在單一檔案中，可以使用媒體斷片（Media Fragments）[media-frags]來指定精確的開始與結束點。

> ##### 注意事項
> 
> 需要特別注意的是一個資源不能在閱讀順序中被參照多於一次。在單一聲音檔案包含一本書的複數章節的內容時，目錄可以用於指定在大型聲音檔案中各章節的開始與結束點，如同本範例所展示。

> ##### 注意事項
> 
> 註解也可以使用媒體斷片來指定資源中註解的位置，其也相容於網頁註解（Web Annotations）模型。這方法將只能應用在沒有被包裝的有聲書宣告。

> ###### 範例 8：單一資源的有聲書閱讀順序
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url" : "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "readingOrder" : [{
>         "type" : "LinkedResource",
>         "url" : "audio/janeeyre.mp3",
>         "encodingFormat" : "audio/mp3",
>         "name" : "Jane Eyre",
>         "duration" : "PT124503.123S"
>     }]
> }

> ###### 範例 9：多重資源使用媒體斷片的有聲書閱讀順序
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url" : "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "readingOrder" : [{
>         "type": "LinkedResource",
>         "url" : "audio/part001.wav#t=0,457.931",
>         "encodingFormat" : "audio/vnd-wav",
>         "name" : "Chapter 1",
>         "duration" : "PT457.931S"
>     }, {
>         "type" : "LinkedResource",
>         "url" : "audio/part002.wav#t=12.741",
>         "encodingFormat" : "audio/vnd-wav",
>         "name" : "Chapter 2",
>         "duration" : "PT234.245S"
>     }]
> }

### 5.8 資源清單

**資源清單**列舉了所有用於處理與呈現有聲書，但未列於閱讀順序的所有附加資源。透過*resources*特性來表示。

如果有聲書包含補充內容，其**必需**要在資源清單中參照。

> ###### 範例 10：有補充內容的有聲書
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url" : "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "resources" : [
>         "cover.jpg",
>         "portrait_CB.jpg",
>         "supplement.pdf"
>     ]
> }

### 5.9 有聲書預覽

預覽為讓使用者在購買或者下載完整有聲書之前，能夠提供體驗內容的常見方式。

預覽透過*preview*連結關係來指定，如[pub-manifest]中所定義。

預覽**可以**位於外部，或者包含在有聲書的資源中。

> ###### 範例 11：有著外部預覽的有聲書
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url"	: "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "resources" : [{
>         "type" : "LinkedResource",
>         "url" : "https://publisher.example.org/jane-eyre-preview.wav",
>         "encodingFormat" : "audio/wav",
>         "rel" : "preview"
>     }]
> }

> ###### 範例 12：有著內部預覽的有聲書
> 
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url"	: "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "resources" : [{
>         "type" : "LinkedResource",
>         "url"	: "preview.wav",
>         "encodingFormat" : "audio/wav",
>         "rel"	: "preview"
>     }]
> }

### 5.10 包裝

本章節為非規範性。

有聲書可以使用解釋於輕量包裝格式（Lightweight Packaging Format） [lpf] 注意事項中的方式來進行包裝。

### 5.11 無障礙輔助性

本章節為非規範性。

有聲書的歷史根於無障礙輔助的世界。不管是純聲音的出版品或者有著文字與聲音同步播放的出版品長久以來都用於協助有著輔助閱讀需求及偏好的使用者。

在出版品中提供無障礙輔助同步媒體的做法現在可以透過出版社群小組的同步多媒體達到。請參考該小組的成果以獲得更多製作那種內容以及將其導入有聲書的資訊。

作為替代，內容創作者可以在資源中以HTML[html]資源提供相同的文字內容。

> ###### 範例 13：有著替代文字的有聲書
>
> {
>     "@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "url" : "https://publisher.example.org/janeeyre",
>     "name" : "Jane Eyre",
>     "readingOrder" : {
>         "type" : "LinkedResource",
>         "url" : "audio/part001.wav#t=0",
>         "encodingFormat" : "audio/vnd-wav",
>         "name" : "Chapter 1",
>         "duration" : "PT457.931S",
>         "alternate" : {
>             "type" : "LinkedResource",
>             "url" : "text/part001-1.html",
>             "encodingFormat" : "text/html"},
>     },
>     "resources" : [{
>          "type": "LinkedResource",
>          "url": "text/part001-1.html",
>          "encodingFormat" : "text/html"
>      }…
>     ]
> }

## 6. 處理宣告

本章節依賴於Infra標準[infra]。

本規格延伸出版品宣告處理演算法[pub-manifest]如下：

**計算內部表述（Generating the Internal Representation）**
    以下延伸步驟為了有聲書宣告而新增：

1. （§5.6.2 長度）確認該出版品的長度如下：
    1. 讓*resourceDuration*持有個別資源的總長度
    2. 對每一個*resource*的*data["readingOrder"]*：
        1. 如果*resource["duration"]*未定義，驗證為錯誤。
        2. 以外，如果*resource["duration"]*，則新增*resource["duration"]*為*resourceDuration*。
    3. 如果未設定*data["duration"]*以至於值無法被比較，驗證為錯誤。 以外，如果*resourceDuration*和*data["duration"]*代表的整體長度不一致，驗證為錯誤。

> ###### 解釋
> 
> 本步驟同時檢驗在閱讀順序中指定長度的所有資源，並且加總所有這些長度以匹配該出版品的總長度。
> 
> 驗證錯誤僅會在確認每一個資源時，如果資源沒有指定長度時發出。長度的有效性[pub-manifest]已經在出版品宣告演算法中檢查過了所以沒有重複進行的必要。

**資料驗證（Data Validation）**
    以下延伸步驟為了有聲書宣告而新增：

1.（§5.7預設閱讀順序）依以下方式確認閱讀順序：
    1. 如果未設定*data["readingOrder"]*，則為嚴重錯誤。
    2. 對每一個*data["readingOrder"]中的resource*，如果*resource*不是聲音資源，驗證為錯誤，由*data["readingOrder"]*中移除資源。
    3. 如果*data["readingOrder"]*為空白清單，則為嚴重錯誤。

> ###### 解釋
> 
> 本步驟確保在閱讀順序中僅列出聲音資源，並且移除其他不是的資源。
> 
> 如果閱讀順序在檢查每個資源後沒有任何資料，則視為嚴重錯誤並且將出版品視為不合規的有聲書。

2. （§5.5出版品類別）如果*data["type"]*未設定或者為空白清單，驗證為錯誤，設定為*« "Audiobook" »*。

> ###### 解釋
> 
> 本步驟當*type*特性未指定時，設定出版品的預設類型為*audiobook*。

3. （§ 5.2需求）確認以下每一個特性都有設定。如果沒有，為每一個驗證為錯誤。
    - data["abridged"]
    - data["accessMode"]
    - data["accessModeSufficient"]
    - data["accessibilityFeature"]
    - data["accessibilityHazard"]
    - data["accessibilitySummary"]
    - data["author"]
    - data["dateModified"]
    - data["datePublished"]
    - data["id"]
    - data["inLanguage"]
    - data["name"]
    - data["readBy"]
    - data["readingProgression"]
    - data["resources"]
    - data["url"]

> ###### 解釋
> 
> 本步驟驗證所有推薦的特性是否被設定。若要了解更多關於這些的資訊，請參考§5.2需求。

4. （§5.2需求）如果在*data["readingOrder"]中沒有任何資源擁有rel*資料包含*cover*關聯，則驗證為錯誤。

> ###### 解釋
> 
> 本步驟確認閱讀順序與資源列表已確認封面有被指定（即為一個資源在其*rel*特性中有其值為*cover*）。

## 7. 使用者代理處理機讀目錄

本章節為非規範性。

本規格延伸出版品宣告之使用者代理處理演算法供機讀目錄[pub-manifest]以確定目錄元素的位置如下：

1. 如果有主要進入頁面，就執行其演算法以確認在主要進入頁面中目錄元素的位置。
2. 如果前一步沒有成功，尋找相關資源，如果有，如在[pub-manifest]中§4.8.1.3目錄所解釋的宣告，則對該資源執行相同演算法。

請見§4.2目錄以取得進一步的細節。

## 8. 安全與隱私考量

有聲書為出版品宣告[pub-manifest]的子規格，所有在該規格中對安全與隱私的考量都是用於本子規格。

本子規格認知到以下考量：

- 在閱讀順序與資源清單中的參照對象可以為遠端或者本地資源的參照。

## 9. 使用者代理對有聲書之行為

本章節為非規範性。

本章節勾勒預期的使用者代理對有聲書實裝的行為。對處理程序而言，使用者代理應該參考出版品宣告規格[pub-manifest]中的處理宣告章節，並且合乎以下說明的所有行為。

所有於本章節中說明的使用者代理行為目的為提供實作者一份指南，而非嚴格要求。本文件中的行為主要來自由工作小組所發表之使用案例與需求[pwp-ucr]注意事項。

### 9.1 開啟及導覽有聲書的內容

當使用者代理開啟有聲書時，其宣告處理程序按照出版品宣告[pub-manifest]中的規則進行，其應該由使用者代理所開啟。閱讀順序，或者，如果有目錄的話，應該要對使用者提供無障礙輔助。使用者代理應該能夠在使用者要求時提供有聲書的內容列表。如果在閱讀順序中要呈現非聲音的資源時，使用者代理可以選擇呈現給使用者或者忽略之。

使用者代理應該提供處理在閱讀順序以及資源清單中非聲音資源的手段。如果內容無法被使用者代理所顯示，則推薦使用者代理告知使用者有該內容但無法顯示。

當有主要進入頁面時，其預期應該是有聲書的進入點。如果內容製作者提供了主要進入頁面，並且使用者代理能夠顯示或者處理HTML內容，其應該為第一個呈現給使用者的東西。該處要進入頁面可以或者可以不包含目錄，如果包含的話，並使用*role="doc-toc"*時，其應該要被處理作為目錄。如果目錄為分開的文件，其應該被處理，使用者代理應該挑選無論其是否符合以上需求。如果在主要進入頁面或者其他地方都未包含目錄的話，使用者代理應該參考閱讀順序。

### 9.2 有聲書的播放性

如同使用案例與需求[pwp-ucr]注意事項所勾勒，有聲書必需在使用者代理中能被導覽。這意味著使用者代理必需提供使用者方法來有聲書中透過線性或者非線性的方式來在閱讀順序或者透過存取目錄間無縫移動。使用者代理應該也允許使用者在短時間間隔內切換單獨聲音檔案。

對有聲書來說，使用者代理應該提供播放器介面[pwp-ucr]其允許使用者以導覽、播放或者暫停該有聲書。該介面可以以任何方式呈現給使用者（例如，物理按鍵、視覺介面、鍵盤輸入或者聲音指令），但應該在聆聽體驗的任何點都提供無障礙輔助。

### 9.3 有聲書包裝以及離線

使用案例與需求[pwp-ucr]注意事項推薦內容應該能離線取得，以及任何包裝格式不應造成出版品的重複出現。這意味著儘管內容被複製很多次透過多重使用者代理給多數使用者，其核心宣告與其識別碼都不該被改變。

本規格推薦輕量包裝格式[lpf]用於包裝有聲書內容，但這不是需求。有聲書使用者代理應該能夠接受LPF檔案供播放，以及應該按照本文件中的需求與推薦顯示內容。

如果使用者代理直接由其服務提供內容（例如，作為內容的零售商或者內容的儲存處），推薦該提供離線或者下載內容給使用者的手段。可以為他們所挑選的任何格式，但有聲書需要為完整並且合規，及其列於宣告中的內容應該以整體的方式提供。儘管使用者代理不支援對某一項資源的顯示（例如一個影像檔或者資料表格），其依然應該能讓使用者下載。

本規格不對內容製作者提供手段來保護或者為其內容加上浮水印，主要在現在的市場上已經有了這些方法。使用者代理與想要保護或者限制其內容配送的內容製作者合作時，可以挑選其一來與他們的需求做到最佳搭配。

### 9.4 有聲書無障礙輔助性

本規格推薦並且提供手段給內容製作者來創建具完整無障礙輔助性的有聲書。使用者代理應該使用這些資訊，在無障礙輔助性章節中，需要實作無障礙輔助的有聲書介面。並且推薦使用者代理提供無障礙輔助播放介面，也推薦內容製作者提供替代內容來讓內容能夠顯示。

## 10. 變更紀錄

從初次發布工作草稿以來的主要變更：

- 2020年9月14日：新增關於目錄結構以及格式資訊的非規範資訊注意事項，其可從出版品宣告規格中取得。請見issue 97。
- 2020年9月12日：移除宣告處理步驟，其會在找不到目錄時給予警告，主要是需求依賴於補充資源的存在而無法被穩定測試。請見issue 93。
- 2020年9月8日：澄清主要進入頁面僅會在包裝無法提供替代手段時為必需。請見issue 61。
- 2020年8月26日：移除同步字幕範例，並且更新同步多媒體出版品社群小組的成果參考以反映該成果的早期特性。請見issue 87。
- 2020年7月27日：更新參考的綱要URL為W3C網址。請見出版品宣告之issue 226。
- 2020年7月2日：新增注意事項關於宣告的型態定義於JSON綱要到宣告導論。請見issue 71。
- 2020年2月12日：演算法步驟以確認並且比較資源長度與整體有聲書長度移動，以避免重複有效性確認。演算法步驟用於警示主要進入頁面沒有列於獨特資源被移除，因為在出版品宣告演算法中沒有檢驗。請見issue 71。
- 2020年2月12日：對在閱讀順序中使用斷片釐清也包含了結束點。一些範本也修正了。請見issue 69。
- 2020年2月7日：宣告需求章節移出特性章節，因為其也包含了資源關聯。請見issue 70。
- 2020年1月3日：新增（非規範）章節§7使用者代理處理機讀目錄定義，延伸目錄處理演算法。請見issue 63。
- 2020年1月3日：於§6處理宣告中加入額外步驟透過PEP的URL到宣告中獨特資源的集合。請見issue 7以取得測試套件。

請參照Github追蹤系統以獲得所提及issue的完整清單。

## A. 宣告範例

本章節為非規範性。

### A.1 簡單的有聲書

有聲書的宣告。也有本宣告的標準版本。

> ###### 範例 14
> 
> {
>   "@context": ["https://schema.org", "https://www.w3.org/ns/pub-context"],
>   "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>   "type": "Audiobook",
>   "id": "https://librivox.org/flatland-a-romance-of-many-dimensions-by-edwin-abbott-abbott/",
>   "url": "https://w3c.github.io/wpub/experiments/audiobook/",
>   "name": "Flatland: A Romance of Many Dimensions",
>   "author": "Edwin Abbott Abbott",
>   "readBy": "Ruth Golding",
>   "publisher": "Librivox",
>   "inLanguage": "en",
>   "dateModified": "2018-06-14T19:32:18Z",
>   "datePublished": "2008-10-12",
>   "duration": "PT15153S",
>   "license": "https://creativecommons.org/publicdomain/zero/1.0/",
> 
>   "resources": [
>     {
>       "rel": "cover",
>       "url": "http://ia800704.us.archive.org/9/items/LibrivoxCdCoverArt12/Flatland_1109.jpg",
      "encodingFormat": "image/jpeg"
>     },{
>       "rel": "contents",
>       "url": "toc.html",
>       "encodingFormat": "text/html"
>     }
>   ],
> 
>   "readingOrder": [
>     {
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_1_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1371,
>       "name": "Part 1, Sections 1 - 3"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_2_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1669,
>       "name": "Part 1, Sections 4 - 5"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_3_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1506,
>       "name": "Part 1, Sections 6 - 7"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_4_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1669,
>       "name": "Part 1, Sections 8 - 10"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_5_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1506,
>       "name": "Part 1, Sections 11 - 12"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_6_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1798,
>       "name": "Part 2, Sections 13 - 14"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_7_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1225,
>       "name": "Part 2, Sections 15 - 17"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_8_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1371,
>       "name": "Part 2, Sections 18 - 20"
>     },{
>       "url": "http://www.archive.org/download/flatland_rg_librivox/flatland_9_abbott.mp3",
>       "encodingFormat": "audio/mpeg",
>       "duration": 1659,
>       "name": "Part 2, Sections 21 - 22"
>     }
>   ]
> }

### A.2 有補充內容的有聲書

有補充內容有聲書的宣告。

> ###### 範例 15
> {
>     "@context" : ["https://schema.org", "https://www.w3/org/ns/pub-context"],
>     "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>     "id" : "https://publisher.example.com/janeeyre",
>     "url" : "https://publisher.example.com/janeeyre",
>     "name" : "Jane Eyre",
>     "author" : "Charlotte Bronte",
>     "readBy" : "Jane Doe",
>     "duration" : "PT123456.789S",
>     "abridged" : false,
>     "inLanguage" : "en",
>     "dateModified" : "2019-03-29T15:59:00Z",
>     "datePublished" : "2019-03-29",
> 
>     "readingOrder": [
>         {"url": "audio/chapter001.aac", "encodingFormat": "audio/aac", "name": "Chapter 1", "duration": "PT1234.567S"},
>         {"url": "audio/chapter002.aac", "encodingFormat": "audio/aac", "name": "Chapter 2", "duration": "PT890.123S"},
>         {"url": "audio/chapter003.aac", "encodingFormat": "audio/aac", "name": "Chapter 3", "duration": "PT456.789S"},
>         {"url": "audio/chapter004.aac", "encodingFormat": "audio/aac", "name": "Chapter 4", "duration": "PT987.654S"},
>         {"url": "audio/chapter005.aac", "encodingFormat": "audio/aac", "name": "Chapter 5", "duration": "PT321.987S"}
>     ],
> 
>      "resources": [
>         {"rel": "cover", "url": "images/cover.jpg", "encordingFormat": "image/jpeg"},
>         {"rel": "contents", "url": "toc.html", "encodingFormat": "text/html"},
>         {"url": "haworth_house.pdf", "encodingFormat": "application/pdf"}
>     ]
> }

## B. 目錄範例

本章節為非規範性。

### B.1 有目錄的主要進入頁面

有聲書之主要進入頁面有著簡單的目錄。

> ###### 範例 16
> 
>     <head>
>         …
>         <script type="application/ld+json">
>     {
>         "@context" : ["https://schema.org","https://www.w3.org/ns/pub-context"],
>         "conformsTo" : "https://www.w3.org/TR/audiobooks/",
>         …
>         "url" : "https://publisher.example.org/janeeyre",
>         …
>     }
>     </script>
>     …
> </head>
> <body>
>     …
>     <section role="doc-toc">
>         <ol>
>             <li><a href="audio/chapter001.wav">Chapter 1. There was no possibility of taking a walk that day...</a></li>
>             <li><a href="audio/chapter002.wav">Chapter 2. I resisted all the way:...</a></li>
>             <li><a href="audio/chapter003.wav">Chapter 3. The next thing I remember is,...</a></li>
>             …
>          </ol>
>     </section>
>     …
> </body>

### B.2 簡單的目錄

簡單有聲書的目錄

> ###### 範例 17
> 
> <nav role="doc-toc">
>     <h2>JANE EYRE</h2>
> 
>     <ol>
>         <li><a href="audio/chapter001.mp3">Chapter 1. There was no possibility of taking a walk that day...</a></li>
>         <li><a href="audio/chapter002.mp3">Chapter 2. I resisted all the way:...</a></li>
>         <li><a href="audio/chapter003.mp3">Chapter 3. The next thing I remember is,...</a></li>
>         …
>     </ol>
> </nav>

### B.3 有媒體斷片的目錄

目錄使用媒體斷片在單一音軌中參照到位置。

> ###### 範例 18
> 
> <nav role="doc-toc">
>     <h2>JANE EYRE</h2>
> 
>     <ol>
>         <li><a href="https://example.publisher.org/janeeyre/part001.mp3#t=0,456.788">Chapter 1</a></li>
>         <li><a href="https://example.publisher.org/janeeyre/part001.mp3#t=456.789,1234.566">Chapter 2</a></li>
>         <li><a href="https://example.publisher.org/janeeyre/part001.mp3#t=1234.567">Chapter 3</a></li>
>     </ol>
> </nav>

## C. 謝詞

本章節為非規範性。

編輯對出版工作小組的成員對本規格的貢獻致謝：

Greg Albers (J. Paul Getty Trust) Franco Alvarado (Macmillan Learning) Boris Anthony (The Rebus Foundation) Luc Audrain (Hachette Livre) Baldur Bjarnason (The Rebus Foundation) Laura Brady (W3C Invited Expert) Steve Breault (Scenarex Inc.) Don Brutzman (Web3D Consortium) Kaylin Bugbee (Earth Science Data Systems Program) Yu-Wei Chang (Taiwan Digital Publishing Forum) Fred Chasen (W3C Invited Expert) Timothy Cole (University of Illinois at Urbana-Champaign) Simon Collinson (Rakuten, Inc.) Rachel Comerford (Macmillan Learning) Garth Conboy (Google, Inc., chair) Juan Corona (Evident Point Software) Christopher Cosner (Stanford University) Dave Cramer (Hachette Livre) Greg Davis (Pearson plc) Romain Deltour (DAISY Consortium) Marisa DeMeglio (DAISY Consortium) Vagner Diniz (NIC.br - Brazilian Network Information Center) Kenneth Dougherty (Pearson plc) Brady Duga (Google, Inc.) Ben Dugas (Rakuten, Inc.) Roger Espinosa (University of Michigan) Reinaldo Ferraz (NIC.br - Brazilian Network Information Center) Teenya Franklin (Pearson plc) Jun Gamo (Voyager Japan, Inc.) Matt Garrish (DAISY Consortium) Michael Goodman (Wiley) Markku Hakkinen (Educational Testing Service) Katie Haritos-Shea (Knowbility) Ivan Herman (W3C Staff) Geoff Jukes (Blackstone Audio, Inc.) Deborah Kaplan (W3C Invited Expert) Bill Kasdorf (Book Industry Study Group) George Kerscher (DAISY Consortium) Yuri Khramov (Evident Point Software) Masakazu Kitahara (Voyager Japan, Inc.) Toshiaki Koike (Voyager Japan, Inc.) Charles LaPierre (Benetech) Mustapha Lazrek (Microsoft Corporation) Laurent Le Meur (EDRLab) Vladimir Levantovsky (Monotype) Mia Lipner (Pearson plc) Phil Madans (Hachette Livre) Christopher Maden (University of Illinois at Urbana-Champaign) Dmitry Markushevich (Evident Point Software) Keith McFarland (Blackstone Audio, Inc.) Jonathan McGlone (University of Michigan) Hugh McGuire (The Rebus Foundation) Nellie McKesson (W3C Invited Expert) Selma Morais (NIC.br - Brazilian Network Information Center) Jasmine Mulliken (Stanford University) Cristina Mussinelli (Fondazione LIA) Christos Nikolakakos (Wiley) Gregorio Pellegrino (Fondazione LIA) Fernando Pinto da Silva (EDRLab) Nicholas Polys (Web3D Consortium) Chris Powell (University of Michigan) Jeff Printy (Macmillan Learning) Ryan Pugatch (Hachette Livre) Joshua Pyle (Wiley) Florian Rivoal (W3C Invited Expert) Leonard Rosenthol (Adobe) Robert Sanderson (J. Paul Getty Trust) Jodi Schneider (University of Illinois at Urbana-Champaign) Ben Schroeter (Pearson plc) Tzviya Siegman (Wiley, chair) Avneesh Singh (DAISY Consortium) Adam Sisco (Earth Science Data Systems Program) David Stroup (Pearson plc) Mateus Teixeira (W. W. Norton & Company) Jonathan Thurston (Pearson plc) Yukio Tomikura (Kodansha, Publishers, Ltd.) Ben Walters (Microsoft Corporation) Daniel Weck (EDRLab, DAISY Consortium) John Weise (University of Michigan) Jason White (Educational Testing Service) Richard Wright (EDRLab) Jeff Xu (Rakuten, Inc.) Evan Yamanishi (W. W. Norton & Company) Maurice York (University of Michigan) Junichi Yoshii (Kodansha, Publishers, Ltd.) Benjamin Young (Wiley) Mohamed ZERGAOUI (INNOVIMAX)

工作小組也想要對數位出版興趣小組的成員對本規格鋪路的努力致謝。

## D. 參考資料

### D.1 規範性文件

**[dom]**
    [DOM Standard](https://dom.spec.whatwg.org/). Anne van Kesteren. WHATWG. Living Standard. URL: https://dom.spec.whatwg.org/

**[dpub-aria-1.0]**
    [Digital Publishing WAI-ARIA Module 1.0](https://www.w3.org/TR/dpub-aria-1.0/). Matt Garrish; Tzviya Siegman; Markus Gylling; Shane McCarron. W3C. 14 December 2017. W3C Recommendation. URL: https://www.w3.org/TR/dpub-aria-1.0/

**[html]**
    [HTML Standard](https://html.spec.whatwg.org/multipage/). Anne van Kesteren; Domenic Denicola; Ian Hickson; Philip Jägenstedt; Simon Pieters. WHATWG. Living Standard. URL: https://html.spec.whatwg.org/multipage/

**[infra]**
    [Infra Standard](https://infra.spec.whatwg.org/). Anne van Kesteren; Domenic Denicola. WHATWG. Living Standard. URL: https://infra.spec.whatwg.org/

**[json-ld]**
    [JSON-LD 1.0](https://www.w3.org/TR/json-ld/). Manu Sporny; Gregg Kellogg; Markus Lanthaler. W3C. 16 January 2014. W3C Recommendation. URL: https://www.w3.org/TR/json-ld/

**[media-frags]**
    [Media Fragments URI 1.0 (basic)](https://www.w3.org/TR/media-frags/). Raphaël Troncy; Erik Mannens; Silvia Pfeiffer; Davy Van Deursen. W3C. 25 September 2012. W3C Recommendation. URL: https://www.w3.org/TR/media-frags/

**[pub-manifest]**
    [Publication Manifest](https://www.w3.org/TR/pub-manifest/). Matt Garrish; Ivan Herman. W3C. 10 November 2020. W3C Recommendation. URL: https://www.w3.org/TR/pub-manifest/

**[RFC2119]**
    [Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119

**[RFC8174]**
    [Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words](https://tools.ietf.org/html/rfc8174). B. Leiba. IETF. May 2017. Best Current Practice. URL: https://tools.ietf.org/html/rfc8174

**[schema.org]**
    [Schema.org](https://schema.org/). URL: https://schema.org

**[url]**
    [URL Standard](https://url.spec.whatwg.org/). Anne van Kesteren. WHATWG. Living Standard. URL: https://url.spec.whatwg.org/

### D.2 參考性文件

**[json-ld11]**
    [JSON-LD 1.1](https://www.w3.org/TR/json-ld11/). Gregg Kellogg; Pierre-Antoine Champin; Dave Longley. W3C. 7 May 2020. W3C Proposed Recommendation. URL: https://www.w3.org/TR/json-ld11/

**[json-schema]**
    [JSON Schema: core definitions and terminology](https://tools.ietf.org/html/draft-zyp-json-schema). K. Zyp. Internet Engineering Task Force (IETF). 31 January 2013. Internet-Draft. URL: https://tools.ietf.org/html/draft-zyp-json-schema

**[lpf]**
    [Lightweight Packaging Format (LPF)](https://w3c.github.io/lpf/). Laurent Le Meur. 2018-08-07. URL: https://w3c.github.io/lpf/

**[pwp-ucr]**
    [Web Publications Use Cases and Requirements](https://www.w3.org/TR/pwp-ucr/). Franco Alvarado; Joshua Pyle. W3C. 13 August 2019. W3C Note. URL: https://www.w3.org/TR/pwp-ucr/