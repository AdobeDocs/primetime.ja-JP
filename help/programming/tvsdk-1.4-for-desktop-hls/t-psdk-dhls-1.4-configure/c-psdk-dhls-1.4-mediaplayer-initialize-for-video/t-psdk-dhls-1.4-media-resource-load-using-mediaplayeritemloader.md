---
description: メディアリソースを解決するもう 1 つの方法は、 MediaPlayerItemLoader を使用することです。 これは、MediaPlayer インスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
title: MediaPlayerItemLoader を使用したメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# MediaPlayerItemLoader を使用したメディアリソースの読み込み{#load-a-media-resource-using-mediaplayeritemloader}

メディアリソースを解決するもう 1 つの方法は、 MediaPlayerItemLoader を使用することです。 これは、MediaPlayer インスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

を通じて `MediaPlayerItemLoader` クラスを使用すると、メディアリソースを `MediaPlayerItem` にビューを取り付けずに `MediaPlayer` インスタンスを使用して、ビデオデコーディングハードウェアリソースを割り当てます。 を取得するプロセス `MediaPlayerItem` インスタンスは非同期です。

1. これらのイベントリスナーの実装 `MediaPlayerItemLoader` イベント：

   * `MediaPlayerItemLoaderEvent.ERROR` イベント

     TVSDK は、この値を使用して、エラーが発生したことをアプリケーションに通知します。 TVSDK は、診断情報を含むエラープロパティを提供します。

1. このインスタンスをに登録 `MediaPlayerItemLoader`.
1. 通話 `DefaultMediaPlayerItemLoader.load`を渡し、 `MediaResource` オブジェクト。

   の URL `MediaResource` オブジェクトは、情報を取得するストリームを指している必要があります。 例：

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
