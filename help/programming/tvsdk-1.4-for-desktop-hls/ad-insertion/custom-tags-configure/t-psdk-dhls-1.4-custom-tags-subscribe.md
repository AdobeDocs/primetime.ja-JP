---
description: TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。
title: カスタムタグのサブスクライブ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# カスタムタグのサブスクライブ{#subscribe-to-custom-tags}

TVSDKは、サブスクライブされたタグがコンテンツマニフェスト内で検出されるたびに、そのタグのTimedMetadataオブジェクトを準備します。

再生開始の前に、タグをサブスクライブする必要があります。
タグをサブスクライブするには、カスタムタグ名を格納しているベクトルを`subscribedTags`プロパティに割り当てます。 デフォルトのオポチュニティジェネレーターが使用する広告タグも変更する必要がある場合は、カスタム広告タグ名を格納しているベクトルを`adTags`プロパティに割り当てます。

HLSマニフェストのカスタムタグに関する通知を受け取るには：

1. カスタムタグを含むベクトルを`MediaPlayerItemConfig`の`subscribeTags`に割り当てて、カスタム広告タグ名をグローバルに設定します。

   >[!IMPORTANT]
   >
   >HLSストリームを操作する場合は、`#`プレフィックスを含める必要があります。

   例：

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. デフォルトのオポチュニティジェネレーターが使用する広告タグをグローバルに変更するには、カスタム広告タグ名を格納しているベクトルを`PSDKConfig`の`adTags`プロパティに割り当てます。

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
   1. メディアプレイヤーアイテム設定を作成します。

      >[!TIP]
      >
      >最も簡単な方法は、デフォルトのメディアプレイヤーアイテム設定を作成することです。

   1. カスタムタグを含むベクトルを`MediaPlayerItemConfig`の`subscribeTags`に割り当てます。

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. 指定したストリームのデフォルトのオポチュニティジェネレーターが使用する広告タグを変更するには、カスタム広告タグ名を格納しているベクトルを`mediaPlayerItemConfig`の`adTags`プロパティに割り当てます

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. ストリームに対する変更を有効にするには、メディアストリームを読み込むときに、メディアプレイヤーアイテム設定を使用します。

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

