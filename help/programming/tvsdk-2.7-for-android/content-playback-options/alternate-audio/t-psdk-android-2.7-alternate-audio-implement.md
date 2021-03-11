---
description: 代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
title: 代替オーディオトラックへのアクセス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
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

