---
description: 遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。
seo-description: 遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 136b4f1b-e56f-4a8a-a961-05193434558c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。

1. がPREPAREDステータ `MediaPlayer` ス以上になるまで待ちます。
1. 以下のイベントをリッスンします。

   * `MediaPlayerItemEvent.ITEM_CREATED`:オーディオトラックの初期リストを使用できます。
   * `MediaPlayerItemEvent.AUDIO_UPDATED`:再生中に変更されたオーディオトラック

1. 使用可能なオーディオトラックをインスタンスから取 `MediaPlayerItem` 得します。
1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックをインスタンスに設 `MediaPlayerItem` 定します。
