---
description: StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。
title: StageVideoが使用可能かどうかを確認します。
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 1%

---


# StageVideoが使用可能かどうかを確認します{#check-whether-stagevideo-is-available}

StageVideoが使用できない場合に、アプリケーションがStageVideoを使用しようとすると、TVSDKはエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEventをリッスンすることで、StageVideoが使用可能かどうかを判断できます。

Flash15以降では、ハードウェア`StageVideo`が使えない場合は、ソフトウェア`StageVideo`に戻ります。 Flash14以前では、`StageVideo`が使用可能かどうかを判断できます。 `StageVideo`が利用できない場合は、`StageVideoAvailabilityEvent`を使って利用できない理由を理解できます。

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
