---
description: アプリケーションは、適切な時間に適切なTimedMetadataオブジェクトを使用する必要があります。
seo-description: アプリケーションは、適切な時間に適切なTimedMetadataオブジェクトを使用する必要があります。
seo-title: ディスパッチ時の時間指定メタデータオブジェクトの格納
title: ディスパッチ時の時間指定メタデータオブジェクトの格納
uuid: 0d0ddfea-6f32-467d-91bc-f18ceadcd842
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# ディスパッチ時の時間指定メタデータオブジェクトの格納 {#store-timed-metadata-objects-as-they-are-dispatched}

アプリケーションは、適切な時間に適切なTimedMetadataオブジェクトを使用する必要があります。

再生前に発生するコンテンツの解析中に、TVSDKはサブスクライブされたタグを識別し、これらのタグをアプリケーションに通知します。

>[!TIP]
>
>各時間に関連付けられる時間は、再 `TimedMetadata` 生タイムライン上のローカル時間です。

ディスパッチ時の時間指定メタデータオブジェクトを保存するには：

1. 現在の再生時間を追跡します。
1. 現在の再生時間を、ディスパッチされるオブジェクトに一致さ `TimedMetadata` せます。

1. 開始時間が現 `TimedMetadata` 在のローカル再生時間と等しい場所を使用します。

   次の例は、内にオブジェクトを保存 `TimedMetadata` する方法を示しま `ArrayList`す。

   ```java
   private List<TimedMetadata> _timedMetadataList =  
     new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```

