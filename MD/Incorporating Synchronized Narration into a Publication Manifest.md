# 將同步旁白整合進出版品宣告
社群小組報告草稿 24 August 2020

**最新編輯草稿：**
    https://w3c.github.io/sync-media-pub/incorporating-synchronized-narration.html
**編輯：**
    Marisa DeMeglio (DAISY Consortium)
    Daniel Weck (DAISY Consortium)
**協助參與：**
    GitHub w3c/sync-media-pub
    提出問題
    版本紀錄
    修改要求

Copyright © 2019-2020 將同步旁白整合進出版品宣告規格貢獻者，由供出版品使用的同步媒體社群小組基於W3C社群貢獻授權協議(CLA)所發表。另有供人讀的摘要。

<hr />

## 概要

本文件提供將同步旁白整合進出版品宣告的草稿版本。

## 本文件狀態

本規格由供出版品使用的同步媒體社群小組所發表。並非W3C標準也不在W3C標準程序上。請注意，基於W3C社群貢獻授權協議(CLA)，適用於有限制的退出與其他狀態。可由W3C社群與業界小組了解更多。

本草稿依然基於供出版品的同步媒體社群小組之考量而可能有所變更。最突出的問題將會在文件所提供的連結所參照。

如果你想要對本文件提供建議，請將他們送到 public-sync-media-pub@w3.org（訂閱，存檔）。

## 目錄

1. 導論
1.1 術語Terminology
2. 規格Specification
2.1 包含進出版品宣告Inclusion in a Publication Manifest
2.2 出版品宣告範本Publication Manifest Examples
A. 參考資料
A.1 參考性文件

<hr />

## 1. 導論

同步旁白文件涵蓋了如何讓一份HTML文件與同步旁白產生關聯，透過在HTML文件自身中指向的方式進行。本文件展示如何將同步旁白在出版品宣告層次上整合。這麼做的理由包括了：

- 有同步旁白的主要資源可能會與一個聲音檔案相關連，且無法包含對外部文件的參照。
- 對閱讀系統而言，在宣告層級會更容易找到替代格式，相對於在每一個HTML文件中反覆查找。

### 1.1 術語Terminology

特別供出版界使用具有特殊意涵的術語在本文件中為首字大寫（中文版則加上括號，如「閱讀系統」）。這些術語及其定義的完整清單則提供在[pub-manifest]中。

每一章節術語僅在第一次出現時，連結到其定義。

此外，以下術語定義供本規格使用：

[Issue #16: 添加包裝術語](https://github.com/w3c/sync-media-pub/issues/16)

**VOCAB**
    待辦事項：我們需要定義何種術語以特別供整合到網頁出版品使用？

## 2. 規格Specification

### 2.1 包含進出版品宣告Inclusion in a Publication Manifest

> 問題 1
> 
> [Issue #15: 澄清包裝規則](https://github.com/w3c/sync-media-pub/issues/15)

同步旁白文件可以與出版品宣告中的閱讀順序項目產生關聯。可以透過創立一個LinkedResource物件供同步旁白並且加入閱讀順序項目的替代特性中辦到：

{
  "readingOrder": [
      {
        "url": "html/c001.html",
        "alternate": {
          "type": "LinkedResource",
          "url": "narration1.json",
          "encodingFormat": "application/vnd.syncnarr+json",
          "duration": "10000s"
        }
      },
      ...
    ]
    ...
}

同步旁白文件為一個LinkedResource並且使用以下特性：

- duration: 如有聲書
- encodingFormat: application/vnd.syncnarr+json
- readBy: 如有聲書
- url: 如出版品宣告

### 2.2 出版品宣告範本Publication Manifest Examples

本章節為非規範性。

> 問題 1
> 
> [Issue #17: 添加更多宣告範本](https://github.com/w3c/sync-media-pub/issues/17)


## 有聲書

有聲書可以添加同步媒體資源來啟動逐段落播放：

{
	"@context" : ["https://schema.org", "https://www.w3.org/ns/pub-context"],
	"type"		 : "Audiobook",
	"url"      : "https://publisher.example.org/janeeyre",
	"name"     : "Jane Eyre",
	"readingOrder" : [{
		"type"	: "LinkedResource",
		"url"   : "audio/part001.wav#0",
		"encodingFormat" : "audio/vnd-wav",
		"name"  : "Chapter 1",
		"duration" : "457.931",
		"alternate" : {
      "type": "LinkedResource",
      "url": "sync-media/part001-1.json",
      "encodingFormat" : "application/vnd.syncnarr+json"
    }
	}, {
		"type"  : "LinkedResource",
		"url"   : "audio/part001.wav#457.932",
		"encodingFormat" : "audio/vnd-wav",
		"name"  : "Chapter 2",
		"duration" : "234.245",
		"alternate" : {
      "type": "LinkedResource",
      "url" : "sync-media/part001-2.json",
      "encodingFormat" : "application/vnd.syncnarr+json"
    }
	}]
}

## 多重文件網頁出版品

此為基於待辦事項的假設範例

{
  "@context": ["https://schema.org", "https://www.w3.org/ns/wp-context"],
  "url": "https://publisher.example.org/mobydick",
  "author": "Herman Melville",
  "dateModified": "2018-02-10T17:00:00Z",

  "readBy": "Someone",
  "duration": "20000s",

  "sync-media-css-class-active": "-my-active-element",
  "sync-media-css-class-playing": "-my-document-playing",

  "readingOrder": [
    {
      "url": "html/c001.html",
      "alternate": [{
        "type": "LinkedResource",
        "url": "narration1.json",
        "encodingFormat": "application/vnd.syncnarr+json",
        "length": "10000s"
      }]
    },
    {
      "url": "html/c002.html",
      "alternative": [{
        "type": "LinkedResource",
        "url": "narration2.json",
        "encodingFormat": "application/vnd.syncnarr+json",
        "length": "10000s"
      }]
    }
  ]
}

## A. 參考資料

### A.1 參考性文件

**[wpub]**
    [Web Publications](https://www.w3.org/TR/wpub/). Matt Garrish; Ivan Herman. W3C. 13 August 2019. W3C Note. URL: https://www.w3.org/TR/wpub/