---
description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を通知します。
seo-description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を通知します。
seo-title: サブタイトルの公開
title: サブタイトルの公開
uuid: 1cd8761f-6e6f-4017-9852-fa61f36197c5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# サブタイトルの公開 {#expose-subtitles}

TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を通知します。

使用可能なサブタイトルには、プロパティのサブタイト `PTMediaPlayerItem` ルからアクセスできま `subtitlesOptions`す。

サブタイトルを公開するには：

1. クライアントを通知のリスナーとして登録 `PTMediaPlayerMediaSelectionOptionsAvailableNotification` します。

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   クライアントがこの通知を受け取ると、サブタイトルはに準備されま `PTMediaPlayerItem`す。
1. 次の例のよ `onMediaPlayerItemMediaSelectionOptionsAvailable` うなメソッドを実装します。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   代替オーディオトラックについて詳しくは、代替オーディオを [参照してくださ](../../alternate-audio/ios-3x-alternate-audio.md)い。