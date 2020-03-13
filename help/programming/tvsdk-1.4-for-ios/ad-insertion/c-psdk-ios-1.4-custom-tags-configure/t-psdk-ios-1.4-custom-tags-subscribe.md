---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのPTTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのPTTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: de66d3db-46d1-485f-9d3a-6e28495bfb13
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタムタグのサブスクライブ {#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのPTTimedMetadataオブジェクトを準備します。

再生を開始する前に、タグをサブスクライブする必要があります。
HLSマニフェストのカスタムタグに関する通知を受け取るには：

1. カスタムタグを含む配列をに渡して、カスタム広告タグ名をグローバルに設定し `setSubscribedTags` ます `PTSDKConfig`。

   >[!IMPORTANT]
   >
   >HLSストリームを使用する場合は、 `#` プレフィックスを含める必要があります。

   例：

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```

