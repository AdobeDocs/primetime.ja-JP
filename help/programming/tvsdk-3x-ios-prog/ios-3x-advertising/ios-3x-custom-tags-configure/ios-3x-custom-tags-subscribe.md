---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのPTTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのPTTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: e47076b2-6184-4c20-bae4-ba7ae62cf198
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

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
