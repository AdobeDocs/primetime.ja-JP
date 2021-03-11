---
description: 遅延バインディングオーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
title: 代替オーディオトラックへのアクセス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. `MediaPlayer`がPREPAREDステータスになるまで待ちます。
1. 以下のイベントをリッスンします。

   * `MediaPlayerItemEvent.ITEM_CREATED`:オーディオトラックの初期リストを使用できます。
   * `MediaPlayerItemEvent.AUDIO_UPDATED`:再生中に変更されたオーディオトラック

1. `MediaPlayerItem`インスタンスから使用可能なオーディオトラックを取得します。
1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックを`MediaPlayerItem`インスタンスに設定します。
