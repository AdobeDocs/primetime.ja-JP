---
description: StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。
seo-description: StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。
seo-title: StageVideoが使用可能かどうかを確認します。
title: StageVideoが使用可能かどうかを確認します。
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# StageVideoが使用可能かどうかを確認します。{#check-whether-stagevideo-is-available}

StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。

Flash 15以降では、ハードウェアが使用で `StageVideo` きない場合、ソフトウェアに戻ります `StageVideo`。 Flash 14以前の場合は、が使用可能かどうかを判断 `StageVideo` できます。 が使用で `StageVideo` きない場合は、を使用して、使用でき `StageVideoAvailabilityEvent` ない理由を理解することができます。

1. をリッスンし `StageVideoAvailabilityEvent` て、使用可能かど `StageVideo` うかを判断します。

   例：

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. が使用で `StageVideo` きない場合は、チェックしま `flash.media.StageVideoAvailabilityReason`す。
