---
description: TVSDK は、コンテンツマニフェストでこれらのオブジェクトを検出するたびに、サブスクライブされたタグの TimedMetadata オブジェクトを準備します。
title: カスタムタグを購読
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# カスタムタグを購読{#subscribe-to-custom-tags}

TVSDK は、コンテンツマニフェストでこれらのオブジェクトを検出するたびに、サブスクライブされたタグの TimedMetadata オブジェクトを準備します。

再生が開始される前に、タグを購読する必要があります。
タグをサブスクライブするには、カスタムタグ名を含むベクトルをに割り当てます。 `subscribedTags` プロパティ。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を含むベクトルをに割り当てます。 `adTags` プロパティ。

HLS マニフェスト内のカスタムタグに関する通知を受け取るには：

1. カスタムタグを含むベクトルをに割り当てることで、カスタム広告タグ名をグローバルに設定します。 `subscribeTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >次を含める必要があります： `#` プレフィックスを使用して、HLS ストリームを操作する場合に使用します。

   例：

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. デフォルトのオポチュニティジェネレーターが使用する広告タグをグローバルに変更するには、カスタム広告タグ名を含むベクトルをに割り当てます。 `adTags` プロパティ： `PSDKConfig`.

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. すべてのグローバル設定を有効にするには、現在のリソースを置き換えます。

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. ストリームのサブスクライブ済みタグ名を設定するには、必要に応じて次の手順を実行します。
   1. メディアプレーヤーアイテム設定を作成します。

      >[!TIP]
      >
      >最も簡単な方法は、デフォルトのメディアプレーヤーアイテム設定を作成することです。

   1. カスタムタグを含むベクトルをに割り当てる `subscribeTags` in `MediaPlayerItemConfig`.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. 指定されたストリーム内のデフォルトのオポチュニティジェネレーターが使用する広告タグを変更するには、カスタム広告タグ名を含むベクトルをに割り当てます。 `adTags` プロパティ： `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. ストリームに対する変更を有効にするには、メディアストリームの読み込み時に、メディアプレーヤーアイテム設定を使用します。

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
