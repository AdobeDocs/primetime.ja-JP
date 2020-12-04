---
description: 遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-description: 遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。
seo-title: 代替オーディオトラックへのアクセス
title: 代替オーディオトラックへのアクセス
uuid: 2915a74f-5ec3-457e-890d-5c79be39f37a
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 代替オーディオトラックにアクセス{#access-alternate-audio-tracks}

遅延バインディングオーディオは、PTMediaPlayerを使用して、M3U8 HLSプレイリストで指定され、複数の代替オーディオストリームを含むことができるビデオを再生します。

1. MediaPlayerが`PTMediaPlayerStatusReady`ステータス以上になるまで待ちます。
1. このイベントをリッスンします。

   通知`PTMediaPlayerItemMediaSelectionOptionsAvailable`:オーディオトラックの初期リストを使用できます。

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self 
        selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:) 
        name:PTMediaPlayerItemMediaSelectionOptionsAvailable  
        object:self.player];
   ```

1. `PTMediaPlayerItem`インスタンスから使用可能なオーディオトラックを取得します。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

1. （オプション）使用可能なトラックをユーザーに表示します。
1. 選択したオーディオトラックを`PTMediaPlayerItem`インスタンスに設定します。
