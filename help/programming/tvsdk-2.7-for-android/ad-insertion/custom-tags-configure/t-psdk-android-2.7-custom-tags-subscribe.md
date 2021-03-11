---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。
title: カスタムタグのサブスクライブ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---


# カスタムタグを登録{#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。

再生開始の前に、タグをサブスクライブする必要があります。 HLSマニフェストのカスタムタグに関する通知を受け取るには：

1. カスタムタグを含む配列を`MediaPlayerItemConfig`の`setSubscribedTags`に渡して、カスタム広告タグ名をグローバルに設定します。

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

