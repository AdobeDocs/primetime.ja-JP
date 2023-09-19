---
description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEvent をリッスンします。
title: 時間指定メタデータ通知のリスナーを追加する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# 時間指定メタデータ通知のリスナーを追加する{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEvent をリッスンします。

新しい `TimedMetadata` オブジェクトが作成された場合、MediaPlayer がディスパッチします。 `AdobePSDK.TimedMetadataEvent`.

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

ID3 メタデータが同じ `Events.TimedMetadataEvent`. 以下を使用すると、 `timedMetadata.type` プロパティを使用して、TAG と ID3 を区別します。
