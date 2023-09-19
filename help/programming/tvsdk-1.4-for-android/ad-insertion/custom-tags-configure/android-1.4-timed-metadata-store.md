---
description: アプリケーションでは、適切な TimedMetadata オブジェクトを適切なときに使用する必要があります。
title: ディスパッチされる時間指定メタデータオブジェクトを保存します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# ディスパッチされる時間指定メタデータオブジェクトを保存します {#store-timed-metadata-objects-as-they-are-dispatched}

アプリケーションでは、適切な TimedMetadata オブジェクトを適切なときに使用する必要があります。

再生前に発生するコンテンツ解析中に、 TVSDK はサブスクライブされているタグを識別し、これらのタグに関してアプリケーションに通知します。 各 `TimedMetadata` は、再生タイムラインのローカル時間です。

アプリケーションは、次のタスクを実行する必要があります。

1. 現在の再生時間を追跡します。
1. 現在の再生時間とディスパッチ済みの時間を一致させる `TimedMetadata` オブジェクト。

1. 以下を使用します。 `TimedMetadata` ここで、開始時間は現在のローカル再生時間と等しくなります。

   次の例は、 `TimedMetadata` 内のオブジェクト `ArrayList`.

   ```java
   private List<TimedMetadata> _timedMetadataList = new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```
