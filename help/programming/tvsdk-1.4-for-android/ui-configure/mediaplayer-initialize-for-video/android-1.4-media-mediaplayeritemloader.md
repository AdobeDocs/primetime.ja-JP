---
description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
seo-description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
seo-title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
uuid: b2311ddc-f059-4775-8553-fc354ec2636b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerItemLoaderを使用したメディアリソースの読み込み {#load-a-media-resource-using-mediaplayeritemloader}

メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

クラスを通 `MediaPlayerItemLoader` じて、インスタンスにビューをアタッチしなくても、メディアリソー `MediaPlayerItem` スと対応するリソースを交換できます。これにより、ビデオデコード `MediaPlayer` のハードウェアリソースが割り当てられます。 インスタンスを取得するプロ `MediaPlayerItem` セスは非同期です。

1. コールバックインターフェ `MediaPlayerItemLoader.LoaderListener` イスを実装します。

       このインターフェイスは、次の2つのメソッドを定義します。
   
   * `LoaderListener.onError` コールバック関数

      TVSDKは、これを使用して、エラーが発生したことをアプリケーションに通知します。 TVSDKは、エラーコードをパラメーターとして提供し、診断情報を含む説明文字列を提供します。

   * `LoaderListener.onError` コールバック関数

      TVSDKは、これを使用して、要求された情報が、コールバックのパラメーターとして渡されるインスタンスの形式で利用でき `MediaPlayerItem` ることをアプリケーションに通知します。

1. このインスタンスを、のコンストラクターにパラメーターとして渡すことで、TVSDKに登録しま `MediaPlayerItemLoader`す。
1. を呼び出 `MediaPlayerItemLoader.load`し、オブジェクトのインスタンスを渡 `MediaResource` します。

   オブジェクトのURL `MediaResource` は、情報を取得するストリームを指し示す必要があります。 例：

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

