# 同步旁白
社群小組報告草稿 24 August 2020

**最新編輯草稿：**
    https://w3c.github.io/sync-media-pub/synchronized-narration.html
**編輯：**:
    Marisa DeMeglio (DAISY Consortium)
    Daniel Weck (DAISY Consortium)
**協助參與：**
    GitHub w3c/sync-media-pub
    提出問題
    版本紀錄
    修改要求

Copyright © 2019-2020 同步旁白規格貢獻者，由供出版品使用的同步媒體社群小組基於W3C社群貢獻授權協議(CLA)所發表。另有供人讀的摘要。

## 概要

本文件提供同步旁白的草稿版本。

## 本文件狀態

本規格由供出版品使用的同步媒體社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意，基於W3C社群貢獻授權協議(CLA)，適用於有限制的退出與其他狀態。可由W3C社群與業界小組了解更多。

本草稿依然基於供出版品的同步媒體社群小組之考量而可能有所變更。最突出的問題將會在文件所提供的連結所參照。

如果你想要對本文件提供建議，請將他們送到 public-sync-media-pub@w3.org（訂閱，存檔）。

## 目錄

1. 導論
1.1 術語
2. 規格
2.1 同步旁白格式
2.1.1 文件格式
2.1.2 特性
2.1.3 由HTML文件進行參照
2.1.3.1 連結
2.1.3.2 播放樣式
2.1.4 使用者代理處理

<hr />

## 1. 導論

同步旁白對一份文件提供了多模式的閱讀體驗，在該文件的主要格式（例如，文字）外擴增了額外的外部媒體（例如，聲音）。這項擴增透過一系列的同步點呈現，同步點讓不同媒體能夠彼此關聯（例如，這一段聲音與本HTML段落一起播放）。本文件定義同步旁白供獨立HTML文件使用。然而，由於本成果在開發上以網頁出版品（Web Publications）作為主要使用案例，而有一份伴隨的文件稱為「將同步旁白整合進出版品宣告」，其包含了與出版品的整合，例如有聲書。

### 1.1 術語

以下術語定義供本規格使用：

**聲音片段（Audio Clip）**
    聲音檔案的連續部分，由時間偏差（time offsets）所定義。

**文字斷片（Text Fragment）**
    HTML文件中的一個元素。

**播放樣式（Playback Styling）**
    強調，或其他樣式，在文字斷片正在播放時顯示。

**跳過（Skip）**
    能夠跳過內容播放，主要基於role。例如，跳過頁碼宣告或者腳註參照的聲音播放。

**跳出（Escape）**
    從播放一組結構中移出，並且回到其母容器的序列。例如，停止播放一個複雜表格並且繼續播放其主要內容。

## 2. 規格

### 2.1 同步旁白格式

#### 2.1.1 文件格式

同步旁白以一份JSON文件定義，以表達依序播放的媒體物件。

一份HTML文件僅能與一份同步旁白文件相關連。

> 問題 1
> 
> [Issue #10: mime/媒體類型](https://github.com/w3c/sync-media-pub/issues/10)

同步旁白文件其媒體類型為*application/vnd.syncnarr+json*。

#### 2.1.2 特性

- narration 供一組播放物件的容器，每一個都包含了媒體特性。

- audio 供聲音的媒體特性。值為一個媒體斷片URL其指向一個聲音資源，透過一個開始/結束時間值所參照，例如audio.mp3#t=123.45,678.9（請見https://www.w3.org/TR/media-frags/#naming-time）。

- text
    文字的媒體特性。值為一個URL「片段」其一般為一個獨特識別碼其參照到一個文件元素（例如，#section2.3）。

> 問題 1
> 
> [Issue #11:定義更多供文字參照的選項](https://github.com/w3c/sync-media-pub/issues/11)

- role
    供旁白容器或者文字/聲音匹配的語意資訊

> 問題 3
> 
> [Issue #12: role的值](https://github.com/w3c/sync-media-pub/issues/12)

> 問題 4
> 
> [Issue #9: 定義對平行媒體特性的限制](https://github.com/w3c/sync-media-pub/issues/9)

聲音與文字同步的範本：

{
  "role": "body",
  "narration": [
    {
      "text": "#id1",
      "audio": "audio.mp3#t=0.0,1.2"
    },
    {
      "text": "#id2",
      "audio": "audio.mp3#t=1.2,3.4"
    },
    {
      "role": "footnote-ref",
      "text": "#id3",
      "audio": "audio.mp3#t=3.4,5.6"
    },
    {
      "role": "aside",
      "narration": [
        {
          "text": "#id4",
          "audio": "audio.mp3#t=5.6,7.8"
        },
        {
          "text": "#id5",
          "audio": "audio.mp3#t=7.8,9.1"
        },
        {
          "text": "#id6",
          "audio": "audio.mp3#t=9.1,10.1"
        }
      ]
    },
    {
      "text": "#id7",
      "audio": "audio.mp3#t=10.1,11.2"
    },
    {
      "text": "#id8",
      "audio": "audio.mp3#t=11.2,13.3"
    },
    {
      "role": "footnote",
      "narration": [
        {
          "text": "#id9",
          "audio": "audio.mp3#t=13.3,14.4"
        },
        {
          "text": "#id10",
          "audio": "audio.mp3#t=14.4,17.4"
        },
      ]
    }
  ]
}

#### 2.1.3 由HTML文件進行參照

##### 2.1.3.1 連結

<head>
  <link
    rel="sync-media"
    href="sync-media/index.json"
    type="application/vnd.syncnarr+json">
</head>

##### 2.1.3.2 播放樣式

與HTML內容同步播放旁白，將帶出播放樣式的概念，如此作者可以對閱讀系統提供樣式資訊。例如，當一個HTML元素被「唸出」（例如，聲音與該指定的DOM片段同步播放），閱讀系統可以插入一個CSS Class名稱到該HTML元素中使得作者指定的樣式可以動態適用於現在正播放（又稱為「啟動」）的元素。

> 問題 5
> 
> [Issue #8：可否使用偽Class（pseudoclasses）供同步強調？](https://github.com/w3c/sync-media-pub/issues/8)

於此，我們提出兩個描述特性供播放樣式：

- *css-class-active*：可適用於HTML元素其呼應的聲音正在播放。作者可以用這個來強調正在朗讀的內容。
- *css-class-playing*：可適用於整份正在播放的HTML文件。作者可以用這個來讓目前沒有被唸到的內容不被強調。

本推薦不指定實際的Class名稱值供這些特性使用。作者必需按以下方式定義值：

<head>
  <meta name="sync-media-css-class-active" content="-my-active-element">
  <meta name="sync-media-css-class-playing" content="-my-document-playing">
</head>

作者可以為這些Class名稱在對應的CSS中定義樣式：

/* emphasize the active element */
.-my-active-element {
    background-color: yellow;
    color: black !important;
}

/* fade out the inactive text */
html.-my-document-playing * {
    color: gray;
}

#### 2.1.4 使用者代理處理

*narration*：在此陣列中的每個物件都要依序播放。在單一物件中的媒體特性要被平行處理。

*audio*: 從開始到結束播放片段。

*text*: 在瀏覽器中將元素提到焦點處理。當元素啟動時，套用播放Class名稱。