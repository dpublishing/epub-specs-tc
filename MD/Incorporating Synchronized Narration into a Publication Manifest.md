# 將同步旁白整合進出版品宣告

Incorporating Synchronized Narration into a Publication Manifest
Draft Community Group Report 24 August 2020

Latest editor's draft:
https://w3c.github.io/sync-media-pub/incorporating-synchronized-narration.html
Editors:
Marisa DeMeglio (DAISY Consortium)
Daniel Weck (DAISY Consortium)
Participate:
GitHub w3c/sync-media-pub
File a bug
Commit history
Pull requests
Copyright © 2019-2020 the Contributors to the Incorporating Synchronized Narration into a Publication Manifest Specification, published by the Synchronized Media for Publications Community Group under the W3C Community Contributor License Agreement (CLA). A human-readable summary is available.

Abstract

This document provides a draft version of Incorporating Synchronized Narration into a Publication Manifest.

Status of This Document

This specification was published by the Synchronized Media for Publications Community Group. It is not a W3C Standard nor is it on the W3C Standards Track. Please note that under the W3C Community Contributor License Agreement (CLA) there is a limited opt-out and other conditions apply. Learn more about W3C Community and Business Groups.

This draft is still under consideration within the Synchronized Media for Publications Community Group and is subject to change. The most prominent issues will be referenced in the document with links provided.

If you wish to make comments regarding this document, please send them to public-sync-media-pub@w3.org (subscribe, archives).

Table of Contents

1. Introduction
1.1 Terminology
2. Specification
2.1 Inclusion in a Publication Manifest
2.2 Publication Manifest Examples
A. References
A.1 Informative references
1. Introduction

The Synchronized Narration document covers how to associate Synchronized Narration with an HTML document, by pointing to it from within the HTML document itself. This document shows how to incorporate Synchronized Narration at the Publication Manifest level. Reasons for wanting to do this include:

The primary resource with which Synchronized Narration is being associated may be an audio file and cannot contain a reference to an external document.
It is more convenient for Reading Systems to discover alternative formats at the manifest level rather than to introspect every HTML document.
1.1 Terminology

Terms with meanings specific to the publishing industry are capitalized in this document (e.g., "Reading System"). A complete list of these terms and definitions is provided in [wpub].

Only the first instance of a term in a section is linked to its definition.

In addition, the following terminology is defined for use in this specification:

Issue #16: add packaging terminology

VOCAB
TODO: what terms do we need to define that are specific to incorporation into web publications?
2. Specification

2.1 Inclusion in a Publication Manifest

ISSUE 1
Issue #15: clarify packaging rules
A Synchronized Narration document may be associated with a reading order entry in a Publication Manifest. This is done by creating a LinkedResource object for the Synchronized Narration document and adding it to the reading order entry's alternate property:


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
A synchronized narration document is a LinkedResource and uses the following properties:

duration: as in Audiobooks
encodingFormat: [application/vnd.syncnarr+json](narration.html#mimetype)
readBy: as in Audiobooks
url: as in pub manifest
2.2 Publication Manifest Examples

This section is non-normative.

ISSUE 2
Issue #17: Add more manifest examples
Audiobook

An audio book can add Synchronized Media resources to enable phrase-by-phrase playback:


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
Multi-document web publication

This is a hypothetical example based on TODO


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
A. References

A.1 Informative references

[wpub]
Web Publications. Matt Garrish; Ivan Herman. W3C. 13 August 2019. W3C Note. URL: https://www.w3.org/TR/wpub/
↑