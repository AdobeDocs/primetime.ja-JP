---
description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# MediaPlayerItemLoader{#load-a-media-resource-using-mediaplayeritemloader}を使用したメディアリソースの読み込み

メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

`MediaPlayerItemLoader`クラスを通じて、`MediaPlayer`インスタンスに表示を割り当てることなく、対応する`MediaPlayerItem`とメディアリソースを交換できます。その結果、ビデオデコーディングハードウェアリソースが割り当てられます。 `MediaPlayerItem`インスタンスを取得するプロセスは非同期です。

1. 以下の`MediaPlayerItemLoader`イベント用にイベントリスナーを実装します。

   * `MediaPlayerItemLoaderEvent.ERROR` イベント

      TVSDKは、このメソッドを使用して、エラーが発生したことをアプリケーションに通知します。 TVSDKは、診断情報を含むエラープロパティを提供します。

1. このインスタンスを`MediaPlayerItemLoader`に登録します。
1. `DefaultMediaPlayerItemLoader.load`を呼び出し、`MediaResource`オブジェクトのインスタンスを渡します。

   `MediaResource`オブジェクトのURLは、情報を取得するストリームを指している必要があります。 例：

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

