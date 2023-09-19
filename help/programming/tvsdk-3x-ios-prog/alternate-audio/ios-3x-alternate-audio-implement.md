---
description: 遅延バインディングオーディオでは、 PTMediaPlayer を使用して、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
title: 代替オーディオトラックへのアクセス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# 代替オーディオトラックへのアクセス {#access-alternate-audio-tracks}

遅延バインディングオーディオでは、 PTMediaPlayer を使用して、M3U8 HLS プレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. MediaPlayer が少なくとも `PTMediaPlayerStatusReady` ステータス。
1. このイベントをリッスンします。

   通知 `PTMediaPlayerItemMediaSelectionOptionsAvailable`：オーディオトラックの初期リストを使用できます。

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. 使用可能なオーディオトラックを `PTMediaPlayerItem` インスタンス。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. （オプション）使用可能なトラックをユーザーに提示します。
1. 選択したオーディオトラックを `PTMediaPlayerItem` インスタンス。
