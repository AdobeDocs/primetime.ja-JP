---
description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を通知します。
seo-description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を通知します。
seo-title: サブタイトルの公開
title: サブタイトルの公開
uuid: 657ab9c7-b205-4d13-81a7-51bc8e7d5ee2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

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

   代替オーディオトラックについて詳しくは、代替オーディオを [参照してくださ](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md)い。