---
description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。
title: 時間指定メタデ追加ータ通知のリスナー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
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

