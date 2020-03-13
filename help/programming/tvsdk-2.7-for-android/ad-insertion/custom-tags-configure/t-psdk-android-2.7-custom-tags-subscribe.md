---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: 9f74b2b9-bbc9-433c-8226-2c2b68eddf7e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

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

