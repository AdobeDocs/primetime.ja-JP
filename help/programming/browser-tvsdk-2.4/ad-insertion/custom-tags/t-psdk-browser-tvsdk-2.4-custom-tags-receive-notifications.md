---
description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。
seo-description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。
seo-title: 時間指定メタデ追加ータ通知のリスナー
title: 時間指定メタデ追加ータ通知のリスナー
uuid: c82c5549-0ab6-4343-a766-5176e784d4cb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# 時間指定メタデ追加ータ通知のリスナー{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。

新しい`TimedMetadata`オブジェクトが作成されると、MediaPlayerは`AdobePSDK.TimedMetadataEvent`をディスパッチします。

1. 適切なリスナーを実装します。

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. イベントリスナーを登録します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

ID3メタデータは、同じ`Events.TimedMetadataEvent`を通じてディスパッチされます。 `timedMetadata.type`プロパティを使用して、TAGとID3を区別できます。

