# EPUB 無障礙輔助性 1.0
W3C會員提案文件 25 January 2017

**本版本：**
    https://www.w3.org/Submission/2017/SUBM-epub-a11y-20170125/
**最新發佈版本：**
    https://www.w3.org/Submission/epub-a11y/
**編輯**：
    Matt Garrish, Invited Expert
    George Kerscher, DAISY Consortium
    Charles LaPierre, Benetech
    Avneesh Singh, DAISY Consortium
**作者**
    Romain Deltour, DAISY Consortium
    Markus Gylling, International Digital Publishing Forum (IDPF)
    Bernhard Heinser, Access for All
    Jean Kaplansky, Invited Expert
    Madeleine Rothberg, Invited Expert
    Tzviya Siegman, John Wiley & Sons
    Jason White, Invited Expert

Copyright © 2017. 本文件基於W3C文件授權提供。請見W3C智慧財產權注意事項以及法律宣告已取得額外資訊。

<hr />

## 概要

EPUB無障礙輔助性定義了供EPUB出版品使用的發現性與內容無障礙輔助性需求。

## 本文件狀態

本章解釋了本文件在其發布時的狀態。其他文件可以取代本文件。當下W3C出版品清單可於W3C技術報告索引下進行查找https://www.w3.org/TR/。

本文件的發佈，W3C承認提案的會員提出了正式提案文件給W3C進行討論。雖然文件由W3C所發布，但並不指出W3C對其內容背書，也不代表W3C曾經、會，或可能分配任何資源到文件所提及的議題。本文件並非具備章程W3C小組的產出物，但其發表後可能進入W3C審查程序。W3C成員意見書會對應此會員提交提案。發表受到認可的W3C會員提案於W3C網頁為W3C會員的一項權利。請參考3.3節W3C專利政策以了解會員提案所相關的需求。也請參考受到認可的W3C會員提案完整清單。

## 目錄

1.   概論
1.1   目的與目標
1.2   有效技巧
1.3   適用於舊版規格
1.4   術語
1.5   適用性宣言
2.   適用性
2.1   具發現性的EPUB出版品
2.2   具無障礙輔助性的EPUB出版品
2.3   最佳化的EPUB出版品
2.4   配送
3.   發現性
3.1   導論
3.2   包裝詮釋資料
3.3   連結的詮釋資料紀錄
4.   無障礙出版品
4.1   導論
4.2   與WCAG之關係
4.3   WCAG適用性
4.3.1   WCAG適用性需求
4.3.2   評量WCAG適用性
4.3.2.1   頁面與出版品
4.3.2.2   套用適用性規範
4.4   EPUB需求
4.4.1   頁面導覽
4.4.1.1   目標
4.4.1.2   瞭解該項目標
4.4.1.3   符合該項目標
4.4.1.4   與WCAG之關係
4.4.2   媒體層疊播放
4.4.2.1   目標
4.4.2.2   瞭解該項目標
4.4.2.3   符合該項目標
4.4.2.4   與WCAG之關係
4.5   適用性報告
5.   出版品最佳化
6.   配送
A.   製作與使用
A.1   導論
A.2   製作工具適用性
A.3   配送系統適用性
A.4   閱讀系統適用性
B.   謝詞與貢獻者
C.   參考資料
C.1 規範性文件
C.2 參考性文件

<hr />

## 1.   概論

### 1.1   目的與目標

本章節為非規範性。

本規格，EPUB無障礙輔助性，表達兩項EPUB生態體系的關鍵需求：

1. 對具無障礙輔助性的EPUB出版品進行評量與認證；
2. 挖掘EPUB出版品的無障礙輔助特性。

儘管並非一直都可能在製作EPUB出版品時提供高度的無障礙輔助性，本規格設定正式的需求以驗證內容為具備無障礙輔助性。這些需求提供作者明確的一組指南以評量他們的內容，並且可用於對品質進行驗證。

包括具無障礙輔助性的詮釋資料，一方面促進提供關於一本EPUB出版品的合用性資訊作為判斷。消費者可以用於檢視內容品質，並且判斷一本EPUB出版品是否合乎其需求，無論其是否符合受到認證為具備無障礙輔助性的標準。

本規格定義了三個EPUB出版品的適用性範疇：

- 發現性（Discoverable） — 一本EPUB出版品符合本規格中對具發現性詮釋資料之需求，卻未符合無障礙輔助性需求。適用性定義於具發現性的EPUB出版品。
- 無障礙輔助性（Accessible） — 一本EPUB出版品符合全部發現性、[WCAG 2.0]以及EPUB無障礙輔助性需求。適用性定義於具無障礙輔助性的EPUB出版品。
- 最佳化（Optimized） — 一本EPUB出版品符合發現性需求以供最佳化使用。適用性定義於最佳化的EPUB出版品。

本規格不指定單一版本的EPUB。其設計以應用於EPUB出版品適用於任何版本或者子集，也包含該標準的未來版本。

理想上，這些指南可以被應用於評量任何基於開放網頁技術的數位出版品，儘管確立這些應用並非本規格的目標。

> ##### 注意事項
> 
> 為獲得制定本規格的決策背景資訊，請參考非規範性的[Accessibility FAQ]。

### 1.2   有效技巧

本規格採取概要式的手段提供EPUB出版品的無障礙輔助性需求，就如[WCAG 2.0]如何分割其無障礙輔助性指南及如何達成之技巧一般。此手段能讓指南就算隨著格式進化也能保持穩定。

為便於應用這項手段，伴隨文件[EPUB Accessibility Techniques]概要地提出了適用性技巧。這些技巧解釋如何讓不同版本的EPUB符合本規格中的需求。

### 1.3   適用於舊版規格

本章節為非規範性。

本規格設計於適用任何EPUB出版品，儘管其內容適用於舊版規格，而並未在本規格中受到參照（即為，早於[EPUB 3.1]的規格）。

這類EPUB出版品的作者在製作內容時，建議符合本規格之無障礙輔助性需求，儘管並非正式要求。

### 1.4   術語

**輔助科技**
    本規格採用[WCAG 2.0]對輔助科技之定義。
    請注意輔助科技並非一直都是外於閱讀系統的應用程式。閱讀系統經常需要整合獨立輔助科技的功能，例如文字轉換語音播放。

**作者**
    對EPUB出版品製作負責的人或組織。作者不必要是內容的創作者。

**具發現性的EPUB出版品**
    一本EPUB出版品在其包裝文件詮釋資料中包含對其無障礙輔助品質的敘述，如在發現性中所定義。
    包含此項詮釋資料允許使用者能夠做充分資訊以判斷EPUB出版品是否合用，儘管在某些案例該內容並不符合本規格的無障礙輔助性需求。

**配送系統**
    提供使用者存取並取得EPUB出版品的系統，例如線上書店或者公共圖書館。

**EPUB製作工具**
    本規格採用[ATAG 2.0]對製作工具之定義。EPUB製作工具的區別僅於其可用於創作或者修改EPUB出版品。

**EPUB內容文件**
    一份符合EPUB內容文件定義的文件。

**EPUB出版品**
    一或多個內容解釋的集合已呈現單一智慧或者藝術作品。

**最佳化的EPUB出版品**
    一本EPUB出版品其內容為了提供使用者在某些特定需求（例如難讀症）上的無障礙輔助性而強化，或者提供所偏好的閱讀形式（例如聲音、觸覺），但並不達到[WCAG 2.0]更廣泛的無障礙輔助性需求。請見出版品最佳化。

**包裝文件**
    包裝文件敘述的EPUB出版品中的一份內容解釋。其包含詮釋資訊、提供內容宣告以及定義了預設閱讀順序。

**閱讀系統**
    用於處理EPUB出版品供呈現給使用者的系統。

**內容解釋**
    一份用於呈現一本EPUB出版品其中一種顯示方式的邏輯文件實體。

> ##### 注意事項
> 
> 有些術語在該版本的EPUB中有更精準的意義。請參照合適的規格以獲得更多資訊。

### 1.5   適用性宣言

本文件中關鍵字：*必需（MUST）、不得（MUST NOT）、需要（REQUIRED）、該（SHALL）、不該（SHALL NOT）、應該（SHOULD）、不應（SHOULD NOT）、推薦（RECOMMENDED）、可以（MAY）、選擇性（OPTIONAL）**應該以[RFC2119]之記述解釋。

本規格之所有章節與附錄皆為規範性，除了以「本章節為非規範性。」識別為非規範性狀態的章節。非規範性狀態套用到該章節以及附錄之所有包含的子級內容以及子章節。

除了標註為非規範性的章節，本規格中所有製作指針、圖表、範本與注意事項都為非規範性。其餘本規格中的內容皆為規範性。

本規格中所有範例皆為非規範性。

## 2.   適用性

### 2.1   可被發現的EPUB出版品

可被發現的EPUB出版品**必需**符合以下需求：

- 其**必需**包含定義於發現性中的可被發現詮釋資料。

### 2.2   具無障礙輔助性的EPUB出版品

一份EPUB出版品**必需**符合以下需求以符合本規格中的無障礙輔助性：

- 其**必需**符合可被發現的EPUB出版品之需求。
- 其**必需**符合[WCAG 2.0]定義在WCAF適用性之需求。
- 其**必需**符合定義在EPUB需求中對EPUB出版品之需求。
- 其**必需**包含定義在適用性報告中無障礙輔助性適用性詮釋資料。

### 2.3   最佳化的EPUB出版品

最佳化的EPUB出版品**必需**符合以下需求：

- 其**必需**符合可被發現的EPUB出版品之需求。
- 其**必需**識別定義在出版品最佳化中，其所適用的標準或者指南。

### 2.4   配送

無論EPUB出版品達到任何類型或者等級的無障礙輔助性，其**必需**能被無障礙配送，如配送所定義。

## 3.   發現性Discovery

### 3.1   導論

本章節為非規範性。

不像網頁，EPUB出版品設計是為了能被透過多種管道遞送供個人使用 — 此模型已經讓EPUB成為成功的電子書以及其他類型數位出版品的格式。然而本模型在結果上，需要指定出版品輔助性的細節以伴隨其提供。

線上書店從作者和出版社取得內容，舉個例子，無法知悉每次遞送的製作品質，所以僅能從每本出版品的詮釋資料取得資訊提供給消費者。

為保障EPUB出版品的無障礙輔助品質能被任何關係人所發現，且作為主要考量。使用者需要能夠在購買、出借或者其他取得EPUB出版品時評量其可用性，就需要一個判斷方式來知悉其是否符合無障礙輔助需求。

同樣的不符合本規格需求的內容，儘管不具廣泛的無障礙輔助性，依然可能符合個別使用者的需求。但僅有在包含豐富詮釋資料的狀況下，使用者能夠判斷內容是否合乎他們的需求。

### 3.2   包裝詮釋資料

每一份合規的EPUB出版品**必需**包含以下[schema.org]無障礙輔助性詮釋資料：

- accessMode — 為了處理或者感知內容所需要的人類知覺感知系統或者認知能力（例如，textual文字、visual視覺、auditory聽覺、tactile觸覺）。

- accessibilityFeature — 提升內容整體無障礙輔助性的功能或者採用技術（例如，alternative text替代文字、extended descriptions延伸說明、captions字幕）。

- accessibilityHazard — 任何內容顯示的潛在問題（例如，flashing閃爍、motion simulation動作刺激、sound聲音）。

- accessibilitySummary — 一份人能讀取的整體無障礙輔助性摘要，其包括了對任何已知缺陷的說明（例如，缺少延伸說明、特殊的問題）。

**推薦**包含以下[schema.org]無障礙輔助性詮釋資料：

- accessModeSufficient — 一或多組存取模式充分在不明顯丟失資訊的狀況下消費內容。EPUB出版品可能有著多於一種的充分存取模式供內容消費，依據其包含的內容種類（例如，不像存取模式，其特性為無法廣泛提供無障礙輔助性的內容負責，例如在聲音內容包含文字說明）。

包含以下[schema.org]無障礙輔助性詮釋資料為**選擇性**：

- accessibilityAPI — 指示資源合乎特定無障礙輔助性API。該特性一般僅用於指示在EPUB出版品中使用的腳本遵從[WAI-ARIA 1.1]製作實踐，而作業系統無障礙輔助性的相容性則為閱讀系統之考量。

- accessibilityControl — 指示可以用於存取內容的手段（例如，鍵盤、滑鼠）

> ##### 注意事項
> 
> 請見發現性詮釋資料技巧[EPUB Accessibility Techniques]以獲得更多關於這些特性以及如何將其包含在不同版本EPUB中的資訊。
> 
> 也請見DIST-002:在配送紀錄中包含無障礙輔助性詮釋資料[EPUB Accessibility Techniques]以獲得更多關於使用其他格式包含無障礙輔助性詮釋資料的資訊。

> ##### 注意事項
> 
> 以上推薦在發表時包含了所有[schema.org]的無障礙輔助性特性。如果未來有新增特性，則鼓勵作者包含於其中，相容上則會於本規格更新時新增。

從其他用語包含無障礙輔助性詮釋資料為**選擇性**。

### 3.3   連結的詮釋資料紀錄

無障礙輔助性詮釋資料也可透過連結的紀錄[Packages]包含在內，但僅包含這樣的詮釋資料在連結的紀錄裡無法滿足本規格的發現性需求。

> ##### 注意事項
> 
> 連結記錄的優先順序根據EPUB版本而有不同（連結記錄在[EPUB 3.1]中有著高於包裝詮釋資料的優先順序，但在早期版本中順位較低）。結果而言，作者需要注意確保在包裝文件中的無障礙輔助性詮釋資料以及任何連結的紀錄並不包含相反的宣告，其才能影響到閱讀系統提供給讀者的資訊。

## 4.   無障礙出版品

### 4.1   導論

本章節為非規範性。

EPUB基於開放網頁平台，使用HTML、CSS、JavaScript與SVG作為其核心技術供內容製作使用。使用這些技術代表EPUB出版品可以在製作時提供高度無障礙輔助性，只要簡單地使用合適既有的網頁無障礙輔助技術即可。

製作無障礙輔助網頁內容最主要的依據是W3C網頁內容無障礙指南（Web Content Accessibility Guidelines, WCAG）2.0[WCAG 2.0]。此規格受到已經完成於[WCAG 2.0]作法的廣泛影響，以建立評量無障礙輔助內容的標竿，也採相同的四項高等級內容綱領[WCAG 2.0]可察覺（perceivable）、可操作（operable）、可理解（understandable）與耐用（Robust） — 為製作無障礙輔助EPUB出版品的核心。

本章節定義如何套用定義於[WCAG 2.0]的適用性規範，並且說明專屬於EPUB出版品的特性。

製作時符合本章節需求的EPUB出版品將能提供給使用者高度的無障礙輔助醒以符合廣泛多樣的閱讀需求與偏好。

### 4.2   與WCAG之關係

本章節為非規範性。

[WCAG 2.0]與[WCAG 2.0 Techniques]涵蓋廣泛的網頁內容無障礙輔助問題與解決方案[WCAG 2.0]從表格到嵌入媒體以致豐富語意。這些呈現了本規格所建構的基礎。

本規格不再重複於這些文件中介紹的需求與技巧，因為這可能會造成破壞兩份標準之間相容性的風險（例如，提供不同步或者衝突的指南）。同時，由於這些需求不會獨立使用，所以不會降低在製作無障礙輔助EPUB出版品的重要性。

本規格目的不在增加一組對EPUB出版品的新需求。這些需求的重要性不比WCAG所涵蓋的多或者少；它們對EPUB出版品而言，僅是必須跟從的原則（每項需求在對應的章節都會說明與WCAG之關係。）

同以為真的是在[EPUB Accessibility Techniques]文件中的技巧。其提供了各種專門提供給EPUB出版品的技巧，或者需要在EPUB出版品脈絡下的區隔。其不表示剩下的WCAG技巧不適用。

結果而言，儘管本章節可以在缺少對WCAG適用性的深刻知識下閱讀，要實踐本規格中的無障礙輔助性需求，仍將需要了解[WCAG 2.0]。

> ##### 注意事項
> 
> 由於本規格添加了不屬於WCAG的需求，一本符合[WCAG 2.0]的EPUB出版品可能不會符合本規格的需求。而不符合對EPUB出版品需求的EPUB出版品對本規格而言並非具無障礙輔助性。
> 
> IDPF預計與W3C和Web Accessibility Initiative一起在WCAG中整合對EPUB出版品的需求。

### 4.3   WCAG適用性

#### 4.3.1   WCAG適用性需求

EPUB出版品**必需**符合[WCAG 2.0]A等級，以符合本規格需求，但**推薦**其符合AA等級。

儘管本規格僅要求A等級適用性，地方或者國家法律可以影響EPUB出版品必須達到的等級以符合所考量的無障礙輔助層級。例如，AA等級適用性時常被採用作為無障礙輔助性在立法與政策上的標竿。此外取得或者配送EPUB出版品的人可以要求比定義於此的基準外，更高的適用性需求。

結果作者需要確保他們理解內容需要在法規或者配送脈絡上需要達到的無障礙考量需求，包含詢問任何必要的法規諮商。本規格提供的最小限度適用性不會取代這樣的需求，也不提供對任何可能引起的適法性問題保護。

#### 4.3.2   評量WCAG適用性

##### 4.3.2.1   頁面與出版品

[WCAG 2.0]綱領關注於如何評量獨立網頁，但EPUB出版品更接近組合在[WCAG 2.0]所參考稱為一系列網頁：「（一組）集合提供相同目的的網頁」。

結果上，當評量EPUB出版品的無障礙輔助性時，個別網頁 — 或內容文件，其在EPUB體系中的稱呼 — 無法被獨立檢視。然而，其整體無障礙輔助性可以被視為更大作品的一部分而必須要被評量。

例如，該出版品擁有邏輯閱讀順序但當出版品將其顯示於錯的順序，就缺乏足夠的資訊來判斷。同樣的，在每份內容文件中包含標題以補充提供整本出版品的標題：如果其中一項有缺失，都會影響到整體無障礙輔助性。

[WCAG 2.0]指南讓內容可察覺、可操作、可理解與耐用，所以**必需**透過整本EPUB出版品來評量，而非個別於其中的內容文件。

更多關於適用這些指南到EPUB出版品的的資訊可由[EPUB Accessibility Techniques]取得。

##### 4.3.2.2   套用適用性規範

當評量一本EPUB出版品時，[WCAG 2.0]適用性規範依照以下方式套用：

- 當判斷適用何適用等級時，EPUB出版品作為整體**必需**符合該等級的適用性需求。
- 作者**不得**使用EPUB的回退機制來提供一個適用的替代版本[WCAG 2.0]，是因為沒有可信賴的方法供使用者得以存取這些回退。當使用回退時，主要內容與其回退，兩方都**必需**符合該宣告適用等級的需求。EPUB特有的回退機制包含宣告回退、裝訂（bindings）以及透過*epub:switch*元素提供的內容切換（switching）。
- 當判斷「整頁」需求的適用性時（例如當在進行適用性宣告時，一頁的部分不得被排除），每份內容文件之整體都**必需**達到該適用等級，出版品中的每一份內容文件都**必需**符合宣稱的適用等級。

### 4.4   EPUB需求

#### 4.4.1   頁面導覽

##### 4.4.1.1   目標

提供固定頁面換頁位置導覽。

##### 4.4.1.2   瞭解該項目標

本章節為非規範性。

固定分頁內容目前依然普遍存在，就像印刷持續為最主要書籍被消費的媒介，無論對一般閱讀大眾還是教育現場。印刷並非固定翻頁的唯一來源，還可以透過數位出版品中的固定頁面邊界以及固定版面來提供。

結果而言，對於環境中非視覺的讀者來說，使用固定翻頁內容對他或她的同儕相對而言是項弱勢，由於無法簡單地找到該出版品的相同位置（例如，當老師指示學生一齊翻到同一指定的頁面）。

包含頁面邊界位置可以協助橋接此項不公平，以確保在使用文字重排媒體時不會因其選擇而相對弱勢。

提供頁面導覽也可以協助未提供固定頁面以及相等機制的文字重排出版品。這些出版品透過閱讀系統提供的預設分頁並非固定，其會因為可視範圍尺寸以及使用者的字體設定而變更。做為結果，同一本EPUB出版品在使用者間協調位置於缺乏固定參考的狀況下會顯得繁瑣。

##### 4.4.1.3   符合該項目標

作者**應該**在以下狀態成立時，於EPUB出版品中包含頁面導覽。

- EPUB出版品辨識為一本固定分頁出版品之動態分頁同等版本（例如，包含在印刷/數位同捆）。
- EPUB出版品提供作為固定分頁出版品的替代版，主要用於某環境中可以合理預測使用兩者中何者（例如，教育領域）。
- EPUB出版品與固定分頁出版品由同一個工作流程中產製，而得以跨格式保留分頁位置。

作者**可以**在沒有固定頁面作為參考時，於文字重排EPUB出版品中包含頁面導覽。

合規的EPUB出版品在包含頁面導覽時**必需**合乎以下需求：

- 其**必需**提供定位分頁位置的手段。
- 其**可以**包含分頁標記。
- 其**必需**辨識分頁來源。

此外，當頁碼在內容播放同步文字-聲音時（例如，EPUB3媒體層疊），作者**必需**在標記中識別頁碼以供播放控制使用。

請見頁碼[EPUB Accessibility Techniques]以獲得更多在EPUB出版品中包含頁面導覽的資訊。

##### 4.4.1.4   與WCAG之關係

本章節為非規範性。

包含頁面導覽呈現能從多面向完成[WCAG 2.0]需求的成功方法，其也提供了其他有意義的方式供使用者能存取內容（例如，在目錄之外提供額外資訊，線性閱讀順序以及其他導覽輔助）。

在混合印刷/數位環境中提供頁面導覽相當重要，包含此項功能的需求有著高於其他多面向成功方法的優先順序。

#### 4.4.2   媒體層疊播放

本章節為非規範性。

##### 4.4.2.1   目標

結構化媒體層疊提供更多無障礙輔助播放體驗。

##### 4.4.2.2   瞭解該項目標

媒體層疊提供了一項無障礙輔助播放體驗，供能從文字及聲音同步播放中獲得利益的任何人使用。也有助於僅需要聲音播放的使用者，或者僅從文字強調獲得利益的使用者。媒體層疊也對全部使用者提供了EPUB出版品從頭到尾無縫的播放體驗。

最基本的媒體層疊文件[Media Overlays]提供了對閱讀系統的最小限度教程，然而。也指示了文字強調與聲音片段如何對應到文字。結果讓使用者僅有最基本的開始與停止選項。

作者需要為媒體層疊文件加入結構與語意資訊，以讓閱讀系統能夠提供更多有用的體驗。有著豐富化標記，閱讀系統可以提供能力來跳過後面會干擾主要旁白的次要內容，讓使用者可以跳出像是表格的深層巢狀內容，也能讓他們在出版品的章節中導覽跳轉而不需要回到目錄。

##### 4.4.2.3   符合該項目標

媒體層疊文件不需要符合任何定義在[Media Overlays]外的需求就能符合本規格的適用性。

為增進媒體層疊的可用性，而會鼓勵作者確保其EPUB出版品符合以下需求：

- 識別媒體層疊文件中所有可跳過的結構[Media Overlays]。
- 識別媒體層疊文件中所有可跳出的結構[Media Overlays]。
- 為EPUB導覽文件包含一份媒體層疊文件[Media Overlays]。

> ##### 注意事項
> 
> 本規格的未來版本可能對媒體層疊文件提出更嚴格的適用性需求。

##### 4.4.2.4   與WCAG之關係

為媒體層疊文件添加結構與語意廣義地落在[WCAG 2.0]資訊與關係成功條件的目標。缺乏結構化與具備語意意義的播放序列，其影響將會剝奪使用者對內容的導覽豐富性。

### 4.5   適用性報告

為指出EPUB出版品合乎本規格的無障礙輔助性需求，其**必需**包含一項*conformsTo*特性[DCTERMS]以及一項*a11y:certifiedBy*特性[Accessibility Vocab]。

*conformsTo*特性的值**必需**為以下IRI之一：

- *http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-a* 該EPUB出版品符合所有無障礙輔助性條件並且達到[WCAG 2.0]A級適用性。


- *http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa* 該EPUB出版品符合所有無障礙輔助性條件並且達到[WCAG 2.0]AA級適用性。


- *http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aaa* 該EPUB出版品符合所有無障礙輔助性條件並且達到[WCAG 2.0]AAA級適用性。

*a11y:certifiedBy*特性指定了驗證該內容的組織名稱。內容認證者可以和EPUB出版品的製作者一樣，但可能為第三方無障礙輔助性驗證者。

> 以下範例呈現EPUB 3出版品由出版社自行進行驗證（*dc:publisher*與 *a11y:certifiedBy*特性之值相同）。
> 
> <metadata>
>   …
>   <dc:publisher>Acme Publishing Inc.</dc:publisher>
>   <meta property="a11y:certifiedBy">Acme Publishing Inc.</meta>
>   <link rel="dcterms:conformsTo" href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa"/>
>   …
> </metadata>

> 以下範例呈現PUB 3出版品由第三方進行驗證（*dc:publisher*與 *a11y:certifiedBy*特性之值不同）。
> 
> <metadata>
>   …
>   <dc:publisher>Acme Publishing Inc.</dc:publisher>
>   <meta property="a11y:certifiedBy">Foo's Accessibility Testing</meta>
>   <link rel="dcterms:conformsTo" href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa"/>
>   …
> </metadata>

> 以下範例呈現EPUB 3出版品由作者自行驗證。
> 
> <metadata>
>   …
>   <dc:creator>Jane Doe</dc:creator>
>   <meta property="a11y:certifiedBy">Jane Doe</meta>
>   <link rel="dcterms:conformsTo" href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa"/>
>   …
> </metadata>

> 以下範例呈現自行驗證的EPUB2出版品。
> 
> <metadata>
>   …
>   <dc:publisher>Acme Publishing Inc.</dc:publisher>
>   <meta name="dcterms:conformsTo" content="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa"/>
>   <meta name="a11y:certifiedBy" content="Acme Publishing Inc."/>
>   …
> </metadata>

> ##### 注意事項
> 
> 如果EPUB出版品由一個組織進行驗證，使用者一般可能會想知道該組織的名稱。不鼓勵以進行這項評量的個人人名來取代驗證組織的名稱，其可能降低使用者對其聲稱的信任。

如果驗證內容的組織發行了憑證或者標章已建立其權威用以驗證內容具無障礙輔助性，該項資訊可以透過*a11y:certifierCredential*特性[Accessibility Vocab]來提供。

> 以下範例呈現一個憑證。
> 
> <meta property="a11y:certifierCredential">A+ Accessibility Rating</meta>

如果驗證內容的組織提供了驗證的詳細報告，則可以透過*a11y:certifierReport*特性[Accessibility Vocab]來建立對驗證的連結。

> 以下範例呈現一個對遠端託管無障礙輔助性報告的連結。
> 
> <link rel="a11y:certifierReport"
>       href="http://www.example.com/a11y/report/9780000000001"/>

> 以下範例呈現一個本地託管無障礙輔助性報告的連結。
> 
> <link rel="a11y:certifierReport" href="reports/a11y.xhtml"/>

> ##### 注意事項
> 
> 由於每個詮釋資料格式其能表述的內容結為獨特，本規格並不限制外於包裝文件的適用性詮釋資料該如何表述。

> ##### 注意事項
> 
> 本規格不定義EPUB出版品的適用等級，僅需符合發現性詮釋資料需求，由於這樣內容的可用性僅能讓使用者自行由無障礙輔助性詮釋資料判斷。供出版品最佳化的報告需求定義在下一章。

## 5.   出版品最佳化

儘管[WCAG 2.0]提供了一般性的指南集使內容能廣泛地具備無障礙輔助性，適用的內容並非一直都為特定使用者群組最佳化。反之，供特定需求或者閱讀方式的最佳化內容經常不會合乎[WCAG 2.0]，因為其並非針對廣泛大眾所設計。

舉個例子，一份有著同步文字與聲音的EPUB出版品可能包含內容的完整錄音，但限制文字內容僅為主要標題。在這狀況下，EPUB出版品僅能由需要聆聽內容的使用者所消費（例如，他們可以聆聽完整出版品並且透過標題來進行導覽），但對於任何無法聽到聲音的人而言都無法使用。

換句話說，當一份EPUB出版品供特定閱讀方式最佳化，其無法達到WCAG適用等級不會讓其對目標對象提供更少的無障礙輔助性。

為處理這樣的矛盾，本規格將重點放在包含可發現的詮釋資料。最佳化的EPUB出版品可讓其目標對象透過所包含的豐富詮釋資料所發現，儘管其並非受到本規格的所認證的廣泛無障礙輔助出版品。

除了定義在發現性的詮釋資料需求外，最佳化的EPUB出版品**必需**在[DCTERMS]*conformsTo*特性中提供內容遵循的標準或者指南。該特性的值**必需**為一個IRI [RFC3987]其參照所遵循的標準或者指南。

> 以下範例呈現一份適用性宣告供符合[DAISY Audio]指南的EPUB 3出版品。
> 
> <package …>
>    <metadata>
>       …
>       <link rel="dcterms:conformsTo" href="http://www.daisy.org/guidelines/epub/navigable-audio-only-epub3-guidelines"/>
>       …
>    </metadata>
>    …
> </package>

如果該IRI不足以讓使用者了解其適用性（例如，該指南並非公開資訊），該內容如何受到最佳化的更多資訊可提供在無障礙輔助性摘要。

> 以下範例呈現一份供點字顯示最佳化的EPUB出版之無障礙輔助摘要。
> 
> <meta property="schema:accessibilitySummary">
>     This publication is optimized for braille readers. It will not be usable by persons who cannot read braille. The publication is designed for braille reading devices capable of displaying 6 character cells and 40 character line lengths. The text is not contracted, and follows Unified English Braille formatting conventions. All characters are encoded using the Unicode braille character set.
> </meta>

> 以下範例呈現一份供聲音顯示最佳化的EPUB出版之無障礙輔助摘要。
> 
> <meta property="schema:accessibilitySummary">
>     This publication is an audio book. It will not be usable by persons who cannot hear the audio. The publication is recorded by a professional narrator. There is navigation to the beginning of each chapter. The text of the publication is not included. Images are not included, but the photo captions are narrated at the end of the chapter where they occur.
> </meta>

> ##### 注意事項
> 
> 本規格未定義或者推薦供製作最佳化內容的標準或者指南。本規格另外提供一份非正式的最佳化標準清單，但並不代表為使用這些標準背書。

## 6.   配送

製作一份具無障礙輔助性的EPUB出版品自身不能保障內容會被使用者所取得或者消費。必須依賴所用的配送系統，其他要素也將會影響到EPUB出版品的整體無障礙輔助性。

本規格區分作者可以控制的要素以及無法控制的要素。例如，用來查找及取得內容的無障礙輔助性介面為配送過程中的基礎部分，其需要能夠搜尋並且檢視無障礙輔助性詮釋資料。這樣的介面一般無法由內容作者所控制，然而，由於EPUB出版品的配送經常由第三方所完成。但儘管作者可以控制其配送管道，這些應用程式的無障礙輔助性超過本規格的目標，像這樣的考量並不適用於EPUB出版品自身。

同時在作者將其內容遞交到配送系統時需要做些抉擇，例如要套用何種數位權利。儘管這些抉擇並不屬於準備內容的一環，但對使用者的潛在衝擊需要特別的關注。

為了最小化配送對無障礙輔助性的影響，作者因此**必需**依從以下遞送實踐：

- 當套用數位權利管理保護到EPUB出版品時，作者**不得**要求對輔助技術存取做出限制。
- 當配送需求一份配送紀錄（例如ONIX）伴隨著EPUB出版品時，作者**必需**包含無障礙輔助性詮釋資料在該格式允許範圍內加入其中。

> ##### 注意事項
> 
> 要獲得更多關於配送系統的無障礙輔助性資訊，請參考配送系統適用性。

## A.   製作與使用

### A.1   導論

儘管本規格關注無障礙輔助EPUB出版品的內容需求，但還有兩項額外的考量可以讓EPUB出版品供所有人使用：讓所有人都能夠製作EPUB出版品，以及讓所有人都能夠消費其內容。

儘管這些需求並非本規格主要關注點，本附錄提供了適用性需求供打造無障礙輔助製作工具、配送系統與閱讀系統。開發者若能達到或者做到多於這些需求，則可以讓應用程式供更廣泛的使用者所用。

> ##### 注意事項
> 
> 本附錄未來可能被專為這些考量而制定的規格所取代。

### A.2   製作工具適用性

合規的EPUB製作工具**必需**符合以下需求：

- 其**必需**符合[ATAG 2.0]A級適用性需求，並且遵從對B部分的澄清：
    - 其**必需**包含對定義在EPUB需求中EPUB專屬需求的支援，儘管所參照的[ATAG 2.0]主要供產生無障礙輔助網頁內容（能套用到其所產製的內容上）。
    - 其**必需**支援與EPUB出版品相關的[WCAG 2.0]無障礙需求，包含對加入定義於包裝詮釋資料中的發現性詮釋資料。請見頁面與出版品以獲得更多資訊。
- 其**應該**符合[ATAG 2.0]AA等級適用性需求，以及定義在後面領域的相同澄清。

### A.3   配送系統適用性

合規的配送系統**必需**符合以下需求：

- 其使用者介面**必需**合於[WCAG 2.0]AA級。
- 其**必需**提供能夠透過可獲得無障礙輔助性詮釋資料而來的搜尋結果。

### A.4   閱讀系統適用性

合規的閱讀系統**必需**符合以下需求：

- 其**必需**通過所有[A11Y Test Suite]基礎無障礙輔助閱讀系統測試。
- 其**應該**符合[UAAG 2.0]AA級適用性需求。

## B.   謝詞與貢獻者

本章節為非規範性。

EPUB由國際數位出版論壇集合出版社、販售商、軟體開發者以及相關標準專輯的集體付出所制定。

EPUB無障礙輔助性規格與技巧由國際數位出版論壇的EPUB維護工作小組所準備，在2015年七月由會員所通過的章程下所制定，由以下人士所帶領：

- Gylling, Markus (International Digital Publishing Forum) Chair (until August 2016)
- Siegman, Tzviya (John Wiley & Sons) Chair
- Conboy, Garth (Google Inc.) Vice-chair; Chair (beginning August 2016)
- Duga, Brady (Google Inc.) Vice-chair

這些文件則是由無障礙輔助小組所進行，由以下人士所帶領：

- LaPierre, Charles ( Benetech )
- Singh, Avneesh ( DAISY Consortium )

該工作組的活躍成員包括：

## IDPF會員

- Albert, Paolo (PubCoder)
- Baker, Mike (Houghton Mifflin Harcourt)
- Balakrishnan, Ramu (MPS Limited)
- Cho, Yong-Sang (KERIS (Korea Education and Research Information Service))
- Comerford, Rachel (Macmillan)
- Cramer, Dave (Hachette Book Group)
- Creasy, Keith (American Printing House for the Blind, Inc.)
- Deltour, Romain (DAISY Consortium)
- Geffroy, Jean-Marie (Mantano)
- Gusso, Lina (Pearson)
- Gylling, Markus (International Digital Publishing Forum (IDPF))
- Hanson, Lauren (Kaplan Publishing)
- Harris, Eric (VitalSource/Ingram Content Group)
- Heinser, Bernhard (Access for All)
- Johnson, Rick (VitalSource/Ingram Content Group)
- Kasdorf, Bill (Apex CoVantage)
- Keating, Patrick (Bluefire Productions)
- Kennedy, Naomi (Penguin Random House)
- Kerscher, George (DAISY Consortium)
- LaPierre, Charles (Benetech)
- Leo, Arthic (Amnet Systems)
- Mietkiewicz, Elie (Gutenberg Technology)
- Murata, Makoto (JEPA EPUB Study Group)
- Mussinelli, Christina (Associazione Italiana Editori)
- Prabhu, John (HOV Services)
- Siegman, Tzviya (John Wiley & Sons)
- Singh, Avneesh (DAISY Consortium)
- Soiffer, Neil (Design Science)
- Thurston, Jonathan (Pearson)
- Webster, Amaya (Benetech)
- Weck, Daniel (DAISY Consortium)

## 邀請專家/觀察員

- Andrews, David
- Bonelli, Giuseppe
- Garrish, Matt
- Kudou, Tomoyuki
- Leva, Paolo
- Marquès Solé, Daniel
- McGlone, Jonathan
- Morris, Julie
- Munchenburger, Manfred
- Rasmussen, Lloyd
- Reddy, Ramesh
- Rothberg, Madeleine
- Sheehan, John
- White, Jason

要取得更細節的謝詞以及每個版本EPUB的貢獻者資訊，請參考謝詞與貢獻者[EPUB3 Overview]

## C.   參考資料

### C.1 規範性文件

[A11Y Test Suite] [EPUB Accessibility Tests](https://github.com/daisy/epub-accessibility-tests) .

[ATAG 2.0] [Authoring Tools Accessibility Guidelines (ATAG) 2.0](https://www.w3.org/TR/ATAG20/) . Jan Richards, et al.

[Accessibility Vocab] [EPUB Accessibility Vocabulary](http://www.idpf.org/epub/vocab/package/a11y) .

[DCTERMS] [DCMI Metadata Terms](http://dublincore.org/documents/dcmi-terms/) .

[EPUB 3.1] [EPUB 3.1](https://www.w3.org/Submission/2017/SUBM-epub31-20170125/Overview.html) .

[Media Overlays] [EPUB Media Overlays 3.1](http://www.idpf.org/epub3/latest/mediaoverlays) .

[Packages] [EPUB Packages 3](http://www.idpf.org/epub3/latest/packages) .

[RFC2119] [Key words for use in RFCs to Indicate Requirement Levels](http://tools.ietf.org/html/rfc2119) (RFC 2119) . March 1997.

[RFC3987] [Internationalized Resource Identifiers (IRIs)](http://tools.ietf.org/html/rfc3987) (RFC 3987) . M Duerst, et al. January 2005.

[UAAG 2.0] [User Agent Accessibility Guidelines 2.0](https://www.w3.org/TR/2015/NOTE-UAAG20-20151215/) . Ian Jacobs, et al. 17 December 2002.

[WAI-ARIA 1.1] [Accessible Rich Internet Applications (WAI-ARIA) 1.1](https://www.w3.org/TR/wai-aria-1.1/) . Joanmarie Diggs, et al.

[WCAG 2.0] [Web Content Accessibility Guidelines (WCAG) 2.0](https://www.w3.org/TR/WCAG20/) . Ben Caldwell, et al.

[WCAG 2.0 Techniques] [Techniques for WCAG 2.0.](https://www.w3.org/TR/WCAG20-TECHS/) . Michael Cooper, et al.

[schema.org] [schema.org](https://schema.org/).

### C.2 參考性文件

[Accessibility FAQ] [EPUB Accessibility Frequently Asked Questions](http://www.idpf.org/epub/guides/a11y-faq).

[DAISY Audio] [Navigable audio-only EPUB 3 Guidelines](http://www.daisy.org/guidelines/epub/navigable-audio-only-epub3-guidelines) .

[EPUB Accessibility Techniques] [EPUB Accessibility Techniques](http://www.idpf.org/epub/latest/accessibility/techniques) .

[EPUB3 Overview] [EPUB 3.1 Overview](http://www.idpf.org/epub/31/spec/epub-overview.html) .