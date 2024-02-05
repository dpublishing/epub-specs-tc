# EPUB規格正體中文翻譯與範本

## 2023年度更新

### 一、更新翻譯文件至推薦標準版

〈EPUB 3.3〉、〈EPUB 3.3閱讀系統〉與〈EPUB可及性1.1〉於2023年5月通過W3C推薦流程成為正式推薦標準，同時數位發展部將提出〈網頁內容可及性規範（WCAG）2.1〉至W3C作為正式繁體中文翻譯版，故將這三份文件更新至推薦版本，並且在詞彙用語上以數位發展部WCAG 2.1版之翻譯進行更新。

-   [EPUB 3.3](https://dpublishing.github.io/epub-specs-tc/epub33_2023/EPUB_update/EPUB33.html)（原文：[EPUB 3.3](https://www.w3.org/TR/epub-33/)）

-   [EPUB 3.3 閱讀系統](https://dpublishing.github.io/epub-specs-tc/epub33_2023/EPUB_update/EPUBrs33.html)（原文：[EPUB 3.3 Reading
    Systems](https://www.w3.org/TR/epub-rs-33/)）

-   [EPUB可及性 1.1](https://dpublishing.github.io/epub-specs-tc/epub33_2023/EPUB_update/EPUBa11y11.html) （原文：[EPUB Accessibility
    1.1](https://www.w3.org/TR/epub-a11y-11/)）

### 二、新增翻譯文件

EPUB固定版面可及性文件為目前W3C出版維護小組正在進行中的文件，固定版面多以圖片為主，所以能夠提供的可及性功能較少，這份文件講明可以支援、應該考量的特別事項。

- [EPUB固定版面可及性](https://dpublishing.github.io/epub-specs-tc/epub33_2023/EPUB_fxl_a11y/epub_fxl_a11y.html)（原文：[EPUB Fixed Layout Accessibility](https://w3c.github.io/epub-specs/epub33/fxl-a11y/)）

### 三、新增範本

更新兩項範本

1. [印刷書頁碼範本](https://github.com/dpublishing/epub-specs-tc/tree/master/epub33_2023/印刷書頁碼範本/印刷書頁碼範本.epub)

內容為群星文化授權之卡夫卡《噢！父親》，其中包含使用EPUB Page-list（頁面列表）功能對應印刷書頁數，以及如何製作、閱讀系統可支援項目之說明。

- EPUB製作者（出版社、排版公司）可用於製作時參考。
- 電子書平台可在考量支援頁面列表時以本範本測試。

2. [EPUB可及性性符合WCAG規定說明與範本](https://github.com/dpublishing/epub-specs-tc/tree/master/epub33_2023/EPUB近用性符合WCAG規定說明與範本)

2021年時，台灣數位出版聯盟已經製作了兩份EPUB[可及性範本](https://github.com/dpublishing/epub-a11y-samples)。
今年提供新範本主要針對內容為達到WCAG A或AA等級，需要達成的成功準則的各種規定。

### 四、提出ACE by DAISY 1.3.2版正體中文地區化

- [1.3.2版中文化Repo](https://github.com/dpublishing/ace)
- [要求合併的Pull Request](https://github.com/daisy/ace/pull/399)

--------

## 2022年度更新

### 文件說明

本清單中之文件，是台灣數位出版聯盟基於W3C EPUB 3 Working Group所推出的EPUB 3.3規格群編輯草稿之中文翻譯版。EPUB 3.3為第一次由W3C工作小組循W3C推薦流程（W3C Recommendation Track）制定的標準，未來將會成為W3C正式推薦標準。

本文件也預期未來由台灣數位出版聯盟提交正式中文翻譯版。

由於EPUB 3.3第一次透過W3C推薦流程發布，按照該流程，必須對規格內容實作進行測試，所有功能都要有兩個以上實作支援才能通過，正式成為推薦標準。所以在結構上進行大幅度的調整。這部分在「EPUB 3總覽」中進行說明，EPUB 3總覽此份文件並非W3C推薦流程規格。

#### EPUB 3.3推薦流程文件

此次改版最大的變更，是將過去多份文件整合，為了易於閱讀，也為了讓規格讀者：「EPUB製作者」和「閱讀系統開發者」兩種身份能快速找到需要的資訊，所以EPUB 3.3主規格分成「EPUB 3.3（出版品）」與「EPUB 3.3閱讀系統」。這兩份將會採推薦流程發布。

過去有一些EPUB規格中的功能並未受到廣泛實作，所以在此次改版時，將這些內容分到其他文件，希望能更進一步完善這些功能，並且鼓勵實作，包括：

### 文件清單

-  [EPUB 3.3
    總覽](https://dpublishing.github.io/epub-specs-tc/epub33/epub-overview-33-20221004.html)（原文：[EPUB
    3.3 Overview](https://w3c.github.io/epub-specs/epub33/overview/)）

-   [EPUB 3.3](https://dpublishing.github.io/epub-specs-tc/epub33/epub-33.html)（原文：[EPUB 3.3](https://w3c.github.io/epub-specs/epub33/core/)）

-   [EPUB 3.3 閱讀系統](https://dpublishing.github.io/epub-specs-tc/epub33/epub-rs-33.html)（原文：[EPUB 3.3 Reading
    Systems](https://w3c.github.io/epub-specs/epub33/rs/)）

-   [EPUB 3 多重內容釋義出版品 1.1](https://dpublishing.github.io/epub-specs-tc/epub33/epub-multi-rend-11-20221014) （原文：[EPUB Multipule-Rendition Publication
    1.1](https://w3c.github.io/epub-specs/epub33/multi-rend/)）

-   [EPUB 3 文字轉換語音增強機制 1.1](https://dpublishing.github.io/epub-specs-tc/epub33/epub-tts-10.html) （原文：[EPUB Text-to-Speech Enhancements
    1.0](https://www.w3.org/TR/epub-tts-10/)）

-   [EPUB 3 結構語意用語集 1.1](https://dpublishing.github.io/epub-specs-tc/epub33/epub-ssv-11.html) （原文：[EPUB Structural Semantics Vocabulary
    1.1](https://www.w3.org/TR/epub-ssv-11/)）

-   [EPUB無障礙輔助性 1.1](https://dpublishing.github.io/epub-specs-tc/epub33/epub-a11y-11.html) （原文：[EPUB Accessibility
    1.1](https://w3c.github.io/epub-specs/epub33/a11y/)）

-   [EPUB無障礙輔助性技巧 1.1](https://dpublishing.github.io/epub-specs-tc/epub33/epub-a11y-tech-11.html) （原文：[EPUB Accessibility Techniques
    1.1](https://w3c.github.io/epub-specs/epub33/a11y-tech/)）

-   [EPUB無障礙輔助性與歐盟無障礙法之對應關係](https://dpublishing.github.io/epub-specs-tc/epub33/epub-a11y-eaa-mapping.html) （原文：[EPUB Accessibility EU
    Accessibility Act Mapping](https://www.w3.org/TR/epub-a11y-eaa-mapping/)）
    
### 範本

我們也製作了一份EPUB 3.3範本，對於各種延伸規格以及新的「資源平面」做了詳細的說明，以實例說明各種資源分類與回退機制。

然而，回退機制自EPUB 3.0開始已經存在，但閱讀系統對其支援並不佳。所以本範本可以通過EPUB檢查工具檢驗，合乎規定，但側載到閱讀程式中時，不保證能夠正常運作。

--------

## 2021年度

### 文件說明

本清單中之文件是台灣數位出版聯盟基於W3C EPUB3 最終社群小組規格（Final Community Group Specification）2019年05月08日公告版本之中文翻譯版。

#### 注意事項

- 以下規格文件清單之正式版本請以括弧內W3C網站連結公布之英文版為準。
- 這是一份由台灣數位出版聯盟自願翻譯之文件，本文件可能會因翻譯出現錯誤或語句不通順之處。如有發現錯誤或不妥之處，歡迎與台灣數位出版聯盟聯繫或直接於此GitHub儲存庫建立issue。

### 文件清單

- [EPUB 3 總覽](https://dpublishing.github.io/epub-specs-tc/epub32/epub-overview.html)（原文：[EPUB 3 Overview](https://www.w3.org/publishing/epub3/epub-overview.html)）
- [EPUB 3.2 規格](https://dpublishing.github.io/epub-specs-tc/epub32/epub-spec.html)（原文：[EPUB 3.2 Specification](https://www.w3.org/publishing/epub3/epub-spec.html)）
- [EPUB 3.2 變更點](https://dpublishing.github.io/epub-specs-tc/epub32/epub-changes.html)（原文：[EPUB 3.2 Changes](https://www.w3.org/publishing/epub3/epub-changes.html)）
- [EPUB包裝 3.2](https://dpublishing.github.io/epub-specs-tc/epub32/epub-packages.html)（原文：[EPUB Packages 3.2](https://www.w3.org/publishing/epub3/epub-packages.html)）
- [EPUB內容文件 3.2](https://dpublishing.github.io/epub-specs-tc/epub32/epub-contentdocs.html)（原文：[EPUB Content Documents 3.2](https://www.w3.org/publishing/epub3/epub-contentdocs.html)）
- [EPUB開放容器格式 3.2](https://dpublishing.github.io/epub-specs-tc/epub32/epub-ocf.html)（原文：[EPUB Open Container Format (OCF) 3.2](https://www.w3.org/publishing/epub3/epub-ocf.html)）
- [EPUB媒體層疊 3.2](https://dpublishing.github.io/epub-specs-tc/epub32/epub-mediaoverlays.html)（原文：[EPUB Media Overlays 3.2](https://www.w3.org/publishing/epub3/epub-mediaoverlays.html)）
- [EPUB無障礙輔助性 1.0](https://dpublishing.github.io/epub-specs-tc/epub32/epub-accessibility.html)（原文：[EPUB Accessibility 1.0](https://www.w3.org/Submission/epub-a11y/)）
