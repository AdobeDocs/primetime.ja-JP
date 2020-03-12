---
description: 遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。
seo-description: 遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: c7060022-29ec-43c1-811b-41cca5f5356c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオは、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオの再生にMediaPlayerを使用します。

1. MediaPlayerがPREPARED状態になるまで待ちます。
1. このイベントをリッスンします。

   `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`:オーディオトラックの初期リストを使用できます。

1. 使用可能なオーディオトラックをインスタンスから取 `MediaPlayerItem` 得します。

   `mediaPlayerItem.getAudioTracks()`1.（オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックをインスタンスに設 `MediaPlayerItem` 定します。

   `mediaPlayerItem.selectAudioTrack(audioTrack)`