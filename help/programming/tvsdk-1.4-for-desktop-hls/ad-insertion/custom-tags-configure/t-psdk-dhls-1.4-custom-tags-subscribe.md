---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-description: TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。
seo-title: カスタムタグのサブスクライブ
title: カスタムタグのサブスクライブ
uuid: 43480265-4951-466a-a347-6debfb6935ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタムタグのサブスクライブ{#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェストで検出されるたびに、サブスクライブされたタグのTimedMetadataオブジェクトを準備します。

再生を開始する前に、タグをサブスクライブする必要があります。
タグをサブスクライブするには、カスタムタグ名を含むベクトルをプロパティに割り当 `subscribedTags` てます。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を含むベクトルをプロパティに割り当て `adTags` ます。

HLSマニフェストのカスタムタグに関する通知を受け取るには：

1. カスタムタグを含むベクトルをに割り当てて、カスタム広告タグ名をグローバルに設定 `subscribeTags` しま `MediaPlayerItemConfig`す。

   >[!IMPORTANT]
   >
   >HLSストリームを使用する場合は、 `#` プレフィックスを含める必要があります。

   例：

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. デフォルトのオポチュニティジェネレーターが使用する広告タグをグローバルに変更するには、カスタム広告タグ名を含むベクトルをのプロパティに `adTags` 割り当てま `PSDKConfig`す。

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. すべてのグローバル設定を有効にするには、現在のリソースを置き換えます。

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. 必要に応じて、ストリームのサブスクライブ済みタグ名を設定するには：
   1. メディアプレイヤー項目の設定を作成します。

      >[!TIP]
      >
      >最も簡単な方法は、デフォルトのメディアプレイヤー項目設定を作成することです。

   1. カスタムタグを含むベクトルをに割り当て `subscribeTags` ます `MediaPlayerItemConfig`。

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. 指定したストリームのデフォルトのオポチュニティジェネレーターが使用する広告タグを変更するには、カスタム広告タグ名を含むベクトルを、 `adTags``mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. ストリームに対する変更を有効にするには、メディアストリームを読み込むときに、メディアプレイヤー項目の設定を使用します。

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

