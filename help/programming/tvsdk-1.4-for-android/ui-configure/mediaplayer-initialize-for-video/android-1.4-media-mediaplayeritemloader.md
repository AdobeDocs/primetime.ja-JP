---
description: メディアリソースを解決するもう 1 つの方法は、 MediaPlayerItemLoader を使用することです。 これは、MediaPlayer インスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
title: MediaPlayerItemLoader を使用したメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# MediaPlayerItemLoader を使用したメディアリソースの読み込み {#load-a-media-resource-using-mediaplayeritemloader}

メディアリソースを解決するもう 1 つの方法は、 MediaPlayerItemLoader を使用することです。 これは、MediaPlayer インスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

を通じて `MediaPlayerItemLoader` クラスを使用すると、メディアリソースを `MediaPlayerItem` にビューを取り付けずに `MediaPlayer` インスタンスを使用して、ビデオデコーディングハードウェアリソースを割り当てます。 を取得するプロセス `MediaPlayerItem` インスタンスは非同期です。

1. の実装 `MediaPlayerItemLoader.LoaderListener` コールバックインターフェイス。

       このインターフェイスは、次の 2 つのメソッドを定義します。
   
   * `LoaderListener.onError` コールバック関数

     TVSDK は、この値を使用して、エラーが発生したことをアプリケーションに通知します。 TVSDK は、エラーコードをパラメーターとして提供し、診断情報を含む説明文字列を提供します。

   * `LoaderListener.onError` コールバック関数

     TVSDK は、この情報を使用して、リクエストされた情報が `MediaPlayerItem` コールバックにパラメーターとして渡されるインスタンス。

1. このインスタンスを、TVSDK のコンストラクターにパラメーターとして渡して、TVSDK に登録します。 `MediaPlayerItemLoader`.
1. 通話 `MediaPlayerItemLoader.load`を渡し、 `MediaResource` オブジェクト。

   の URL `MediaResource` オブジェクトは、情報を取得するストリームを指している必要があります。 例：

   ```java
   // instantiate the listener interface 
   MediaPlayerItemLoader.LoaderListener _itemLoaderListener = 
     new MediaPlayerItemLoader.LoaderListener() { 
       @Override 
       public void onError(MediaErrorCode mediaErrorCode, String description) { 
           // something went wrong - look at the error code and description 
       } 
       @Override 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
           // information is available - look at the data in the "playerItem" object 
       } 
   } 
   
   // instantiate the MediaPlayerItemLoader object (pass the listener as parameter) 
   MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(_itemLoaderListener); 
   
   // create the MediaResource instance and set the URL to point to the actual media stream 
   MediaResource mediaResource =  
     MediaResource.createFromUrl("https://test.com/test_media.m3u8", null); 
   
   // load the media resource 
   itemLoader.load(mediaResource); 
   ```
