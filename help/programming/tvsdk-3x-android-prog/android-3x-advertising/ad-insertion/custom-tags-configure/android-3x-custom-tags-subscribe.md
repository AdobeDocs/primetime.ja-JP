---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: f1a934bd-772e-435f-84b5-cb48db23c06e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# カスタムタグのサブスクライブ {#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。

再生を開始する前に、タグをサブスクライブする必要があります。 HLSマニフェストのカスタムタグに関する通知を受け取るには：

1. カスタムタグを含む配列をに渡して、カスタム広告タグ名をグローバルに設定し `setSubscribedTags` ます `MediaPlayerItemConfig`。

   >[!IMPORTANT]
   >
   >HLSストリームを使用する場合は、 `#` プレフィックスを含める必要があります。

   例：

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```
