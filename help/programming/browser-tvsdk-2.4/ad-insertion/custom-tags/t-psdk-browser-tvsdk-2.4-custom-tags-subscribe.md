---
description: ブラウザーTVSDKは、サブスクライブされたタグがメディアプレゼンテーション記述(MPD)ファイルで検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。
title: カスタム広告タグのサブスクライブ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# カスタム広告タグ{#subscribe-to-custom-ad-tags}にサブスクライブ

ブラウザーTVSDKは、サブスクライブされたタグがメディアプレゼンテーション記述(MPD)ファイルで検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。

再生開始の前にタグをサブスクライブする必要があります。
タグをサブスクライブするには、カスタムタグ名を格納するベクトルを`subscribedTags`プロパティに設定します。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を格納するベクトルを`adTags`プロパティに設定します。

カスタムタグをサブスクライブするには：

1. 新しいメディアプレイヤーアイテム設定を作成します。

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. 空の文字列ベクトルを作成します。

   ```js
   var subscribeTags = [];
   ```

1. 追加カスタムタグの名前をこのベクトルにします。

   >[!IMPORTANT]
   >
   >HLSストリームを扱う場合は、`#`プレフィックスを必ず含めてください。

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. 更新したベクトルを`mediaPlayerItemConfig.subscribeTags`プロパティに割り当てます。

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. 空の文字列ベクトルを作成します。

   ```js
   var adTags= [];
   ```

1. こ追加のベクトルのカスタム広告タグ名。

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. 更新したベクトルを`mediaPlayerItemConfig.adTags`プロパティに割り当てます。

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. メディアストリームを読み込む際は、メディアプレイヤーアイテム設定を使用します。

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

