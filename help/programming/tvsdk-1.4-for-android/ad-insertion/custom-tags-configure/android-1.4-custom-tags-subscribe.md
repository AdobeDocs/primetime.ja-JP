---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: fe8ba34d-66fc-43bb-b98e-659c1702d1e0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタムタグのサブスクライブ{#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。

再生を開始する前に、タグをサブスクライブする必要があります。
HLSマニフェストのカスタムタグに関する通知を受け取るには：

カスタムタグを含む配列をに渡して、カスタム広告タグ名をグローバルに設定し `setSubscribedTags` ます `MediaPlayerItemConfig`。

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

