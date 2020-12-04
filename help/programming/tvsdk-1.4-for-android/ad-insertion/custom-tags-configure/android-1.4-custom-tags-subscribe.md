---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: fe8ba34d-66fc-43bb-b98e-659c1702d1e0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 1%

---


# カスタムタグのサブスクライブ{#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。

再生開始の前に、タグをサブスクライブする必要があります。
HLSマニフェストのカスタムタグに関する通知を受け取るには：

カスタムタグを含む配列を`MediaPlayerItemConfig`の`setSubscribedTags`に渡して、カスタム広告タグ名をグローバルに設定します。

>[!IMPORTANT]
>
>HLSストリームを操作する場合は、`#`プレフィックスを含める必要があります。

例：

```java
String[] array = new String[3]; 
array[0] = "#EXT-X-ASSET"; 
array[1] = "#EXT-X-BLACKOUT"; 
array[2] = "#EXT-OATCLS-SCTE35"; 
MediaPlayerItemConfig.setSubscribedTags(array);
```

