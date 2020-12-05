# 同步旁白

Synchronized Narration
Draft Community Group Report 24 August 2020

Latest editor's draft:
https://w3c.github.io/sync-media-pub/synchronized-narration.html
Editors:
Marisa DeMeglio (DAISY Consortium)
Daniel Weck (DAISY Consortium)
Participate:
GitHub w3c/sync-media-pub
File a bug
Commit history
Pull requests
Copyright © 2019-2020 the Contributors to the Synchronized Narration Specification, published by the Synchronized Media for Publications Community Group under the W3C Community Contributor License Agreement (CLA). A human-readable summary is available.

Abstract

This document provides a draft version of Synchronized Narration.

Status of This Document

This specification was published by the Synchronized Media for Publications Community Group. It is not a W3C Standard nor is it on the W3C Standards Track. Please note that under the W3C Community Contributor License Agreement (CLA) there is a limited opt-out and other conditions apply. Learn more about W3C Community and Business Groups.

This draft is still under consideration within the Synchronized Media for Publications Community Group and is subject to change. The most prominent issues will be referenced in the document with links provided.

If you wish to make comments regarding this document, please send them to public-sync-media-pub@w3.org (subscribe, archives).

Table of Contents

1. Introduction
1.1 Terminology
2. Specification
2.1 The Synchronized Narration Format
2.1.1 Document Format
2.1.2 Properties
2.1.3 Referencing from an HTML document
2.1.3.1 Linking
2.1.3.2 Playback Styling
2.1.4 User Agent Processing
1. Introduction

Synchronized Narration provides a multimodal reading experience for a document by augmenting the document's primary format (e.g. text) with additional external media (e.g. audio). This augmentation is represented as a series of synchronization points which correlate the different media with each other (e.g. "this audio phrase goes with this HTML paragraph"). This document defines Synchronized Narration for use with standalone HTML documents. However, as this work has been developed with Web Publications as a primary use case, there is an accompanying document called Incorporating Synchronized Narration into a Publication Manifest, which covers integration with publications, such as Audiobooks.

1.1 Terminology

The following terminology is defined for use in this specification:

Audio Clip
A contiguous portion of an audio file, defined by time offsets.

Text Fragment
An element in an HTML document

Playback Styling
Highlight or other style provided for text fragments as they are being played.

Skip
Enable skipping playback of content, based on role. E.g. skip audio playback of page number announcements or footnote references.

Escape
Move playback out of a structure and back into the parent container's sequence. E.g. stop playing a complex table and resume playing main body content.

2. Specification

2.1 The Synchronized Narration Format

2.1.1 Document Format

Synchronized Narration is defined as a JSON document representing the in-order playback of media objects.

No more than one Synchronized Narration document may be associated with an HTML document.

ISSUE 1
Issue #10: mime/media type
A Synchronized Narration document has a media type of application/vnd.syncnarr+json.

2.1.2 Properties

narration
Container for an array of playback objects, each containing media properties.

audio
Media property for audio. Value is a Media Fragment URL that points to an audio resource, referenced via a begin/end tuple of time values, such as audio.mp3#t=123.45,678.9 (see https://www.w3.org/TR/media-frags/#naming-time ).

text
Media property for text. Value is a URL "fragment" which is typically a unique identifier that references a document element (e.g. #section2.3).

ISSUE 2
Issue #11: Define more options for text references
role
Semantic information for a narration container or text/audio pair.

ISSUE 3
Issue #12: role values
ISSUE 4
Issue #9: Define restrictions on parallel media properties
Example of audio and text synchronization:

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
2.1.3 Referencing from an HTML document

2.1.3.1 Linking

<head>
  <link
    rel="sync-media"
    href="sync-media/index.json"
    type="application/vnd.syncnarr+json">
</head>
2.1.3.2 Playback Styling

Playing narration synchronized with HTML content introduces the idea of playback styling, so that authors can provide styling information to reading systems. For example, whenever an HTML element is being "narrated" (i.e. audio playback synchronized with this particular DOM fragment), the reading system injects a CSS class name into this HTML element so that the authored styles are applied dynamically for the currently-playing (aka "active") element.

ISSUE 5
Issue #8: Possible to use pseudoclasses for synchronized highlight?
Here we propose two descriptive properties for playback styling:

css-class-active: Applied to the HTML element whose corresponding audio is being played. Authors may use this to highlight narrated content.
css-class-playing: Applied to the entire HTML document being played. Authors may use this to de-emphasize content that is not currently being narrated.
This recommendation does not specify actual classname values for these properties. Authors must define values as follows:

<head>
  <meta name="sync-media-css-class-active" content="-my-active-element">
  <meta name="sync-media-css-class-playing" content="-my-document-playing">
</head>
The author then defines styles for these classnames in the corresponding CSS:

/* emphasize the active element */
.-my-active-element {
    background-color: yellow;
    color: black !important;
}

/* fade out the inactive text */
html.-my-document-playing * {
    color: gray;
}
2.1.4 User Agent Processing

narration: each object in the array is played in sequence. Media properties on a single object are rendered in parallel.

audio: Play clip from begin to end

text: Render the text by bringing focus to the element in the browser. Apply playback classnames while the element is active.

↑