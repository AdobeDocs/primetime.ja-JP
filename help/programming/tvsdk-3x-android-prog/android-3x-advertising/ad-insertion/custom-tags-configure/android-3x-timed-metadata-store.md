---
description: アプリケーションは、適切なTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。
seo-description: アプリケーションは、適切なTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。
seo-title: ディスパッチ時の時間指定メタデータオブジェクトの格納
title: ディスパッチ時の時間指定メタデータオブジェクトの格納
uuid: 3d0ed022-829d-474e-83a9-152caeb5b317
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# ディスパッチ時の時間指定メタデータオブジェクトの保存{#store-timed-metadata-objects-as-they-are-dispatched}

アプリケーションは、適切なTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。

再生前に発生するコンテンツ解析中に、TVSDKはサブスクライブされたタグを識別し、これらのタグをアプリケーションに通知します。

>[!TIP]
>
>各`TimedMetadata`に関連付けられる時間は、再生タイムライン上のローカル時間です。

ディスパッチ時の時間指定メタデータオブジェクトを保存するには：

1. 現在の再生時間を追跡します。
1. 現在の再生時間を、ディスパッチされた`TimedMetadata`オブジェクトと一致させます。

1. `TimedMetadata`は、開始時間が現在のローカル再生時間と等しい場合に使用します。

   次の例は、`ArrayList`内に`TimedMetadata`オブジェクトを保存する方法を示しています。

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

