---
description: 代替オーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むビデオの再生にMediaPlayerを使用します。
seo-description: 代替オーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むビデオの再生にMediaPlayerを使用します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 09aa00e9-0cbf-4f5b-9652-ce514f6e2f38
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

代替オーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むビデオの再生にMediaPlayerを使用します。

1. が少なくともス `MediaPlayer` テータスになるまで待 `MediaPlayerStatus.PREPARED` ちます。
1. ステータスでイベント `MediaPlayerEvent.STATUS_CHANGED` をリッスンしま `MediaPlayerStatus.PREPARED`す。

   この手順は、オーディオトラックの初期リストが使用可能であることを意味します。

1. 使用可能なオーディオトラックをインスタンスから取 `MediaPlayerItem` 得します。

   ```java
   mediaPlayerItem.getAudioTracks()
   ```

1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックをインスタンスに設 `MediaPlayerItem` 定します。

   ```java
   mediaPlayerItem.selectAudioTrack(audioTrack)
   ```
