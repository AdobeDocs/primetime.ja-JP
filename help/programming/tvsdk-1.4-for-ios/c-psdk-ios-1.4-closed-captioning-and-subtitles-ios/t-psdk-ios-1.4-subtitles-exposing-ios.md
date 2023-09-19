---
description: TVSDK は、 PTMediaPlayerMediaSelectionOptionsAvailableNotification 通知を使用して、内部 AVAsset の availableMediaCharacteristicsWithMediaSelectionOptions が使用可能であることをプレーヤークライアントに通知します。
title: サブタイトルを公開
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# サブタイトルを公開 {#expose-subtitles}

TVSDK は、 PTMediaPlayerMediaSelectionOptionsAvailableNotification 通知を使用して、内部 AVAsset の availableMediaCharacteristicsWithMediaSelectionOptions が使用可能であることをプレーヤークライアントに通知します。

使用可能なサブタイトルには、 `PTMediaPlayerItem` プロパティの `subtitlesOptions`.

サブタイトルを公開するには：

1. クライアントをのリスナーとして登録します。 `PTMediaPlayerMediaSelectionOptionsAvailableNotification` 通知。

   ```
   [[NSNotificationCenter defaultCenter]  
     addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
     name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player];
   ```

   クライアントがこの通知を受け取ると、サブタイトルは `PTMediaPlayerItem`.
1. の実装 `onMediaPlayerItemMediaSelectionOptionsAvailable` 次の例のようなメソッドを使用します。

   ```
   - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification *) notification { 
       NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions; 
       NSArray* audioOptions = self.player.currentItem.audioOptions; 
   }
   ```

   代替オーディオトラックについて詳しくは、  [代替オーディオ](../alternate-audio/c-psdk-ios-1.4-alternate-audio.md).
