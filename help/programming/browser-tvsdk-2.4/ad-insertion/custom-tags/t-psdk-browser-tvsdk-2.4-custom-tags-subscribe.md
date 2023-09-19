---
description: ブラウザー TVSDK は、メディアプレゼンテーションの説明 (MPD) ファイルでこれらのオブジェクトが検出されるたびに、サブスクライブされたタグの TimedMetadata オブジェクトを準備します。
title: カスタム広告タグを購読
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# カスタム広告タグを購読{#subscribe-to-custom-ad-tags}

ブラウザー TVSDK は、メディアプレゼンテーションの説明 (MPD) ファイルでこれらのオブジェクトが検出されるたびに、サブスクライブされたタグの TimedMetadata オブジェクトを準備します。

再生を開始する前に、タグを購読する必要があります。
タグをサブスクライブするには、カスタムタグ名を含むベクトルを `subscribedTags` プロパティ。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を含むベクトルをに設定します。 `adTags` プロパティ。

カスタムタグを購読するには：

1. 新しいメディアプレーヤーアイテム設定を作成します。

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. 空の文字列ベクトルを作成します。

   ```js
   var subscribeTags = [];
   ```

1. このベクトルにカスタムタグ名を追加します。

   >[!IMPORTANT]
   >
   >HLS ストリームを扱う場合は、必ず `#` プレフィックス。

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. 更新されたベクトルを `mediaPlayerItemConfig.subscribeTags` プロパティ。

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. 空の文字列ベクトルを作成します。

   ```js
   var adTags= [];
   ```

1. このベクトルにカスタム広告タグ名を追加します。

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. 更新されたベクトルを `mediaPlayerItemConfig.adTags` プロパティ。

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. メディアストリームを読み込む際には、メディアプレーヤーアイテム設定を使用します。

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```
