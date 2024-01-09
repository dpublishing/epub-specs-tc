↑
→
W3C
EPUB可及性 1.1
EPUB出版品的符合性與發現性規定

W3C工作草稿 2022年12月31日

更多關於本文件的細節
本版本：
https://www.w3.org/TR/2021/WD-epub-a11y-11-20211101/
最新發佈版本：
https://www.w3.org/TR/epub-a11y-11/
最新編輯草稿：
https://w3c.github.io/epub-specs/epub33/a11y/
歷史：
發布歷程
更新歷程
前一版本：
https://www.w3.org/TR/2021/WD-epub-a11y-11-20211029/
編輯者：
Matt Garrish (DAISY Consortium)
George Kerscher (DAISY Consortium)
Charles LaPierre (Benetech)
Gregorio Pellegrino (Fondazione LIA)
Avneesh Singh (DAISY Consortium)
提出回饋：
GitHub w3c/epub-specs (pull requests, new issue, open issues)
以郵件主旨…訊息主題…[epub-a11y-tech-11]寄送到public-epub3@w3.org(存檔)
Copyright © 2017-2021 W3C® (MIT, ERCIM, Keio, Beihang). W3C liability, trademark and permissive document license rules apply.

摘要

本規格指定了用來驗證EPUB出版品可及性的內容符合性規定。也同時指定了供EPUB出版品發現性使用的可及性後設資料規定。

本文件狀態

本章節解釋了本文件在其發表時的狀態。其他文件可能取代本文件。W3C的當前出版品清單以及本技術報告的最新版本可於位在 https://www.w3.org/TR/之W3C技術報告索引中取得。

編輯註解
目前未製作具可及性內容的出版社，建議可於本規格尚在制訂發展時，更新其產製流程以符合 [EPUB-A11Y-10]的規定。內容若符合該版本規定，基本上僅需做一些必要的變更，就能符合本規格之規定。

本文件由EPUB 3工作小組發布為工作草稿。本文件預計成為W3C推薦規格。

推薦使用GitHub Issues對本規格進行討論。此外，你也可以將意見寄送到我們的郵寄列表。請寄到public-epub3@w3.org（訂閱，存檔）。

文件在以工作草稿發表階段，不代表受到所有W3C會員所支持。

本文件為草稿，而且可能會隨時會被其他文件更新、取代、淘汰。編輯作業尚未完成前，不適宜引用本文件。

本文件由基於W3C專利政策下運作的一個小組所製作。W3C維護了一份與該小組交付成果有關的任何專利披露公開清單，該頁面也包含了專利披露的說明。任何人若實際擁有某項專利知識並相信其包含該專利之主要申請範圍，則必須依照W3C專利政策第六節之規定揭露該訊息。

本文件受 2020年9月15日W3C流程文件所規範。.

目錄

摘要
本文件狀態
1. 介紹
1.1 概要
1.2 成功技巧
1.2.1 國際化
1.3 應用於舊版規格
1.4 術語
1.5 符合性
2. 發現性
2.1 介紹
2.2 包裝後設資料
2.3 連結的後設資料紀錄
3. 無障礙出版品
3.1 介紹
3.2 與WCAG之關係
3.3 WCAG符合性
3.3.1 WCAG符合性規定
3.3.2 評量WCAG符合性
3.3.2.1 頁面與出版品
3.3.2.2 應用符合性準則
3.4 EPUB規定
3.4.1 頁面導覽
3.4.1.1 概要
3.4.1.2 可應用性
3.4.1.3 目標
3.4.1.3.1 分頁來源
3.4.1.3.2 頁面列表
3.4.1.3.3 分頁點
3.4.2 同步文字-聲音播放
3.4.2.1 概要
3.4.2.2 可應用性
3.4.2.3 目標
3.4.2.3.1 完整性
3.4.2.3.2 閱讀順序
3.4.2.3.3 可跳過性
3.4.2.3.4 可跳出性
3.4.2.3.5 導覽文件
3.5 報告符合性
3.5.1 介紹
3.5.2 出版品符合性
3.5.3 評量者資訊
3.5.4 重新評量符合性
4. 最佳化的出版品
5. 配布
6. 隱私與安全
A. EPUB近用性用語集
A.1 概要
A.1.1 關於此用語集
A.1.2 參照
A.1.3 供符合性使用的特性
A.1.3.1 certifiedBy
A.1.3.2 certifierCredential
A.1.3.3 certifierReport
B. 變更紀錄
C. 致謝
D. 參考資料
D.1 規範性文件
D.2 參考性文件
1. 介紹

1.1 概要

本章節為非規範性。

本規格──EPUB可及性──用以描述EPUB®生態系統中的兩項關鍵需求。

對EPUB出版品之無障礙品質提供發現性；以及
對具可及性的EPUB出版品進行評量以及認證。
提供可及性後設資料可協助判斷一本EPUB出版品之易用性。消費者能用來檢視內容擁有哪些特質，以決定一本EPUB出版品是否符合其需求，無論是否滿足可及性驗證標準。所有符合本規格的EPUB出版品，至少需滿足§2. 發現性中所描述的可及性後設資料規定。

就算EPUB製作者總是以高標準提供EPUB出版品之可及性，本規格依然設置了正式的規定，以用來驗證內容是否具備可及性。這些規定提供了EPUB製作者一系列明確的準則來評量其內容，並且能用於驗證其品質。一本具可及性的EPUB出版品需要滿足§3. 無障礙出版品中所描述的可及性規定。

本規格也討論EPUB出版品對於特殊閱讀模式的最佳化實踐，在這些案例中內容無法滿足本規格中廣義的可及性規定，但是只要遵從發現性以及報告規定，EPUB製作者可以讓使用者得以判斷是否該內容符合其需求。請參閱§4. 最佳化出版品以獲得更多資訊。

本規格也在§ 5. 配布中提及配布對於內容可及性與發現性的影響。

本規格不特別針對單一版本的EPUB。其可應用於合乎任何版本或者子集的EPUB出版品，包含了該標準的未來版本。

理想上，這些準則可協助評量任何基於開放網頁技術製作的數位出版品，然而確保這樣的應用並非本規格的目標。

注意事項
若想取得本規格中各決策的額外背景資訊，請參考EPUB可及性常見問題。

1.2 成功技巧（Success Techniques）

本章節為非規範性。

本規格以抽象方式以定義EPUB出版品的可及性規定，就如同網頁內容無障礙指引（WCAG）[WCAG2] 將其可及性準則和達成該指引的技巧分開一般。這種方法能夠讓準則隨著格式進化依然保持穩定。

為了讓此方法更便於執行，本規格伴隨的文件EPUB可及性技巧 [EPUB-A11Y-TECH-11] 匡列出合規的技巧。這些技巧說明如何在不同版本的EPUB中符合本規格之規定。

編輯注意事項
EPUB 3工作小組目前成立了一個任務組規劃供固定版面出版品使用的可及性技巧。當該文件正式發表時，將會於本章節提及。

1.2.1 國際化

本規格在討論使用者的可及性需求時，不會因為語言不同而有差異。這和定義在 [WCAG2] 中的各項原則（Principles）以及成功標準（success criteria）相同。目標是為了確保使用者能夠完整地消費出版品中資訊，無論偏好使用何種模式閱讀。

同時，所發行文字的語言與書寫習慣會影響符合可及性規定所必要的技巧。例如，EPUB要求支援萬國碼（Unicode）文字 [EPUB-3] ，就是為了確保能夠使用正確的字元資料（例如，EPUB製作者不需將文字做成圖片）。儘管這是重要的功能，但光這樣不足以確保任何語言的文字都具備可及性（例如，可能會需要額外資訊，如文字方向、強調、標點等）。

結論上，可能需要更多針對指定語言或特別文化的實踐以符合可及性規定。這些實踐如果專屬於EPUB，將會定義在本規格或隨附的達成技巧中；如果會廣泛地影響到所有網頁內容，會定義在其他地方（例如，在WCAG技巧或者針對指定語言的推薦最佳實踐中）。

1.3 應用於舊版規格

本章節為非規範性。

本規格可應用於任何EPUB出版品，就算符合不參照此規格的舊版本（例如，EPUB 2 [OPF-201] ）內容亦然。

這類EPUB出版品的製作者應該在製作內容時，符合本規格對可及性及發現性的規定。EPUB製作者也應該升級到最新版本的EPUB，以使用最先進的可及性功能以及技巧。

1.4 術語

本規格採用以下定義於EPUB 3 [EPUB-3] 中的術語：

EPUB內容文件
EPUB製作者
EPUB出版品
媒體層疊文件
包裝文件
閱讀系統
此外，也使用了 [WCAG2] 中的輔助科技定義。

注意事項
輔助科技不一定是與閱讀系統分開的應用程式。閱讀系統經常整合了獨立的輔助科技功能，像是文字轉換語音（text-to-speech）播放。

1.5 符合性

本規格中被標註為非規範性的章節，以及所有製作指引、圖表、範例以及註釋都為非規範性。本規格其他部分皆為規範性。

關鍵字：可以(MAY), 必須(MUST), 不得(MUST NOT), 選擇性(OPTIONAL), 推薦(RECOMMENDED), 以及應該(SHOULD)在本文件中，僅有在如上方式以粗體出現時，需按照BCP 14 [RFC2119] [RFC8174] 中的敘述詮釋。

2. 發現性

2.1 介紹

本章節為非規範性。

不像網頁，EPUB製作者透過許多管道配布EPUB出版品供人們使用──此模式使得EPUB成為成功的電子書和其他類型數位出版品的格式。然而，此模式造成的結果，就是出版品在可及性上的特殊細節，必須伴隨著一起發布。

線上書店從出版社以及作者處取得內容，故此，除非出版社透過後設資料告知，不然無法得知每次提交（新書）的製作品質。

我們主要關注點為確保任何關係組織與個人，都可以發現EPUB出版品的可及性品質。一本EPUB出版品可以擁有多於一組的充要存取模式，按照所提供的替代資訊來啟動另外一種閱讀的模式。例如，如果在一本出版品中為所有圖片提供了文字與描述，預設就會具備結合文字（textual）與視覺（visual）的充要存取模式，以及純文字（textual）充要存取模式。

使用者必須能夠在他們購買、借閱或以其他方式取得EPUB出版品時判斷其可用性，需要一個評判標準以知悉該本書下了多少工夫以符合可及性規定。

同樣地，未能符合本規格之可及性規定的內容，也不代表無法滿足個別讀者之需求。

唯有透過發行豐富的後設資料，才能讓使用者判斷內容是否適合他們使用。

2.2 包裝後設資料

所有EPUB出版品必須在其包裝文件中包含 [schema-org] 可及性後設資料，以展現其可及性特性，無論該出版品是否符合可及性或者最佳化規定。

EPUB出版品必須包含以下可及性後設資料：

accessMode — 一種必須的人類感官知覺系統，或認知官能，用以處理或者察覺內容（例如，文字textual、視覺visual、聽覺auditory、觸覺tactile）。

accessibilityFeature — 有助於提升整體內容可及性的功能及內容改編（例如，替代文字、延伸描述、字幕）。

accessibilityHazard — 任何內容呈現時可能造成的潛在危害（例如，閃光、模仿動作、聲音）。

accessibilitySummary — 一份人類可閱讀的整體可及性摘要，其包含了對於任何已知缺失的敘述（例如，缺少延伸描述，特定的危害）。

EPUB出版品應該包含以下 [schema-org] 可及性後設資料：

accessModeSufficient — 一組一或多個存取模式（譯註：即前述accessMode），其足以用來消費內容並且不會明顯掉失資訊。一本EPUB出版品可以有多於一組的充要存取模式供內容消費，取決於其包含了哪種類型的內容（然而，與accessMode不同，本特性用於不符合廣義可及性內容的額外加工，像是為聲音內容提供抄錄的文字）。

EPUB製作者可以包含本章節並未指定、額外的 [schema-org] 可及性後設資料。

注意事項
請參考Schema.org 供發現性用語集使用的可及性特性 [A11Y-DISCOV-VOCAB]，以取得能與這些特性使用的受同意術語完整列表。

注意事項
請參照後設資料發現性技巧 [EPUB-A11Y-TECH-11] 以獲得更多關於這些特性的資訊，以及如何將其包含在不同版本的EPUB中。也請見 在配布紀錄中包含可及性後設資料 [EPUB-A11Y-TECH-11]獲得更多資訊，以在其他格式中包含可及性後設資料。

2.3 連結的後設資料紀錄

可及性後設資料也能包含在連結的紀錄 [EPUB-3] 中（也就是透過link元素參照的後設資料紀錄），但光在連結的紀錄中包含這樣的後設資料，並無法滿足本規格的發現性規定。

3. 無障礙出版品

3.1 介紹

本章節為非規範性。

EPUB建構在開放Web平台上，HTML、CSS、JavaScript與SVG為應用在內容製作的核心科技。使用這些技術即代表，EPUB製作者只要妥善地應用既已完備的Web可及性技巧，就能打造出具高度可及性的EPUB出版品。

產出具可及性Web內容的主要依據是W3C網頁內容可及性準則（Web Content Accessibility Guidelines, WCAG） [WCAG2] 。本規格活用WCAG的大量成果，用來建立對可及性內容的評比標竿，也採用相同的四項高等級內容原則 — 可感知（perceivable）、可操作（operable）、可理解（understandable）、穩健的（robust） — 作為打造無障礙EPUB出版品的核心。

本章節定義了如何應用定義於WCAG中的符合性標準於EPUB出版品，以及說明EPUB出版品專屬的特性。

符合本章節規定製作的EPUB出版品，即擁有高度可及性，可廣泛地滿足讀者對閱讀的需求及偏好。

3.2 與WCAG之關係

本章節為非規範性。

WCAG [WCAG2] 及其相關的技巧，提供了網頁內容可及性問題及解法，其包含範圍廣闊 — 從表格到嵌入式多媒體，以至於豐富語義。這些都是建構本規格的基礎。

本規格並不重複這些規定，以及這些文件中所介紹的技巧。因為這麼做將會造成使兩份標準不相容的風險（也就是會讓指引不同步，甚至產生衝突）。同時，就算本規格不再重申這些規定，也不會減低其在製作可及性EPUB出版品中的重要。

相對之下，本規格定義如何應用WCAG在EPUB出版品上 — 相對於網頁為一整頁，EPUB出版品是 一系列Web文件的集合 — 並且添加一組 額外的規定。這些規定與WCAG所涵蓋的內容同等重要；EPUB出版品僅需單純遵守即可（每項規定都在對應的章節解釋與WCAG的關係）。

同樣的道理可套用在EPUB可及性技巧文件 [EPUB-A11Y-TECH-11] 上頭。該文件提供了專為EPUB出版品所用，或者在EPUB出版品脈絡下需要特別說明的技巧。但這不意味著不能應用其他的WCAG技巧。

結果上，儘管EPUB製作者可以在不完整知悉WCAG符合性的狀態下閱讀本章節，但若實作本規格的可及性規定，依然需要對WCAG有所理解。

由於本規格添增了不屬於WCAG的規定，所以一本EPUB出版品可能合乎WCAG、卻不合於本規格。

3.3 WCAG符合性

3.3.1 WCAG符合性規定

一本EPUB出版品若要合乎本規格，則：

必須符合WCAG 2.0 [WCAG20] 的規定，但強烈推薦符合最新推薦版本WCAG 2之規定。

必須符合A等級的規定，但強烈推薦符合AA等級之規定 [WCAG2] 。

這兩點規定所提供的報告彈性，是用以確保本規格能受到強制要求可及性的區域採用，而不需要取消或取代這些區域既已生效的規定。

本規格將WCAG 2.0 A等級設為規定底線，主要是為了給EPUB製作者對舊內容的反向相容性，以及在沒有正式規定下，鼓勵採用具可及性產製流程的彈性。大多數實踐可及性的製作者，都不會認為A等級提供了高度的可及性。

理想上，EPUB製作者應該試著符合最新版本WCAG 2 AA等級規定，但地方與國家法律，或代理商、通路端，才決定了他們需要符合的正式規定。

注意事項
對於可及性的法律規定，案例包括歐盟的2019/882指令，以及美國1973年發布《康復法案》的508條款。EPUB出版品需要符合高於基本A等級以上的成功標準，才能合乎這些法規。

持續跟進WCAG的優點是可以持續增進使用者的近用權。隨著Web技術迭代演進，察覺阻礙近用權狀況的手段也會進化，標準就會增添新的規定。符合這些新增的規定可以協助確保EPUB出版品使用最先進的技巧。雖然符合舊版規定依然有所幫助，但結果上提供的閱讀體驗不大理想。

同樣的，法律框架與政策也經常採用AA等級符合性作為可及性的評比標竿。理由是其提供了EPUB製作者實際上能執行的最大幅度的改進（EPUB製作者如果可以，就應該嘗試符合AAA等級，但是一般不大可能完整符合AAA等級規定）。當EPUB製作者僅符合A等級符合性，其內容對許多使用者族群妥協，結果上提供的閱讀體驗就會不大理想。

注意事項
W3C 可及性準則工作小組目前正在制定WCAG 3。該版本預計會與WCAG 2有很大的差異，本規格的未來版本會描述與其相關的符合性規定。但直到WCAG 3穩定並且廣受認識後，才會鼓勵EPUB製作者採用，但合乎該新版本，並非本標準之規定。

3.3.2 評量WCAG符合性

3.3.2.1 頁面與出版品

WCAG的原則 [WCAG2] 聚焦於評量單一網頁，但一本EPUB出版品更近似於WCAG中所指出的一組網頁「（一組）具備相同目的的網頁集合」[WCAG2]。

結論上，在評量一本EPUB出版品的可及性時，EPUB製作者不能單獨檢視個別頁面 — 在EPUB 3中稱為內容文件。相對之下，EPUB製作者必須將其視為更大作品的一部分來評量其可及性。

舉個例子，EPUB製作者光是給予單獨EPUB內容文件邏輯閱讀順序還不夠，還要確認該文件是否列於正確的閱讀順序中。同樣的在每一份EPUB內容文件中包含標題，可以作為整份出版品標題的補充：但無論少了哪一方，都會降低整體可及性。

EPUB製作者必須依照WCAG對內容的準則：可感知、可操作、可理解、穩健的，對整本EPUB出版品進行評量，而不僅對其中的個別內容文件為之。

EPUB無障礙技巧 [EPUB-A11Y-TECH-11] 提供了更多應用這些準則到EPUB出版品上的資訊。

3.3.2.2 應用符合性準則

當評量EPUB出版品時，WCAG 符合性標準 [WCAG2] 可按照以下方式應用：

當判斷合乎哪一個符合性等級時，EPUB出版品整體都必須符合要達成之等級的符合性規定。
EPUB製作者不得利用EPUB的回退機制來提供合規的替代版 [WCAG2]，因為沒有可靠的方法確保使用者能夠得以存取這些回退。如果EPUB製作者使用回退，那麼主要內容與其回退兩方都必須符合要達到之符合性等級規定。專屬於EPUB的回退機制包含了宣告回退 [EPUB-3]、bindings [EPUB-3]以及透過epub:switch元素的內容切換 [EPUB-3]。
[WCAG2] 有著「完整頁面」規定，也就是當宣稱合規時，頁面中的部分不能被視為例外。此項規格適用於EPUB出品的每一份內容文件（也就是全部都必須符合所宣稱的是用性等級）。
3.4 EPUB規定

3.4.1 頁面導覽

3.4.1.1 概要

本章節為非規範性。

靜態分頁的內容依然普遍，就像印刷書目前還是被一般讀者大眾以及教育情境兩方最主要用來閱讀的媒介。印刷書不是靜態分頁的唯一內容來源，固定版面（fixed-layout）數位出版品也具備靜態分頁邊界。

就結論而言，在使用靜態分頁內容的環境中，透過非視覺方式閱讀的讀者與其同儕相比，相對處於劣勢，他們不能輕鬆地在一份出版品中到達相同的位置（例如，老師要求學生翻到指定頁面）。

包含分頁邊界的位置可以彌補這種差距，讓選擇流動版面媒介的使用者不會居於劣勢。

流動版面出版品不能做到相同的靜態分頁，而提供分頁導覽可以提供協助。這些出版品由閱讀系統所做的預設分頁並非靜態，會隨著顯示區域尺寸以及使用者的字型設定而改變。結果上，在缺乏靜態參照資訊的狀況下，很難讓使用者在閱讀同一本EPUB出版品時，到相同的位置。

包含分頁導覽資訊，可作為一項達成多面向成功標準（Multiple Ways success criterion） [WCAG2] 的方法，其提供了另一個有意義的手段，讓使用者能用來存取內容（也就是在目錄、線性閱讀順序以及其他導覽協助之外多了這一項）。

提供分頁導覽在印刷書/電子書混用的環境中相當重要，將包含此項功能規定為優先事項，也可以視為達到多面向成功標準的多種手段之一。

注意事項
請見 [EPUB-A11Y-TECH-11] 的頁面標記以取得更多在EPUB出版品中包含頁面導覽的資訊。

3.4.1.2 可應用性

當以下任一狀況成立時，一本EPUB出版品應該包含定義在本章節中的分頁導覽目標：

EPUB製作者將該EPUB出版品視為靜態分頁出版品的動態分頁對等版（即為包含在一個印刷／數位組合中）；
EPUB製作者提供該EPUB出版品作為靜態分頁出版品的替代品，並應用於合理推斷會同時使用兩種版本的環境（例如教育情境）；或者
EPUB製作者在同一流程中產製出EPUB出版品以及靜態分頁的出版品，可跨格式維持分頁點位置。
EPUB製作者可以在沒有相對靜態分頁對應的狀況下，為流動版面的EPUB出版品包含分頁導覽。

3.4.1.3 目標

3.4.1.3.1 分頁來源

目標
識別靜態分頁點位置來源。

認識目標
使用者需要知道一本EPUB出版品分頁的來源，以決定是否能滿足他們的需求。例如印刷出版品的精裝與平裝版本可能分頁不一樣。同一本書的不同版本可能在分頁上也會不同。

包含靜態分頁來源之可辨識的識別碼，像是ISBN或ISSN，可確保使用者能用來判斷對應哪一個版本的分頁。

如果EPUB製作者要為僅有數位版之出版品加入分頁作為導覽輔助，就不能指定來源（也就是不能把該出版品當作自身的分頁來源）。

達成目標
當一本EPUB出版品包含分頁點標記及／或頁面列表，其對應到該出版品的靜態分頁版本時，EPUB製作者必須在包裝文件後設資料中識別其來源。

3.4.1.3.2 頁面列表

目標
提供靜態分頁點位置的導覽。

認識目標
頁面列表是用於導覽分頁點位置的主要手段，其提供了一組列表，可連結到EPUB出版品中的靜態分頁點位置。

閱讀系統一般使用此列表來產生「到第？頁」介面，讓使用者能夠輸入他們想要前往的頁碼，但有時也會讓使用者能夠存取整份列表來選擇他們想要前往的頁碼。

若缺少頁面列表，翻頁導覽將變得非常困難，只能依賴對個別分頁點標記的導覽（如果有的話）。

達成目標
一本EPUB出版品必須包含一份頁面列表。

EPUB製作者應該包含到由來源重新製作內容所有頁面的連結，（也就是這份列表不需要提供到空白頁、以及數位版本中沒有的內容的連結）。

EPUB製作者應該將供來源中所有頁面的連結包含於其中，無論是否被重新製作，但這並非一項規定。

3.4.1.3.3 分頁點

目標
提供靜態分頁點位置。

認識目標
在EPUB出版品中插入分頁點標記能夠提供給使用者他們在文字中哪一部分的脈絡。輔助科技可以使用這項資訊來告知使用者現在的頁碼，例如，當使用者想要摘要頁面上的內容時。

包含分頁點標記也能讓使用者透過頁數快速地前後翻閱，而不需要每次都透過頁面列表來存取。

包含這些標記也可簡化頁面列表的製作，只需要簡單地提供這些連結的參照目標即可。

達成目標
在EPUB出版品中包含分頁點標記為選擇性。

但若EPUB製作者要包含分頁點標記時，則：

他們應該包含由來源重新製作所有頁面使用的分頁點標記（即為，空白頁以及在數位版本中沒有被重製的內容就不需要標記）。
它們應該包含將供來源中所有頁面使用的的分頁點標記（無論是否被重新製作），但這並非一項規定。
此外，如果頁碼在該內容的同步文字語音播放中被朗讀出來（例如，EPUB 3媒體層疊 [EPUB-3] ），EPUB製作者必須在標記中識別其頁碼以控制播放。

3.4.2 同步文字-聲音播放

3.4.2.1 概要

本章節為非規範性。

媒體層疊能夠透過文字與語音同步提供可及性播放體驗給需要的受眾。對於僅需要聲音播放，或者僅需要閱讀時強調文字的的使用者也有幫助。媒體層疊也能為全部使用者提供整本EPUB出版品從頭到尾無縫的播放體驗。

然而，作為基礎的媒體層疊文件規格 [EPUB-3] 僅提供閱讀系統最小限的教程。其指出需要強調正在播放聲音片段的文字。結果使得使用者僅有基本的開始與停止選項可用。

EPUB製作者需要為媒體層疊文件添加結構與語意，才能讓閱讀系統提供更多有用的體驗。有完善的標記，閱讀系統可以提供這些功能，包括：跳過次要內容、使其不會干預到主要敘事。以及讓使用者可以跳出深層巢狀結構，如表格。以及讓他們可以出版品的章節間進行導覽，而不需要回到目錄頁。

為媒體層疊文件添加結構與語意，可廣義滿足 [WCAG2] 中的 資訊與關聯成功標準。缺少具有結構以及語意的播放序列，其影響會剝奪使用者對內容進行完整導覽的可能。

3.4.2.2 可應用性

媒體層疊文件必須符合 [EPUB-3] 中的規定。沒有必要符合定義於 [EPUB-3] 外的額外規定，即可符合本規格之規定。

為了讓媒體層疊的效益最大化，符合人們不同的閱讀需求，強烈鼓勵EPUB製作者符合定義在下一章節的選擇性目標。

注意事項
EPUB製作者不需要為了符合這些規定，在其EPUB出版品中添加媒體層疊。

3.4.2.3 目標

3.4.2.3.1 完整性

目標
確保全文都有對應的語音。

認識目標
雖然使用者可以使用文字轉換語音播放來將整本出版品轉換成聲音形式，但其體驗相對於提供預先錄製旁白的出版品來得差。文字轉換語音引擎受限於內建的詞彙，當遇到非常用字時，常會不曉得怎麼發音或者發錯音。結果讓使用者必須重複播放該字或者逐字拼出才能讀懂內容的意義，這降低了他們的閱讀速度並且阻礙對內容的理解。

因此，一本出版品額外提供全文的旁白顯得重要。使用者可以決定以何種偏好的模式進行閱讀：文字、聲音，或者兩者混合。

達成目標
EPUB製作者必須為所有文字內容透過媒體層疊方式提供同步語音播放。

3.4.2.3.2 閱讀順序

目標
確保同步文字-聲音播放符合邏輯閱讀順序。

認識目標
每一本EPUB出版品都有其預設閱讀順序，可讓使用者按照邏輯進度閱讀內容。其確保讀者可以跟從主要敘述，以及他們會在最符合文脈之處遇到次要內容。預設閱讀順序也建立一些較不明顯的關係，像是在表格的格與格以及列與列之間的順序。

如果在媒體層疊文件中的par及seq元素的序列不符合該順序，讀者無論單純聆聽聲音或者嘗試在視覺上跟隨進度。都會感到混亂，

讓播放排序符合預設閱讀順序是最安全的方法，以確保使用者可以跟隨文字。在某些案例裡，嚴格遵守這項原則可能會令閱讀體驗變得較差（例如，在某些狀況下以行，而非列來播放表格，可能更符合邏輯）。本項目標的目的並非禁止另類的呈現方式，而是確保任何偏差都能回歸內容的邏輯順序。

達成目標
EPUB製作者應該在媒體層疊文件中排列par與seq元素的順序，使其能夠反映以下兩者：

所參照的EPUB內容文件在書脊 [EPUB-3] 中的順序；以及
每個元素在其個別EPUB內容文件中的順序。
如果EPUB製作者使用不同的順序，其順序必須依然讓按照內容的邏輯播放。

3.4.2.3.3 可跳過性

目標
讓使用者可以自動跳過內容。

認識目標
閱讀理解的核心為：在不受干預之下閱讀該作品的主要敘述。EPUB製作者一般製作EPUB出版品，以視覺表現次要資訊，如側邊欄以及腳註等內容，會放在主要敘述流之外（例如，使用不同的背景色或者位置，如此一來讀者在閱讀時可以在視覺上分辨這些資訊）。

然而，如果讀者偏好使用聲音播放，就沒辦法同樣簡單地跳過這些資訊。媒體層疊在閱讀系統中，一般會在遇到次要內容時直接播放。

當EPUB製作者為媒體層疊文件提供結構性語意時，閱讀系統就可以用來讓使用者決定在播放時，預設要跳過哪些次要內容，提供更好的閱讀體驗。

達成目標
EPUB製作者應該在媒體層疊文件中識別所有可跳過的結構 [EPUB-3] 。

3.4.2.3.4 可跳出性

目標
讓使用者可以自動從結構性內容跳出。

當以視覺閱讀時，使用者可以快速移開或者跳出高度結構性的內容，像是表格、列表以及圖片等。表格使用行與列構成，例如，讀者可以快速順著兩軸線之一來找到他們要的資訊，並且找到以後能輕易地回到主要敘述。同樣的，列表中的項目可讓使用者掃到他們要的內容，然後在他們找到想要的資訊後跳出來。

但預設上，媒體層疊文件就無法提供相同簡單地跳出內容功能了。使用者無法從表格的格、列甚至表格本身中跳出，除非EPUB製作者將文件中的這些元素以結構化語意進行編碼。

當EPUB製作者提供這些資訊時，閱讀系統可以為使用聲音的讀者簡化播放以提供更適切的閱讀體驗。

達成目標
EPUB製作者應該在媒體層疊文件中識別所有 可跳出的結構 [EPUB-3] 。

3.4.2.3.5 導覽文件

目標
確保當閱讀系統顯示EPUB導覽文件時，聲音播放能夠作為導覽輔助。

認識目標
閱讀系統一般提供自有介面來提供EPUB導覽文件的導覽輔助。例如，閱讀系統開啟目錄維特化的介面，呈現在使用者正在閱讀內容的頂端。

為了使用這些介面，使用者一般而言必須仰賴文字轉換語音播放（如果有）來聽到目錄項目。

為EPUB導覽文件提供媒體層疊文件，可以提供閱讀系統透過聲音標記呈現連結的能力，為使用聲音的讀者增進體驗。

達成目標
EPUB製作者應該為EPUB導覽文件 [EPUB-3] 包含媒體層疊文件。

3.5 報告符合性

3.5.1 介紹

本章節為非規範性。

評量者透過在EPUB包裝文件中的後設資料特性表述，以報告一本EPUB出版品的可及性符合性等級。

該後設資料建構以下兩者：

所達到的符合性等級；以及
誰執行該項評量的資訊。
該後設資料使用了來自DCMI後設資料術語 [DCTERMS] 和EPUB可及性用語集的特性組合，將會於以下章節進行更詳細的說明。

3.5.2 出版品符合性

為了指出一本EPUB出版品合乎本規格的可及性需求，其必須包含一個conformsTo特性，其值必須精準對應（即為在大小寫以及空格上）以下模式：

EPUB-A11Y-A11Y-VER_WCAG-WCAG-VER-WCAG-LVL

其中：

A11Y-VER
EPUB製作者必須指定該出版品符合的EPUB可及性規格版本，但不包含小數點。EPUB製作者必須使用值 11 來指定本版本規格。

WCAG-VER
EPUB製作者必須指定該出版品符合的WCAG版本，但不包含小數點（例如對於WCAG 2.0為 20 ，WCAG 2.1為 21 ）。

WCAG-LVL
EPUB製作者必須指定該出版品符合的WCAG符合性等級（例如 A 或  AA）。

以下是符合性字串可用於合乎本規格的出版品：

EPUB-A11Y-11_WCAG-20-A
EPUB-A11Y-11_WCAG-20-AA
EPUB-A11Y-11_WCAG-20-AAA
EPUB-A11Y-11_WCAG-21-A
EPUB-A11Y-11_WCAG-21-AA
EPUB-A11Y-11_WCAG-21-AAA
注意事項
合規的符合性字串清單將會隨著W3C發布新版WCAG而新增。

範例 1
以下範例呈現一本EPUB 3出版品的符合性宣告，其合乎EPUB可及性規格1.1版，並且達到WCAG 2.1的AA等級。

<package …>
   <metadata>
      …
      <meta 
          property="dcterms:conformsTo"
          id="conf">
         EPUB-A11Y-11_WCAG-21-AA
      </meta>
      …
   </metadata>
   …
</package>
注意事項
未來WCAG 3.0版本可能也會出現新的等級名稱（現在為銅、銀、金）。這些名稱將會取代字串模式中的A、AA及AAA。

注意事項
EPUB製作者可以使用符合性URL，如 [WCAG2] 中符合性宣稱的必要元件一節所定義，當EPUB出版品僅達到WCAG符合性規定時，可透過conformsTo特性提供（即為，不完整符合本規格）。

由於 [WCAG2] 未定義如何透過URL來指定符合性等級，EPUB製作者還是可以找到替代手段，在需要時連結該資訊（例如透過可及性摘要）。

3.5.3 評量者資訊

EPUB出版品必須包含一個a11y:certifiedBy特性，用以指定評量該EPUB出版品的組織名稱。

注意事項
任何個人或者組織都可以進行符合性評量。評量者可為第三方，或和製作EPUB出版品的組織相同。

範例 2
以下範例呈現一本由出版社自行評量的EPUB 3出版品（dc:publisher 與 a11y:certifiedBy特性的值相同）。

<metadata>
  …
  <dc:publisher>
     Acme Publishing Inc.
  </dc:publisher>
  …
  <meta
      property="dcterms:conformsTo"
      id="conf">
     EPUB-A11Y-11_WCAG-21-AA
  </meta>
  <meta
      property="a11y:certifiedBy"
      refines="#conf">
     Acme Publishing Inc.
  </meta>
  …
</metadata>
範例 3
以下範例呈現一本由第三方進行評量的EPUB 3出版品。（dc:publisher與 a11y:certifiedBy特性的值不同）。

<metadata>
  …
  <dc:publisher>
     Acme Publishing Inc.
  </dc:publisher>
  …
  <meta
      property="dcterms:conformsTo"
      id="conf">
     EPUB-A11Y-11_WCAG-21-AA
  </meta>
  <meta
      property="a11y:certifiedBy"
      refines="#conf">
     Foo's Accessibility Testing
  </meta>
  …
</metadata>
範例 4
以下範例呈現一本由EPUB製作者自行評量的EPUB 3出版品。

<metadata>
  …
  <dc:creator>
     Jane Doe
  </dc:creator>
  …
  <meta
      property="dcterms:conformsTo"
      id="conf">
     EPUB-A11Y-11_WCAG-21-AA
  </meta>
  <meta
      property="a11y:certifiedBy"
      refines="#conf">
     Jane Doe
  </meta>
  …
</metadata>
範例 5
以下範例呈現一本自行評量的EPUB 2出版品。

<metadata>
  …
  <dc:publisher>
     Acme Publishing Inc.
  </dc:publisher>
  …
  <meta
      name="dcterms:conformsTo"
      content="EPUB-A11Y-11_WCAG-21-AA"/>
  <meta
      name="a11y:certifiedBy"
      content="Acme Publishing Inc."/>
  …
</metadata>
注意事項
當一本出版品由某組織評量時，使用者一般可能會想知道該組織的名稱。本規格鼓勵包含進行評量的個人姓名，以取代組織名稱，然而這樣的宣告可能會降低使用者的信任。

進行評量的日期可以透過一個dcterms:date特性 [DCTERMS] 連結到certifier，來進行指定。

範例 6
以下範例呈現進行評量的日期。

<meta
    property="a11y:certifiedBy"
    id="certifier">
   EPUB Accessibility Evaluator
</meta>
<meta
    property="dcterms:date"
    refines="#certifier">
   2021-09-07
</meta>
如果評量內容的組織有憑證或者標章可用來提供評量內容的權威，可透過一個a11y:certifierCredential特性來包含該項資訊。

範例 7
以下範例呈現一份憑證。使用refines屬性將憑證與certifier進行關聯。

<meta
    property="dcterms:conformsTo"
    id="conf">
   EPUB-A11Y-11_WCAG-21-AA
</meta>
<meta
    property="a11y:certifiedBy"
    refines="#conf"
    id="certifier">
   EPUB Accessibility Evaluator
</meta>
<meta
    property="a11y:certifierCredential"
    refines="#certifier">
   A+ Accessibility Rating
</meta>
如果評量內容的組織提供公開可讀的報告，可以透過一個a11y:certifierReport特性來提供對該報告的連結。

範例 8
以下範例呈現到遠端託管可及性報告的連結。

<meta
    property="dcterms:conformsTo"
    id="conf">
   EPUB-A11Y-11_WCAG-21-AA
</meta>
<meta
    property="a11y:certifiedBy"
    refines="#conf"
    id="certifier">
   EPUB Accessibility Evaluator
</meta>
<link
    rel="a11y:certifierReport"
    refines="#certifier"
    href="http://www.example.com/a11y/report/9780000000001"/>
範例 9
以下範例呈現到本地端可及性報告的連結。

<meta
    property="dcterms:conformsTo"
    id="conf">
   EPUB-A11Y-11_WCAG-21-AA
</meta>
<meta
    property="a11y:certifiedBy"
    refines="#conf"
    id="certifier">
   EPUB Accessibility Evaluator
</meta>
<link
    rel="a11y:certifierReport"
    refines="#certifier"
    href="reports/a11y.xhtml"/>
注意事項
每一種後設資料格式所能表達的內容都具其獨特性，本規格並不指定在EPUB包裝文件外，該如何表示符合性後設資料。

注意事項
本規格不定義外於EPUB 3出版品的可及性後設資料規定，即作為配布用的後設資料。確保內部與外部的可及性後設資料表述能夠一致，為作者、出版社以及通路的責任。進一步討論可及性對配布的影響，請見§ 5.配布。

3.5.4 重新評量符合性

本章節為非規範性。

注意事項
以下指引用於協助EPUB製作者判斷是否需要進行新的評量。而並非一項用以合乎本規格的規定。

一本EPUB出版品的符合性評量有效期間多長？這是個複雜的問題。不像網站會持續演進，EPUB製作者可能在初版之後就不會再更新EPUB出版品了。結論來說，EPUB出版品若不修改，就永遠適用於最終的評量。

然而，發布新版EPUB出版品來修正作品中的錯誤或者誤字，或者週期性地發布新版本，對出版而言這是常態。而並非所有對EPUB出版品變更都會改變其可及性，這使得EPUB製作者需不需要進行新的評量成了複雜的問題，要做整體、還是部分的重新評量就好，也是問題。

作為規則，EPUB製作者必須重新評量其內容，當他們對一本EPUB出版品的結構以及功能做了根本性的變更，例如：

調整了EPUB內容文件中標記的性質或者順序；
添加或修改承載資訊的圖片；
修改會影響到可讀性的格式（例如：對比）；以及
添加或修改了控制與表單等互動。
如果該EPUB出版品大致上內容與標記與前一發佈版本相同，EPUB製作者可以僅需要評量修改之處以重新確認符合性。

如果本規格或者 [WCAG] 在該EPUB出版品最終發布後推出了更新版本，本規格則推薦進行新的評量以確保符合性符合最新標準。在這狀況下，EPUB製作者可以不需進行完整的重新評量（即為，他們僅需要確認新的或者變更的成功標準，除非標準在方法或者符合性上進行了大幅變更）。

反過來，EPUB製作者在進行以下微幅變更時，不需要進行重新評量，如：

修正內文的錯誤（也就是沒有變更到標記）；
新增或者修改裝飾性的圖片；
修改不會影響到理解內容或者改變文字顯示的格式；以及
修改包裝文件的後設資料。
能夠判斷對EPUB出版品的可及性的個人，應該就能判斷修改是否為根本性。舉個例子來說，編輯可能不會理解表面上小小格式修正所造成的影響。

就算僅微幅修改，若可及性標準有所修訂，本標準依然建議更新評量（全部或者部分）。

EPUB製作者應該嘗試比這裡所敘述更積極的態度。若等到內容更新才檢視、更新EPUB出版品的可及性，可能使其無法對應近期的演進。舉個例子，出版社應該主動優先地週期性檢視旗下最熱銷的EPUB出版品，以確保它們能夠廣泛地受到最多數讀者所使用。

4. 最佳化的出版品

本章節為非規範性。

雖然WCAG [WCAG2] 提供了一組通用準則使內容能夠具備廣泛的可及性，但合規的內容並非都能針對特別使用族群最佳化。反過來說，針對特殊需求或者閱讀模式的最佳化內容，通常不會完美地合乎WCAG，因為其目標受眾為特殊族群。

例如，一本包含文字與聲音同步的EPUB出版品，內含完整內容的錄音，但是文字內容只有主要標題。這案例中，EPUB出版品可以被需要聽到內容的使用者所消費（也就是說，他們可以聽完整本出版品，並且透過標題進行導覽），但是卻無法被聽不到聲音的人所使用。

換句話說，當EPUB製作者針對特定閱讀模式為EPUB出版品進行最佳化，就無法達到WCAG符合性等級，卻依然能對預期的受眾提供完整的可及性。

為最佳化出版品定義規定並非本規格的目標，我們認同其他為這些特別需求所制定的標準以及準則。本規格僅提供基本的通用模式，以辨識EPUB製作者對內容做出了如何的最佳化。

詳細來說，如果一本EPUB出版品符合一項最佳化標準，最佳實踐推薦如下：

該EPUB出版品應該符合本規格的發現性後設資料規定，使可及性特性能被機器所讀取。
EPUB出版品應該在一個符合 [DCTERMS] 的 conformsTo 特性中，識別其所遵從的標準或者準則，使資訊能夠讓使用者取得。
若該標準未定義符合性的值供 conformsTo 特性使用，EPUB製作者應該使用URL [URL] 以指向標準的公開位置，這樣使用者可以查詢標準的特定細節。
如果識別碼不足以讓使用者理解其符合性（例如，該準則並未公開），EPUB製作者應該在可及性摘要中提供額外資訊說明內容如何最佳化。
當為最佳化的EPUB出版品製作準則時，建議這些實踐應該要與正式符合性規定相整合。

注意事項
請參照最佳化出版品標準指引，以取得非正式的標準列表。

範例 10
以下範例呈現一本符合DAISY可導覽僅有聲音的EPUB 3準則 [DAISYAudio] EPUB出版品的合規性聲明。

<package …>
   <metadata>
      …
      <link
          rel="dcterms:conformsTo"
          href="http://www.daisy.org/guidelines/epub/navigable-audio-only-epub3-guidelines"/>
      …
   </metadata>
   …
</package>
範例 11
以下範例呈現一本針對點字呈現最佳化的EPUB出版品的可及性摘要。

<meta property="schema:accessibilitySummary">
    This publication is optimized for braille readers. It will not be 
    usable by persons who cannot read braille. The publication is designed
    for braille reading devices capable of displaying 6-character cells and
    40-character line lengths. The text is not contracted, and follows 
    Unified English Braille formatting conventions. All characters are
    encoded using the Unicode braille character set.
</meta>
範例 12
以下範例呈現一本針對聲音呈現最佳化的EPUB出版品的可及性摘要。

<meta property="schema:accessibilitySummary">
    This publication is an audio book. It will not be usable by persons who 
    cannot hear the audio. The publication is recorded by a professional
    narrator. There is navigation to the beginning of each chapter. The text
    of the publication is not included. Images are not included, but the
    photo captions are narrated at the end of the chapter where they occur.
</meta>
5. 配布

本章節為非規範性。

儘管EPUB製作者不遵守本章節中的推薦事項，依然可以符合本規格。但有些法規要求EPUB製作者按照相同的方式執行。例如歐盟2019/882指令，在歐盟流通的數位出版品需要符合相同的規定。

製作具可及性的EPUB出版品，並不足以保證該出版品能被使用者以具輔助性的方式取得或者消費。取決於EPUB製作者如何配布他們的EPUB出版品。其他要素將會影響到整體可及性。例如，在配布過程中，具有可及性的介面供定位和取得內容是必要的環節，能夠搜尋並且檢視可及性後設資料也一樣重要。

由於EPUB製作者不能控制大多數的配布過程，所以並非本規格的目標。然而還是有些EPUB製作者所能控制的要素，例如，就算EPUB製作者通常不能控制數位權利管理（digital rights management, DRM）綱要套用在其EPUB出版品後的可及性，但他們可以決定出版品的使用權利。所以即使DRM綱要讓作者可以阻擋對出版品中文字的存取權，EPUB製作者需要注意別讓這類限制阻擋了輔助科技，而無法唸出文字內容。

為了讓配布對可及性的影響限縮在最小限度，本規格建議EPUB製作者遵守以下配布實踐：

其不得添加限制以限制輔助科技的存取；以及
若該格式支援，其必須在EPUB出版品供配布使用的紀錄格式中包含可及性後設資料（即為 [ONIX] 或 [MARC21] ）。
注意事項
配布端可能會套用數位權利管理綱要，其會阻礙可及性，但這並非EPUB製作者的錯。跟從本章節的指引，不是要限制EPUB製作者使用這樣的配布端。其目的是讓EPUB製作者不要啟動某個一般不會啟動的功能以影響可及性。

6. 隱私與安全

本章節為非規範性。

製作可及性內容並不會為使用者產生新的隱私與安全性考量。符合可及性規定僅為適當地使用既有的科技，本規格未提出任何新的功能。

EPUB製作者包含可及性後設資料也一樣，不會為其產生安全或隱私問題，僅描述一本EPUB出版品提供適用於不同使用者族群的通用概念。

使用可及性後設資料的一端，如閱讀系統、書店、以及其他可能建立使用者輪廓的介面，從另一個角度來看，就有可能違反個人隱私法律。例如，其可能有助於儲存或者預估使用者會想要消費或者最佳啟動其播放的內容類型。除非取得該類使用者的同意，開發者不應該搜集這類資訊，並且應該提供簡易刪除該使用者輪廓的手段。

儘管在使用者同意應用程式取得關於他們可及性需求資訊的狀況下，開發者必須確保這些資訊能夠保持私有（即為，不得和第三方廣告商、甚至原出版社分享）。

使用者基於內容的可及性特性進行搜尋，作為搜尋的一種特性，開發者也應該注意關於此類資訊之儲存或者探勘。這類資訊可以間接地描述使用者的能力。

A. EPUB無障礙用語集

A.1 概要

A.1.1 關於此用語集

本用語集定義了在EPUB出版品包裝文件後設資料中用以說明可及性的特性。

A.1.2 參照

用於參照本用語集的基準URL為  http://www.idpf.org/epub/vocab/package/a11y/#.

本規格保留字首"a11y:"供本用語集的特性使用。EPUB製作者不需要在包裝文件中宣告此字首。

A.1.3 供符合性使用的特性

A.1.3.1 certifiedBy

certifiedBy特性之定義
名稱：	certifiedBy
說明：	識別對EPUB出版品之可及性進行測試與負責認證的組織。
允許的值：	xsd:string
基數：	一或多個
範例：	
<meta
    property="a11y:certifiedBy">
   Accessibility Testers Group
</meta>
A.1.3.2 certifierCredential

certifierCredential特性之定義
名稱：	certifierCredential
說明：	識別一項憑證或者標章，其由與certifiedBy特性相關聯的組織所發行，其權威足以證明內容具可及性。
允許的值：	xsd:string
基數：	零或多個
延伸：	a11y:certifiedBy
範例：	
<meta
    property="a11y:certifiedBy"
    id="certifier">
   Accessibility Testers Group
</meta>
<meta
    property="a11y:certifierCredential"
    refines="#certifier">
   DAISY OK
</meta>
A.1.3.3 certifierReport

certifierReport特性之定義
名稱：	certifierReport
說明：	提供對一份可及性報告的連結，其由與certifiedBy特性相關聯的組織所製作。
允許的值：	xsd:anyURI
基數：	零或多個
延伸：	 certifiedBy
範例：	
<meta
    property="a11y:certifiedBy"
    id="certifier">
   Accessibility Testers Group
</meta>
<link
    rel="a11y:certifierReport"
    refines="#certifier"
    href="https://example.com/a11y-report/"/>
B. 變更紀錄

本章節為非規範性。

請注意，本變更紀錄僅用於辨識自EPUB可及性1.0以來根本性的變更 — 這些變更會影響到EPUB出版品的符合性，或具同樣的重要性。

若要取得在改版過程中所有議題的列表，請參考工作小組的議題追蹤器。

28-Sep-2021: 最佳化出版品章節改為非規範性，並且重新寫過以強調用以便是合乎哪些標準的最佳實踐，請見pull request 1833。
23-Sep-2021: 新增章節以解釋國際化的影響與使用的技巧，請見issue 1790。
07-Sep-2021: 新增使用refines屬性指向certifier後設資料的範例，以呈現預期的連結，請見issue 1789。
07-Sep-2021: 新增對 dcterms:date 特性能用於指出評量進行時間的解釋，請見issue 1590。
09-June-2021: 釐清僅有數位的出版品，就算有分頁點標記及/或包含分頁清單時，也不該指定其分頁來源。issue 1599。
29-Apr-2021: 變更符合性識別碼，使用連字號與連接號以避免在純文字字串中造成困擾，請見issue 1455。
26-Mar-2021: 新增非規範章節，以具體描述何時該重新評估EPUB出版品，請見issue 1470。
12-Mar-2021: 將配布章節改為非規範性，但新增一項注意事項指出法規（例如在歐盟）必須要遵守的規定。請見issue 1487。
08-Mar-2021: 添加目標使媒體層疊文件中par及seq元素的序列反應邏輯閱讀順序。請見issue 1556。
05-Mar-2021: 新增推薦，內容中從來源重製的所有頁面都該包含頁面標記，以及最佳實踐，為來源中的所有頁面都該包含頁面標記。請見issue 1502。
05-Mar-2021:新增推薦頁面列表中從來源重製的所有頁面都該包含連結，以及最佳實踐，頁面列表中所有來源的頁面都該包含連結。請見issue 1503。
05-Mar-2021: 重新調整EPUB規定章節架構，將頁面導覽以及媒體層疊標題中群組化的個別目標分開。請見issue 1458。
25-Feb-2021: 以更具彈性的文字字串取代用於回報符合1.0規格的IDPF URL。請見issue 1455。
19-Feb-2021: 更新對WCAG 2.0的參照，指向無日期的版本（除了特別指定WCAG 2.0版的符合性標準）。
01-Feb-2021: 變更對媒體層疊的推薦，將符合EPUB規格規定作為一項規定。請見 issue 1486。
17-Nov-2020: certifierCredentialcertifierReport特性新增refines屬性以及範例。請見issue 1410。
16-Nov-2020: 從發現性章節移除選擇性的無障礙附註性控制以及API後設資料參考資料。這些後設資料特性更適合用在閱讀系統上。請見issue 1327。
26-Sept-2020: 可及性1.0規格的改版將被發布作為一項ISO標準，並初始草稿文字。
C. 致謝

本章節為非規範性。

以下EPUB 3工作小組的成員對本規格的產製有所貢獻：

Juliette Alexandria (Access2online Inc.)
Luc Audrain (W3C Invited Expert)
Will AWAD (Newgen Knowledgeworks)
Sofia Bautista (Legible Media Inc.)
Laura Brady (W3C Invited Expert)
Leah Brochu (National Network for Equitable Library Service)
Matthew C. Chan (House of Anansi Press)
Yu-Wei Chang (Taiwan Digital Publishing Forum)
Fred Chasen (Scribd)
Garth Conboy (Google LLC)
Juan Corona (Legible Media Inc.)
Dave Cramer (W3C Invited Expert, chair)
Romain Deltour (DAISY Consortium)
Marisa DeMeglio (DAISY Consortium)
Brady Duga (Google LLC)
Reinaldo Ferraz (NIC.br - Brazilian Network Information Center)
John Foliot (W3C Invited Expert)
Teenya Franklin (Pearson plc)
Hadrien Gardeur (EDRLab)
Matt Garrish (DAISY Consortium)
Jen Goulden (Crawford Technologies)
Ivan Herman (W3C, staff contact)
Tetsu Hoshino (Kodansha, Publishers, Ltd.)
Norikazu Ishizu (Kadokawa Corporation)
Norihito IYENAGA (Kodansha, Publishers, Ltd.)
Ken Jones (Circular Software)
Deborah Kaplan (W3C Invited Expert)
Bill Kasdorf (Book Industry Study Group)
George Kerscher (DAISY Consortium)
Kazuhito Kidachi (Mitsue-Links Co., Ltd.)
Masakazu Kitahara (Voyager Japan, Inc.)
Toshiaki Koike (Voyager Japan, Inc.)
Ryo Kuroda (ACCESS CO., LTD.)
Charles LaPierre (Benetech)
Dan Lazin (Google LLC)
Laurent Le Meur (EDRLab)
Farrah Little (National Network for Equitable Library Service)
Karan Malhotra (Newgen Knowledgeworks)
Makoto Murata (DAISY Consortium)
Cristina Mussinelli (Fondazione LIA)
Yoichiro Nagao (Kodansha, Publishers, Ltd.)
Yoshinori Ohmura (SHUEISHA Inc.)
Rachel Osolen (National Network for Equitable Library Service)
Gregorio Pellegrino (Fondazione LIA)
Vijaya Gowri Perumal (Newgen Knowledgeworks)
Wendy Reid (Rakuten, Inc., chair)
Leonard Rosenthol (Adobe)
Shinobu Sato (Kadokawa Corporation)
Ben Schroeter (Pearson plc)
Daihei Shiohama (MEDIA DO Co., Ltd.)
Tzviya Siegman (Wiley)
Avneesh Singh (DAISY Consortium)
MOTOI SUZUKI (SHUEISHA Inc.)
Yutaka Suzuki (Kadokawa Corporation)
Kyrce Swenson (Pearson plc)
Shinya Takami (Kadokawa Corporation, chair)
Mateus Teixeira (W. W. Norton & Company)
Yukio Tomikura (Kodansha, Publishers, Ltd.)
Aimee Ubbink (Crawford Technologies)
Daniel Weck (DAISY Consortium)
Zheng Xu (Gardenia Corp, Rakuten, Inc.)
Fuqiao Xue (W3C)
Evan Yamanishi (W. W. Norton & Company)
Osamu Yoshiba (Kodansha, Publishers, Ltd.)
Junichi Yoshii (Kodansha, Publishers, Ltd.)
Naomi Yoshizawa (W3C)
D. 參考資料

D.1 規範性文件

[DCTERMS]
DCMI Metadata Terms. DCMI Usage Board. DCMI. 20 January 2020. DCMI Recommendation. URL: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
[EPUB-3]
EPUB 3. W3C. URL: https://www.w3.org/TR/epub/
[RFC2119]
Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc2119
[RFC8174]
Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words. B. Leiba. IETF. May 2017. Best Current Practice. URL: https://www.rfc-editor.org/rfc/rfc8174
[schema-org]
Schema.org. W3C Schema.org Community Group. W3C. 6.0. URL: https://schema.org/
[WCAG2]
Web Content Accessibility Guidelines (WCAG) 2. W3C. URL: https://www.w3.org/TR/WCAG2/
[WCAG20]
Web Content Accessibility Guidelines (WCAG) 2.0. Ben Caldwell; Michael Cooper; Loretta Guarino Reid; Gregg Vanderheiden et al. W3C. 11 December 2008. W3C Recommendation. URL: https://www.w3.org/TR/WCAG20/
D.2 參考性文件

[DAISYAudio]
Navigable audio-only EPUB 3 Guidelines. URL: http://www.daisy.org/guidelines/epub/navigable-audio-only-epub3-guidelines
[EPUB-A11Y-10]
EPUB Accessibility 1.0. Matt Garrish; George Kerscher; Charles LaPierre; Avneesh Singh. IDPF. 05 January 2017. URL: http://idpf.org/epub/a11y/accessibility-20170105.html
[EPUB-A11Y-TECH-11]
EPUB Accessibility Techniques 1.1. Matt Garrish; George Kerscher; Charles LaPierre; Gregorio Pellegrino; Avneesh Singh. W3C. 29 October 2021. W3C Note. URL: https://www.w3.org/TR/epub-a11y-tech-11/
[MARC21]
MARC 21 XML. URL: https://www.loc.gov/standards/marcxml/
[ONIX]
ONIX for Books 3.0. URL: https://www.editeur.org/8/ONIX/
[OPF-201]
Open Packaging Format 2.0.1. IDPF. 04 September 2010. URL: http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm
[URL]
URL Standard. Anne van Kesteren. WHATWG. Living Standard. URL: https://url.spec.whatwg.org/
[WCAG]
Web Content Accessibility Guidelines 1.0. Wendy Chisholm; Gregg Vanderheiden; Ian Jacobs. W3C. 5 May 1999. W3C Recommendation. URL: https://www.w3.org/TR/WAI-WEBCONTENT/
↑