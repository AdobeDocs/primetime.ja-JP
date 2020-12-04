---
description: StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。
seo-description: StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。
seo-title: StageVideoが使用可能かどうかを確認します。
title: StageVideoが使用可能かどうかを確認します。
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---


# StageVideoが使用可能かどうかを確認します{#check-whether-stagevideo-is-available}

StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。

Flash15以降では、ハードウェア`StageVideo`が使えない場合は、ソフトウェア`StageVideo`に戻ります。 Flash14以前では、`StageVideo`が使用可能かどうかを判断できます。 `StageVideo`が利用できない場合は、`StageVideoAvailabilityEvent`を使用して利用できない理由を理解できます。

1. `StageVideoAvailabilityEvent`をリッスンして、`StageVideo`が利用可能かどうかを判断します。

   例：

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. `StageVideo`が利用できない場合は、`flash.media.StageVideoAvailabilityReason`をチェックします。
