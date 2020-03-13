---
description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
seo-description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
seo-title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
uuid: a7ec8f58-7357-4757-a402-e879dd6caec8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayerItemLoaderを使用したメディアリソースの読み込み{#load-a-media-resource-using-mediaplayeritemloader}

メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

クラスを通 `MediaPlayerItemLoader` じて、インスタンスにビューをアタッチしなくても、メディアリソー `MediaPlayerItem` スと対応するリソースを交換できます。これにより、ビデオデコード `MediaPlayer` のハードウェアリソースが割り当てられます。 インスタンスを取得するプロ `MediaPlayerItem` セスは非同期です。

1. 次のイベントのイベントリスナーを実装 `MediaPlayerItemLoader` します。

   * `MediaPlayerItemLoaderEvent.ERROR` event

      TVSDKは、これを使用して、エラーが発生したことをアプリケーションに通知します。 TVSDKは、診断情報を含むエラープロパティを提供します。

1. このインスタンスをに登録しま `MediaPlayerItemLoader`す。
1. を呼び出 `DefaultMediaPlayerItemLoader.load`し、オブジェクトのインスタンスを渡 `MediaResource` します。

   オブジェクトのURL `MediaResource` は、情報を取得するストリームを指し示す必要があります。 例：

   ```
   private function onLoadError(event:MediaPlayerItemLoaderEvent):void { 
       // something went wrong - look at the error code and description 
       // contained within the event.error 
   } 
   private function onLoadCompleted(event:MediaPlayerItemLoaderEvent):void { 
       // information is available - look at the data in the "event.item" object 
   } 
   // instantiate the MediaPlayerItemLoader object and register event listeners 
   var itemLoader:MediaPlayerItemLoader = new DefaultMediaPlayerItemLoader(); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.ERROR, onLoadError); 
   itemLoader.addEventListener(MediaPlayerItemLoaderEvent.COMPLETED, onLoadCompleted); 
   // create the MediaResource instance and set the URL to point to the actual media stream 
   var mediaResource:MediaResource = 
     MediaResource.createFromURL("https://example.com/media/test_media.m3u8", null); 
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```

