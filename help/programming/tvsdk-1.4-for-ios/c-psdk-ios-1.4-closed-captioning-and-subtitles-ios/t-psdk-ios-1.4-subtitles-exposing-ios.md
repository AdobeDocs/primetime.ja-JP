---
description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を知らせます。
seo-description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を知らせます。
seo-title: サブタイトルを表示する
title: サブタイトルを表示する
uuid: 657ab9c7-b205-4d13-81a7-51bc8e7d5ee2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# サブタイトル{#expose-subtitles}を公開する

TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を知らせます。

`PTMediaPlayerItem`プロパティの`subtitlesOptions`を通じて、使用可能なサブタイトルにアクセスできます。

サブタイトルを公開するには：

1. クライアントを`PTMediaPlayerMediaSelectionOptionsAvailableNotification`通知のリスナーとして登録します。

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   クライアントがこの通知を受け取ると、サブタイトルは`PTMediaPlayerItem`に準備されます。
1. 次の例のような`onMediaPlayerItemMediaSelectionOptionsAvailable`メソッドを実装します。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   代替オーディオトラックについて詳しくは、[代替オーディオ](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md)を参照してください。