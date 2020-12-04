---
description: 代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-description: 代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 9cec3a00-1416-497d-8d16-0ee429c8b575
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---


# 代替オーディオトラックにアクセス{#access-alternate-audio-tracks}

代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. `MediaPlayer`が少なくとも`MediaPlayerStatus.PREPARED`ステータスになるのを待ちます。
1. `MediaPlayerEvent.STATUS_CHANGED`イベントをリッスンします。ステータスは`MediaPlayerStatus.PREPARED`です。

   この手順は、オーディオトラックの初期リストが使用可能であることを意味します。

1. `MediaPlayerItem`インスタンスから使用可能なオーディオトラックを取得します。

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックを`MediaPlayerItem`インスタンスに設定します。

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```

