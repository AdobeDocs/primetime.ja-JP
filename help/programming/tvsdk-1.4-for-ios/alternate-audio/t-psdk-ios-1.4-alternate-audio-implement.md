---
description: 遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-description: 遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 77e39633-bf17-4a06-a2a1-93fdaadedd17
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 代替オーディオトラックへのアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. MediaPlayerが少なくともステータスになるまで待ち `PTMediaPlayerStatusReady` ます。
1. このイベントをリッスンします。

   通知 `PTMediaPlayerItemMediaSelectionOptionsAvailable`:オーディオトラックの初期リストを使用できます。

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. 使用可能なオーディオトラックをインスタンスから取 `PTMediaPlayerItem` 得します。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックをインスタンスに設 `PTMediaPlayerItem` 定します。
