---
description: TVSDK は、コンテンツマニフェストでこれらのオブジェクトを検出するたびに、サブスクライブされたタグの PTTimedMetadata オブジェクトを準備します。
title: カスタムタグを購読
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# カスタムタグを購読 {#subscribe-to-custom-tags}

TVSDK は、コンテンツマニフェストでこれらのオブジェクトを検出するたびに、サブスクライブされたタグの PTTimedMetadata オブジェクトを準備します。

再生が開始される前に、タグを購読する必要があります。
HLS マニフェスト内のカスタムタグに関する通知を受け取るには：

1. カスタムタグを含む配列をに渡して、カスタム広告タグ名をグローバルに設定します。 `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >次を含める必要があります： `#` プレフィックスを使用して、HLS ストリームを操作する場合に使用します。

   例：

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
