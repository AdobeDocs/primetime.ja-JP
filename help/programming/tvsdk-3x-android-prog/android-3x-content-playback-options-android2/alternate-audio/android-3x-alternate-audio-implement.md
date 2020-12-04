---
description: 代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-description: 代替オーディオは、MediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 09aa00e9-0cbf-4f5b-9652-ce514f6e2f38
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

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
