---
description: メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}を使用したメディアリソースの読み込み

メディアリソースを解決する別の方法は、MediaPlayerItemLoaderを使用する方法です。 これは、MediaPlayerインスタンスをインスタンス化せずに、特定のメディアストリームに関する情報を取得する場合に役立ちます。

`MediaPlayerItemLoader`クラスを通じて、`MediaPlayer`インスタンスに表示を割り当てることなく、対応する`MediaPlayerItem`とメディアリソースを交換できます。その結果、ビデオデコーディングハードウェアリソースが割り当てられます。 `MediaPlayerItem`インスタンスを取得するプロセスは非同期です。

1. `MediaPlayerItemLoader.LoaderListener`コールバックインターフェイスを実装します。

       このインターフェイスは、次の2つのメソッドを定義します。
   
   * `LoaderListener.onError` コールバック関数

      TVSDKは、このメソッドを使用して、エラーが発生したことをアプリケーションに通知します。 TVSDKは、エラーコードをパラメーターとして提供し、診断情報を含む説明文字列を提供します。

   * `LoaderListener.onError` コールバック関数

      TVSDKは、このメソッドを使用して、要求された情報がコールバックに対するパラメーターとして渡される`MediaPlayerItem`インスタンスの形式で利用できることをアプリケーションに知らせます。

1. このインスタンスを`MediaPlayerItemLoader`のコンストラクターにパラメーターとして渡して、TVSDKに登録します。
1. `MediaPlayerItemLoader.load`を呼び出し、`MediaResource`オブジェクトのインスタンスを渡します。

   `MediaResource`オブジェクトのURLは、情報を取得するストリームを指している必要があります。 例：

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

