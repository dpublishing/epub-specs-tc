# EPUB 3總覽
最終社群小組規格 08 May 2019

**最新編輯草稿**：
    https://w3c.github.io/publ-epub-revision/epub32/spec/epub-overview.html
**編輯**：
    Garth Conboy (Google Inc.)
    Matt Garrish (DAISY Consortium)
    MURATA Makoto (Keio Advanced Publishing Laboratory and JEPA)
    Daniel Weck (DAISY Consortium)
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

本文件提供內容製作者與軟體開發者一個認識EPUB® 3規格的起點。包含了所有資訊上的概要材料以說明EPUB 3的所有功能。

現在使用的EPUB 3版本定義於[EPUB32]，為此項標準的第二次小型修訂。最新版本的變更點記述於另一份資料性文件EPUB 3.2變更[EPUB32Changes]上。

## 本文件狀態

本規格由EPUB 3社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意本規格適用於W3C社群完整規範協議（FSA）。可進一步了解W3C社群與業界小組。

如果你想要對本文件提出意見，請寄送到 public-epub3@w3.org （訂閱，存檔）。

## 目錄

1. 功能
1.1 包裝文件
1.2 導覽
1.2.1 閱讀順序
1.2.2 導覽文件
1.3 詮釋資料
1.4 內容文件
1.5 固定版面
1.6 排版與CSS
1.7 多媒體
1.8 字型
1.9 腳本
1.10 文字轉換語音
1.11 容器
2. 全球語言支援
2.1 詮釋資料
2.2 內容文件
2.3 CSS
2.4 字型
2.5 文字轉換語音
2.6 容器
3. 無障礙輔助功能
3.1 導覽
3.2 語意標注
3.3 動態版面
3.4 語音解說與媒體層疊
3.5 回退
3.6 腳本
4. EPUB改版歷史
4.1 OEB, OCF與EPUB 2: 1999—2010
4.2 EPUB 3.0: 2010
4.3 EPUB 3.0.1: 2014
4.4 EPUB 3.1: 2017
4.5 EPUB 3.2: 2018
A. 參考資料
A.1 參考性文件

<hr />

## 1. 功能

本節涵蓋了EPUB的主要功能，包含整體能應用在製作EPUB出版品的各項重要元件與主題。

### 1.1 包裝文件

每一本EPUB出版品都包含了至少一份內容解釋，這些內容解釋以「包裝文件」呈現。

包裝文件列出了所有內容排版處理時所需要的諮詢。內容文件也定義了線性使用時的閱讀順序，以及讓詮釋資料和導覽資訊與內容解釋相互關聯。

包裝文件與一般的網頁相較，呈現出顯著的進展。以網頁為例，在內容裡嵌入了對資源的連結，雖然是簡單且具彈性的連結資源方式，卻也難以排列整理出所有排版呈現時所需的資源。此外，也沒有標準化的方式能讓網站定義某組網頁作為大型出版品的一部分，這就是EPUB *spine*元素[Packages32]的功能所在（換句話說，它提供了一個外部宣告的方式來強化對一系列文件的導覽順序）。最後，包裝文件以標準化的方式制定了詮釋資料如何通用地適於一系列文件上頭。

包裝文件也包含了*collection*元素[Packages32]，允許將一群邏輯上相關的出版諮詢設為群組。套用這項元素可應用於定義內容識別、處理以及排列功能，像是能夠用於定義嵌入的預覽內容，或者由構成的XHTML內容文件中取出索引或者字辭典定義。

包裝文件以及其他專用於解釋內容的說明，都定義在[Packages32]。

### 1.2 導覽

#### 1.2.1 閱讀順序

EPUB的關鍵概念為，EPUB出版品包含多種資源，而能被人、以及機器，按照一些特殊順序來完整導覽及閱讀。

各式各類的出版品都有明確的閱讀順序，或者整個內容有著邏輯上的進程。以小說為例，就是高度有順序性的文件——通常會有開頭、承續、結尾——但不是所有出版品都這麼依序閱讀：例如食譜與攝影集就可能更像是一個資料庫。但所有的文件都至少有一個最主要層級的邏輯閱讀順序內容項目，可以按照日期、主題、地點或者其它範疇（例如，食譜一般會按照烹煮方式排序）。

每一份EPUB出版品的內容解釋都定義了至少一個最主要層級內容的邏輯順序（即為spine[Packages32]），以及宣告性的目錄（即為EPUB導覽文件[EPUB32]）。EPUB出版品令這些資料結構化，而在內容之外透過機器可讀取的方式得以讓內容易於被發現及被使用。

EPUB出版品並不僅限於以線性順序閱讀內容，也可以使用預先包含的連結，以任意跳躍的方式來讀——如同網頁一般，而EPUB出版品以超文本技術打造——其所具備的基礎閱讀以及導覽方式以能被信任的方式建構，這是HTML頁面所不具備的。

### 1.2.2 導覽文件

每一份EPUB出版品的內容解釋都包含了一個特殊的XHTML內容文件，稱為EPUB導覽文件，該文件使用了[HTML] *nav*元素來定義人類可讀且機器也可讀的導覽資訊。

導覽文件取代EPUB 2中的NCX文件[OPS2]。導覽文件提供最底限無障礙輔助功能，並且具備NCX的導覽協助與各項功能，並且提供新的機能以及透過排版功能能夠為所有使用者提供強化的導覽。最重要的對於國際化（例如導覽文件採用XHTML文件格式，原生支援Ruby註釋）的較佳支援，以及支援嵌入式語法（MathML與SVG都可以包含在導覽連結之中）。

作為XHTML內容文件，導覽文件也提供了更大的彈性，可以使用CSS以及*hidden*屬性[Package32]來設計導覽的顯示，同時不會影響到閱讀系統存取這些資訊。

### 1.3 詮釋資料

EPUB出版品提供了一堆豐富的選項讓你添加詮釋資料。每一個內容解釋的包裝文件都包含了專門的*metadata*區塊[Package32]用來提供關於該EPUB出版品的一般性資訊，令該本EPUB出版品的書名、作者、識別碼以及其他資訊能夠輕易被存取。也提供了能夠使用link元素[Packages32]附加完整書目紀錄的方法。

包裝文件也能透過*unique-identifier*屬性[Packages32]為EPUB出版品建立獨有的識別碼。也需要在包裝的metadata區塊中加入最後修改日期，以配合識別碼來作為發布識別使用。這提供了用來辨識同一EPUB出版品不同版本的手段（請見出版品識別碼[Packages32]）。包裝識別碼解釋了如何在不修改獨有識別碼的狀況下發布EPUB出版品的新版並且識別為新版本的做法。

XHTML內容文件也包含了以完善的詮釋資料為文件增加註解的方法，讓資料能夠更具語意上的意義並且對於資訊處理以及無障礙協助做出貢獻（XHTML語意變化[ContentDocs32]）。XHTML內容文件可以使用RDFa以及Microdata屬性，提供內容層級的詮釋資料敘述（XHTML語意豐富性[ContentDocs32]）

### 1.4 內容文件

每一份EPUB出版品的內容解釋都包含一個以上的EPUB內容文件，定義於[EPUB32]中。這些內容文件是XHTML或者SVG文件用來描述可被閱讀的內容以及連結到相關的媒體資源上（例如，圖片，影音片段等。）

XHTML內容文件為定義於[HTML]中的一項規格。

### 1.5 固定版面

儘管EPUB的歷史就是致力於推動可重排的內容，但並非所有出版品都可以輕易地以重排的方式處理。童書、漫畫與圖文書、雜誌與其他多種內容形式，都需要透過精準分頁的排版能力才能夠完整表現其內容。

EPUB 3可以在詮釋資料中允許使用固定版面的XHTML內容文件[Package32]，以擴張原來使用SVG技術製作固定版面的表現性。這些詮釋資料可以讓頁面空間[ContentDocs32]受到控制，以打造出讓各元素能夠精準定位的畫布。

詮釋資料不僅用於指定哪些內容該是固定版面或者重排，也讓作者能夠在同時跨頁顯示時[Packages32]，指定想要的頁面方向[Packages32]，以及頁面在分頁中該如何定位[Packager32]，為EPUB出版品的表現提供了更廣泛的控制功能。

### 1.6 排版（Rendering）與CSS

EPUB的一項關鍵概念就是內容呈現可由使用者自行調整適應，而不是讓使用者去適應特別的顯示方式。HTML初始設計就支援對結構內容的動態排版，但隨著時間變化，瀏覽器對HTML的支援越來越集中在網頁應用程式的需求上，而多數熱門的網站都採用固定格式的版面。

然而，EPUB出版品是為了提供給視障者最大程度的無障礙輔助功能而打造，同時閱讀系統通常動態顯示文字與行、分頁排版，以適應顯示範圍的尺寸、使用者設定的字型大小，以及其他環境要素。但EPUB本身不保證這樣的行為，也包含對影像、向量圖片、影片以及其它非重排內容的支援，有些閱讀系統可能不支援動態顯示，或者全部支援。不過，對整個EPUB標準的進展過程而言，對動態適應排版和無障礙輔助功能的支援，是最主要的設計思維。

EPUB內容文件可以參照CSS樣式表，可使作者能定義想要的排版細節。EPUB 3對CSS的支援程度，定義於[CSSSnapshot]中。

EPUB 3也能透過CSS樣式同時支援橫排與直排版面，以及由左向右和由右向左書寫。若想了解更多資訊，請參照CSS全球語言支援章節。

### 1.7 多媒體

EPUB 3支援嵌入聲音與影片，透過使用[HTML]的*audio*和*video*元素嵌入XHTML內容文件中，可以使用所有這些元素具備的功能與各種屬性。若想要知道更多關於聲音與影片格式的細節，請參照[EPUB32]。

另一項EPUB 3的關鍵多媒體功能是包含了媒體層疊（Media Overlay）文件[MediaOverlays32]。當預錄好的旁白設定在內容解釋中能讓EPUB出版品使用時，媒體層疊提供讓聲音能伴隨內容文件上的文字同步播放的機制（請參閱語音解說與媒體層疊）。

### 1.8 字型

EPUB 3支援兩種緊密相關的字型格式——OpenType[OpenType]與WOFF[WOFF] [WOFF2]——同時適應傳統出版工作流程，以及逐漸興起以網頁為基礎的工作流程。文字處理程式在製作EPUB出版品時，通常只會從已經安裝的OpenType字型集合中挑選字型，而抓取網頁作為存檔的EPUB產生器則僅能存取WOFF資源（該資源不能在非預期，以及大多數沒有授權、捨棄WOFF詮釋資料的狀況下轉為OpenType格式）。

EPUB 3也支援亂數化與一般的字型資源，不限OpenType與WOFF字型格式。對亂數化字體資源的支援在對應多數商售的字型授權限制上為必要。

### 1.9 腳本

EPUB致力於以宣告式方式處理內容——資料可以被調整，但不該透過程式執行的方式產生——但支援腳本（Scripting），如[HTML]及[SVG2]中的定義（想要了解更多，請參照腳本[ContentDocs32]）。

然而，值得注意的是，EPUB 3不要求閱讀系統支援腳本，所以可能因為安全性因素而被關閉。

作者也需要注意的是EPUB出版品中的腳本可能因為網頁瀏覽器的支援而產生安全性問題。例如，傳統相同來源（same-origin）政策並不適用於已經下載到使用者本機端上的內容。但依然強烈建議將腳本限制在容器限制的脈絡內，如後面會說明的有腳本的內容文件—內容相容性[ContentDocs32]。

換言之，對個案腳本進行限制與否會影響使用者體驗，因為這麼做會降低內容在閱讀系統間交互使用的可攜性，並且對無障礙輔助功能和內容再利用性造成障礙。

### 1.10 文字轉換語音

EPUB 3提供以下文字轉換語音（text-to-speech, TTS）機制用以控制各種語音合成機制，像是發音、韻律與音色：

#### 發音辭典

EPUB 3可包含通用的發音辭典，使用W3C PLS格式 [PRONUNCIATION-LEXICON]可以讓作者提供發音規則套用在整個EPUB出版品上。想知道更多資訊可參考發音辭典[ContentDocs32]。

#### 文內SSML音素

與SSML音素（phonemes）功能[SSML]的合作，可以直接插入EPUB內容文件中提供精緻化的發音控制，可以取代預設的發音規則和/或參考的發音辭典（如上所述，採PLS格式）。想知道更多資訊可參考SSML屬性[ContentDocs32]

### 1.11 容器

一本EPUB出版品可以被以單一檔案（一個「可攜式文件」）傳輸及交換，其中包含包裝文件、所有內容文件以及所有其他包含在內容說明需要的資源。EPUB單一檔案容器格式為廣泛接納的ZIP格式，以及一個XML文件用以指定包裝文件的存放位置，每一份內容說明在ZIP封存檔案中的位置都預先定義了。

這種方法在EPUB出版品的製作者及任何接受EPUB的系統間提供了清晰的協定，這是一種可靠的表述方式，不受網路傳輸或者檔案系統規格所影響。

一本EPUB出版品的容器檔案表意定義於[OCF32]。

## 2. 全球語言支援

### 2.1 詮釋資料

EPUB 3的詮釋資料區塊中，所有的文字詮釋資料項目支援多元表述形式，以增進EPUB出版品的全球性發布。這多元語言特性（*alternate-script*）[Packages32]可透過*xml:lang*屬性來包括並且辨識多元語言，用於顯示該語言特有的詮釋資料。

使用這項特質，以日文EPUB出版品為例，可以額外包含作者名字的羅馬拼音顯示，及/或書明以羅馬拼音的另一種/多種表達型態。

翻頁方向屬性可讓改變分頁方向來廣泛支援全球各種內容的頁面排列方向（請見*page-progression-direction*[Packages32]）。

### 2.2 內容文件

XHTML內容文件採用了HTML的方向性功能來提升對雙向內容排版的支援：*bdi*元素可以讓一段文字獨立於包圍它的內容採不同方向排列，*bdo*元素允許其子內容的方向性可被覆寫，以及*dir*元素允許任何元素的方向受強制指定。

XHTML內容文件也支援用於輔助發音的Ruby註釋（也同時適用於導覽文件連結）。

SVG內容文件支援雙向文字排版，但不包括對Ruby的支援。

### 2.3 CSS

EPUB 3透過支援CSS 3模組而讓多種不同語言與文化的排版得以再現，一些特殊的強化包括：

- 支援直排，並且提供閱讀系統能讓讀者切換閱讀方向的能力；
- 處理「強調」字詞更完善，包含了日文「旁點」；
- 對於斷行提供更好的處理，斷行可以發生在字元層級，對於不使用空格來區分字詞的語言更方便；以及
- 對於斷詞有更好的控制，讓斷行效果更好。

### 2.4 字體

EPUB 3不要求閱讀系統內建特殊的系統字型。但如發生在網頁上的狀況一樣，特殊地區的使用者可能需要安裝字型來顯示地區設定下無法顯示的字符，閱讀系統可能會使用自己的字型或者字型引擎，而不使用作業系統安裝的字型。就結果來論，EPUB出版品的文字內容可能不會在所有的閱讀系統上得到如原生預期的排版結果。

為處理這個問題，EPUB 3提供了嵌入字型支援，用來協助文字內容的排版，並且推薦使用，讓內容能夠如預想一般呈現。

### 2.5 文字轉換語音

EPUB 3對PLS文件以及SSML屬性的支援增進了對發音的控制，讓作者可以在啟用文字轉換語音的閱讀系統中控制任何自然語言的表現。若想進一步了解更多資訊及其限制，請參閱功能章節的文字轉換語音部分。

結合CSS Speech與行內SSML因素也可以對Ruby元素進行微調。

### 2.6 容器

OCF容器格式支援UTF-8，允許內容資源的檔案與目錄能使用各種語言作為名稱。

## 3. 無障礙輔助功能

EPUB的一項主要目標在於提供內容無障礙輔助功能，很多EPUB 3的功能都支援這項需求。本章節將檢視這些功能，細述一些既有的最佳實踐，以確保EPUB出版品在可用的範圍內具備無障礙輔助性。

EPUB 3也包含一項無障礙輔助規範[E{UBAccessibility]，作為網頁內容無障礙規範[WCAG20]的延伸成果。這項規範定義了EPUB出版品在製作上的要求，而能使更廣泛為的使用者能夠使用。也提供了一份訣竅文件來提供最佳實踐，以達到這項需求。

值得注意的是，儘管無障礙輔助功能本身就相當重要，無障礙內容也是更有價值的內容：一個支援無障礙的EPUB出版品能夠被更多裝置接受，並且易於重新使用，不管是整體或者部分，無論被人或者自動工作流程。EPUB工作組強力建議作者能確保他們的內容具備無障礙功能。

### 3.1 導覽

EPUB 3以額外的EPUB導覽文件強化了NCX文件。如同上面對導覽文件的說明，導覽功能能呈現通用且具彈性的導覽系統。

導覽文件也能重新使用於EPUB出版品的內文中，只需將其包含在*spine*中即可。為了避免讓高度結構化的文件呈現出完整的目錄給讀者在內文中看到的狀況發生，顯示層級可以使用[HTML]的*hidden*屬性調整，這項屬性會被閱讀系統在*spine*之外處理目錄時忽略（也就是會提供別的檢視方式），可以避免提供的內容受到縮減。

也鼓勵作者可以提供額外的*nav*元素，尤其在EPUB出版品包含非結構化的物件，像是圖片、表格等，可以提供進一步對於內容使用的協助。

### 3.2 語意標注
 
[HTML]支援一系列能讓標注更具語意意涵的元素（例如*section*, *nav*與*aside*）同時也更明確地定義了一些HTML4元素的語意。使用這些元素，如同建立良好結構的網頁內容一般，當製作EPUB的XHTML內容文件時，這些額外的元素可以讓內容更容易被歸類及定義，無論用於呈現文件結構或者應用於邏輯導覽上。XHTML內容文件也原生包括對於ARIA role以及狀態屬性、事件的支援，有助於應用各種輔助科技於內容互動上。
 
EPUB 3包括了*epub:type*屬性，在功能上等同於W3C的Role屬性[Role-Attribute]。這項屬性可以讓XHTML內容文件中的任何元素提供額外關於用途以及在本作品中所具意義的資訊，但只能使用受控制的語彙與條件。想進一步了解，請參照XHTML語意變化[ContentDoc32]。

### 3.3 動態版面

EPUB的設計中心思想為動態版面：內容標準上應該動態生成版面，而非預先以分頁的方式設計完成（即為指定尺寸的「頁面」）。這項核心能力非常有用，例如針對不同尺寸螢幕以及視窗尺寸時都能提供最佳化的排版，同時能促進、簡化內容的無障礙輔助性。

EPUB同時也能夠接受高度設計的內容——例如透過點陣圖或者SVG圖像，甚至能使用CSS指定定位或者透過table元素來達成特別的視覺呈現——但強烈不建議作者使用這些技巧。這些做法在EPUB中並不可靠，許多閱讀系統的分頁演算法主要目標是將單一捲動的內容予以切割成頁，而非處理預先設定好的固定頁面。如果這些技巧對於傳達出版品的內容為必要，請考慮包含回退[EPUB32]（例如圖像小說）。

整體而言，推薦使用CSS樣式來達到視覺上的多變，但不建議指定絕對尺寸與定位。

### 3.4 語音解說與媒體層疊

內容的語音合成對於無障礙輔助來說相當重要，同時對其他使用者來說也是期待的一項功能。對語言合成最底限的支援是運用用於動態版面顯示的語意HTML。若想知道更多資訊了解下和使用EPUB XHTML文件的各種原生機制，請參考文字轉換語音。

[MediaOverlay32]能讓EPUB出版品中的文字與聲音內容同步，這項功能對於DAISY數位語音書的讀者而言已非常熟悉。層疊功能讓無障礙輔助領域提升到更為有用的層次：文字與語音的同步可以作為學習閱讀的工具，可以應用於多種狀況。

### 3.5 回退

並非所有格式原生具備無障礙功能，也並非所有使用者都願意以原來提供的格式閱讀。EPUB定義了一系列的方法來提供回退，而讓另一種排版方式成為可行。

出版品，或者內容層級的回退定義在外部資源[EPUB32]中。這些回退機制得以讓EPUB出版品能夠包含外部資源，另EPUB3內容在支援程度不一的閱讀系統間能具備相容性（例如能夠支援多種影片格式，或者能讓XHTML退回SVG內容文件以支援EPUB 2閱讀系統）。

此外，一個完整作品的多種副本可以透過單一EPUB出版品來提供，在OCF容器檔案中定多重*rootfile*元素（如容器檔(*container.xml*)[OCF32]中的描述）。這些額外的內容解釋回退可能會被使用，例如，一本預先分頁的圖像小說由SVG頁面序列構成，可以伴隨另一份以XHTML定義的具輔助性文字版本。

### 3.6 腳本

在腳本自身不會干涉文件的完整性下（即為：不會在不支援腳本的狀況下造成資訊不完整），EPUB 3接受對腳本化內容的漸進支援。結論上而言，就算使用腳本的文件能夠提供回退[ContentDocs32]以供進一步存取其內容，但文件自身在沒有腳本的狀況下也必須能被存取。

請確保你必須實現網頁文件在無障礙輔助性上的腳本最佳實踐，例如[WAI-ARIA]所提供的資訊。並且在互動會對使用者經驗造成重要影響的狀況，減少腳本使用。

## 4. EPUB改版歷史

### 4.1 OEB, OCF與EPUB 2: 1999—2010

EPUB基於稱為Open EBook Publication Structure（OEBPS）的交換格式。OEBPS 1.0於1999年由開放電子書論壇（Open eBook Forum）所通過，該組織後來改組為國際數位出版論壇（International Digital Publishing Forum, IDPF）。後續改版1.1與1.2版由IDPF分別在2001及2002通過。

當時認知到對於標準化格式有著確切需求，無論用於遞送到終端，或者作為交換格式。2005下半年開始為OEBPS格式制定單一檔案容器格式，後來由IDPF所通過並且在2006發布為OEBPS容器格式（OEBPS Container Format OCF）。同時進行OEBPS 2.0的改版作業，於2007年10月改名為EPUB 2.0發表，結合三大規格：Open Package Format（OPF），Open Publication Format（OPF）以及OCF格式。EPUB 2.0.1作為對2.0規格的維護性改版，提供了初始目的澄清與勘誤表，於2010年9月通過[OPF2][OPS2][OCF2]。

### 4.2 EPUB 3.0: 2010

EPUB規範的大型改版作業開始於2010年，目標是希望讓EPUB能夠更貼近HTML格式，並且引進新的原生多媒體功能、複雜的CSS排版顯示以及嵌入字體、透過腳本達到互動性、強化全球語言支援，並且提升無障礙輔助功能。一項新的規範，EPUB媒體層疊也在本版本提出，能夠讓文字與聲音在EPUB出版品中同步播放。為了讓規格名稱能和標準更貼近，Open Package Format規格改名為「EPUB出版品」，而Open Publication Format規格改名為「EPUB內容文件」。EPUB 3.0規格於2011年10月通過。[Publications30] [ContentDocs30] [OCF30] [MediaOverlays30] [EPUB3Changes]

### 4.3 EPUB 3.0.1: 2014

EPUB 3.0.1改版作業於2013到14年進行，主要為小型更新調整，並且整合了固定版面文件，在重排格式的EPUB不適合內容時，能讓作者更完整地控制內容表現。[Publications301] [ContentDocs301] [OCF301] [MediaOverlays301] [EPUB301Changes]

### 4.4 EPUB 3.1: 2017

EPUB 3.1是第一個EPUB 3格式的小型改版。其目標是希望讓EPUB 3與現今網頁標準更加貼近。所參考的重要標準變得沒有限期，這意味著當他們改版時，立即就可以應用於EPUB 3內容（例如，最新版本的HTML永遠可以立即套用，不需要透過EPUB改版）。能使用的CSS也整理澄清，同時刪除EPUB特有的屬性。

許多EPUB特有的屬性由標準中移除，特別是內容切換（Switching）、觸發（triggers）與連結（bindings）。這些變化需要新的包裝文件版本號。[EPUB31] [Packages31] [ContentDocs31] [OCF31] [MediaOverlays31] [EPUB31Changes]

### 4.5 EPUB 3.2: 2018

EPUB 3.2的改版就在EPUB 3.1完成後立即進行，目的是回復對於EPUB 3內容的相容性。EPUB 3.1推出新版就意味著作者、販賣端與閱讀系統開發者需要製作、遞送，使用兩個版本的EPUB內容，但這樣的改變所需的成本大於新版本帶來的優點。EPUB 3.2保持了所有EPUB 3.1版的優點，但是將一些刪除的元素重新恢復，這樣就不需要更改包裝文件中的版本號碼。[EPUB32] [Packages32] [ContentDocs32] [OCF32] [MediaOverlays32] [EPUB32Changes]

## A 參考資料

### A.1 參考性文件

[ContentDocs30]
EPUB Content Documents 3.0. URL: http://www.idpf.org/epub/30/spec/epub30-contentdocs.html
[ContentDocs301]
EPUB Content Documents 3.0.1. URL: http://www.idpf.org/epub/301/spec/epub-contentdocs.html
[ContentDocs31]
EPUB Content Documents 3.1. URL: http://www.idpf.org/epub/31/spec/epub-contentdocs.html
[ContentDocs32]
EPUB Content Documents 3.2. URL: epub-contentdocs.html
[CSSSnapshot]
CSS Snapshot. URL: https://www.w3.org/TR/CSS/
[EPUB301Changes]
EPUB 3.0.1 Changes from 3.0. URL: http://www.idpf.org/epub/301/spec/epub-changes.html
[EPUB31]
EPUB 3.1. URL: http://www.idpf.org/epub/31/spec/epub-spec.html
[EPUB31Changes]
EPUB 3.1 Changes from 3.0.1. URL: http://www.idpf.org/epub/31/spec/epub-changes.html
[EPUB32]
EPUB 3.2. URL: epub-spec.html
[EPUB32Changes]
EPUB 3.2 Changes. URL: epub-changes.html
[EPUB3Changes]
EPUB 3 Changes from 2.0.1. URL: http://www.idpf.org/epub/30/spec/epub30-changes.html
[EPUBAccessibility]
EPUB Accessibility. URL: http://www.idpf.org/epub/latest/accessibility
[HTML]
HTML. W3C. W3C Recommendation. URL: https://www.w3.org/TR/html/
[MediaOverlays30]
EPUB Media Overlays 3.0. URL: http://www.idpf.org/epub/30/spec/epub30-mediaoverlays.html
[MediaOverlays301]
EPUB Media Overlays 3.0.1. URL: http://www.idpf.org/epub/301/spec/epub-mediaoverlays.html
[MediaOverlays31]
EPUB Media Overlays 3.1. URL: http://www.idpf.org/epub/31/spec/epub-mediaoverlays.html
[MediaOverlays32]
EPUB Media Overlays 3.2. URL: epub-mediaoverlays.html
[OCF2]
EPUB Open Container Format (OCF) 2.0.1. URL: http://www.idpf.org/epub/20/spec/OCF_2.0.1_draft.doc
[OCF30]
EPUB Open Container Format (OCF) 3.0. URL: http://www.idpf.org/epub/30/spec/epub30-ocf.html
[OCF301]
EPUB Open Container Format (OCF) 3.0.1. URL: http://www.idpf.org/epub/301/spec/epub-ocf.html
[OCF31]
Open Container Format (OCF) 3.1. URL: http://www.idpf.org/epub/31/spec/epub-ocf.html
[OCF32]
Open Container Format (OCF) 3.2. URL: epub-ocf.html
[OpenType]
OpenType specification. Microsoft. URL: http://www.microsoft.com/typography/otspec/default.htm
[OPF2]
Open Packaging Format 2.0.1. URL: http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm
[OPS2]
Open Publication Structure 2.0.1. URL: http://www.idpf.org/epub/20/spec/OPS_2.0.1_draft.htm
[Packages31]
EPUB Packages 3.1. URL: http://www.idpf.org/epub/31/spec/epub-packages.html
[Packages32]
EPUB Packages 3.2. URL: epub-packages.html
[PRONUNCIATION-LEXICON]
Pronunciation Lexicon Specification (PLS) Version 1.0. Paolo Baggia. W3C. 14 October 2008. W3C Recommendation. URL: https://www.w3.org/TR/pronunciation-lexicon/
[Publications30]
EPUB Publications 3.0. URL: http://www.idpf.org/epub/30/spec/epub30-publications.html
[Publications301]
EPUB Publications 3.0.1. URL: http://www.idpf.org/epub/301/spec/epub-publications.html
[Role-Attribute]
Role Attribute 1.0. Shane McCarron et al. W3C. 28 March 2013. W3C Recommendation. URL: https://www.w3.org/TR/role-attribute/
[SSML]
Speech Synthesis Markup Language (SSML) Version 1.1. Daniel Burnett; Zhi Wei Shuang. W3C. 7 September 2010. W3C Recommendation. URL: https://www.w3.org/TR/speech-synthesis11/
[SVG2]
Scalable Vector Graphics (SVG) 2. Amelia Bellamy-Royds; Bogdan Brinza; Chris Lilley; Dirk Schulze; David Storey; Eric Willigers. W3C. 4 October 2018. W3C Candidate Recommendation. URL: https://www.w3.org/TR/SVG2/
[WAI-ARIA]
Accessible Rich Internet Applications (WAI-ARIA) 1.0. James Craig; Michael Cooper et al. W3C. 20 March 2014. W3C Recommendation. URL: https://www.w3.org/TR/wai-aria/
[WCAG20]
Web Content Accessibility Guidelines (WCAG) 2.0. Ben Caldwell; Michael Cooper; Loretta Guarino Reid; Gregg Vanderheiden et al. W3C. 11 December 2008. W3C Recommendation. URL: https://www.w3.org/TR/WCAG20/
[WOFF]
WOFF File Format 1.0. Jonathan Kew; Tal Leming; Erik van Blokland. W3C. 13 December 2012. W3C Recommendation. URL: https://www.w3.org/TR/WOFF/
[WOFF2]
WOFF File Format 2.0. Vladimir Levantovsky; Raph Levien. W3C. 1 March 2018. W3C Recommendation. URL: https://www.w3.org/TR/WOFF2/
↑