---
description: StageVideo が使用できない場合に、アプリケーションが StageVideo を使用しようとしても、 TVSDK はエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEvent をリッスンすることで、StageVideo が使用可能かどうかを判断できます。
title: StageVideo が使用可能かどうかを確認します。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# StageVideo が使用可能かどうかを確認します。{#check-whether-stagevideo-is-available}

StageVideo が使用できない場合に、アプリケーションが StageVideo を使用しようとしても、 TVSDK はエラーを発行しません。 アプリケーションは、StageVideoAvailabilityEvent をリッスンすることで、StageVideo が使用可能かどうかを判断できます。

Flash15 以降（ハードウェアの場合） `StageVideo` が使用できない場合は、ソフトウェアに戻ります `StageVideo`. Flash14 以前では、 `StageVideo` が使用可能です。 次の場合 `StageVideo` は使用できません。次を使用できます： `StageVideoAvailabilityEvent` をクリックして、使用できない理由を確認します。

1. 次をリッスン： `StageVideoAvailabilityEvent` ～かどうかを判断する `StageVideo` が使用可能です。

   例：

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. 次の場合 `StageVideo` は使用できません。 `flash.media.StageVideoAvailabilityReason`.
