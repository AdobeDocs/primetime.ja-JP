---
description: 代替オーディオでは、 MediaPlayer を使用して、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
title: 代替オーディオトラックへのアクセス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

代替オーディオでは、 MediaPlayer を使用して、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. 待機： `MediaPlayer` 少なくとも内に居る `MediaPlayerStatus.PREPARED` ステータス。
1. をリッスンします。 `MediaPlayerEvent.STATUS_CHANGED` ステータスのイベント `MediaPlayerStatus.PREPARED`.

   このステップは、オーディオトラックの初期リストが使用可能であることを意味します。

1. 使用可能なオーディオトラックを `MediaPlayerItem` インスタンス。

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. （オプション）使用可能なトラックをユーザーに提示します。
1. 選択したオーディオトラックを `MediaPlayerItem` インスタンス。

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
