---
description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を知らせます。
seo-description: TVSDKは、PTMediaPlayerMediaSelectionOptionsAvailableNotification通知を使用して、プレイヤークライアントに内部AVAssetのavailableMediaCharacteristicsWithMediaSelectionOptionsの可用性を知らせます。
seo-title: サブタイトルを表示する
title: サブタイトルを表示する
uuid: 1cd8761f-6e6f-4017-9852-fa61f36197c5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
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

   代替オーディオトラックについて詳しくは、[代替オーディオ](../../alternate-audio/ios-3x-alternate-audio.md)を参照してください。