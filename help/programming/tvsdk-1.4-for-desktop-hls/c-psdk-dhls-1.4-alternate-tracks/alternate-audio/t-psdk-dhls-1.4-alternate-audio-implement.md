---
description: 遅延バインディングオーディオでは、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生に MediaPlayer が使用されます。
title: 代替オーディオトラックへのアクセス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオでは、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生に MediaPlayer が使用されます。

1. 待機： `MediaPlayer` 少なくとも PREPARED ステータスになっている。
1. 次のイベントをリッスンします。

   * `MediaPlayerItemEvent.ITEM_CREATED`：オーディオトラックの初期リストを使用できます。
   * `MediaPlayerItemEvent.AUDIO_UPDATED`：再生中に変更されたオーディオトラック

1. 使用可能なオーディオトラックを `MediaPlayerItem` インスタンス。
1. （オプション）使用可能なトラックをユーザーに提示します。
1. 選択したオーディオトラックを `MediaPlayerItem` インスタンス。
