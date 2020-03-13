---
description: ブラウザーTVSDKは、サブスクライブされたタグがMedia Presentation Description(MPD)ファイルで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-description: ブラウザーTVSDKは、サブスクライブされたタグがMedia Presentation Description(MPD)ファイルで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタム広告タグのサブスクライブ
title: カスタム広告タグのサブスクライブ
uuid: 208f61f4-dc33-4363-aa71-878458740a8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタム広告タグのサブスクライブ{#subscribe-to-custom-ad-tags}

ブラウザーTVSDKは、サブスクライブされたタグがMedia Presentation Description(MPD)ファイルで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。

再生を開始する前に、タグをサブスクライブする必要があります。
タグをサブスクライブするには、カスタムタグ名を含むベクトルをプロパティに設定 `subscribedTags` します。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を含むベクトルをプロパティに設定 `adTags` します。

カスタムタグをサブスクライブするには：

1. 新しいメディアプレイヤー項目の設定を作成します。

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
   >HLSストリームを処理する場合は、プレフィックスを必ず含めてく `#` ださい。

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. 更新したベクトルをプロパティに割り当 `mediaPlayerItemConfig.subscribeTags` てます。

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

1. 更新したベクトルをプロパティに割り当 `mediaPlayerItemConfig.adTags` てます。

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. メディアストリームの読み込み時に、メディアプレイヤー項目の設定を使用します。

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

