---
description: MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、再生を遅延なく開始できるように、バッファリング前のストリームで特に便利です。
seo-description: MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、再生を遅延なく開始できるように、バッファリング前のストリームで特に便利です。
seo-title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
uuid: 504063af-1dd4-4268-88e7-ad5a247fdff7
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}を使用したメディアリソースの読み込み

MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、再生を遅延なく開始できるように、バッファリング前のストリームで特に便利です。

`MediaPlayerItemLoader`クラスは、ビデオデコーディングハードウェアリソースを割り当てる表示を`MediaPlayer`インスタンスに割り当てることなく、メディアリソースを現在の`MediaPlayerItem`と交換するのに役立ちます。 DRM保護されたコンテンツには、追加の手順が必要ですが、本マニュアルではそれらの手順について説明しません。

>[!IMPORTANT]
>
>TVSDKは、1つの`QoSProvider`をサポートせず、`itemLoader`と`MediaPlayer`の両方で動作します。 アプリケーションが即時オンを使用する場合、アプリケーションは2つの`QoS`インスタンスを維持し、情報の両方のインスタンスを管理する必要があります。 詳しくは、[即時オン](../../android-3x-content-playback-options-android2/buffering-configuration/android-3x-instant-on.md)を参照してください。

1. `MediaPlayerItemLoader`のインスタンスを作成します。

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
   
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
   
           public void onBufferingBegin() { 
               //Do something 
           } 
   
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       }); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   } 
   ```

   >[!TIP]
   >
   >各リソースに対して`MediaPlayerItemLoader`の個別のインスタンスを作成します。 1つの`MediaPlayerItemLoader`インスタンスを使用して複数のリソースを読み込まないでください。

1. `ItemLoaderListener`クラスを実装して、`MediaPlayerItemLoader`インスタンスから通知を受信します。

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
           public void onBufferingBegin() { 
               //Do something 
           } 
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       } ); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   }
   ```

   `onLoadComplete()`コールバックで、次のいずれかを実行します。

   * WebVTTやオーディオトラックの選択など、バッファリングに影響を与える可能性のあるものがすべて完了していることを確認し、`prepareBuffer()`を呼び出して即時オンを利用します。
   * `replaceCurrentItem()`を使用して、`MediaPlayer`インスタンスにアイテムをアタッチします。

   `prepareBuffer()`を呼び出すと、準備が完了した時に`onBufferPrepared`ハンドラにBUFFER_PREPAREDイベントを受け取ります。
1. `MediaPlayerItemLoader`インスタンスで`load`を呼び出し、読み込むリソースと、必要に応じてコンテンツIDと`MediaPlayerItemConfig`インスタンスを渡します。

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. ストリームの先頭以外のポイントからバッファリングするには、バッファリングを開始する位置（ミリ秒）で`prepareBuffer()`を呼び出します。
1. `replaceCurrentItem()`メソッドと`play()`メソッドを使用して、`MediaPlayer`の再生を開始します。
1. アイドル状態を待って`replaceCurrentItem`を呼び出します。
1. 項目を再生します。

   * アイテムがロードされるがバッファリングされない場合：

      1. 初期化済みの状態を待機します。
      1. `prepareToPlay()`を呼び出します。
      1. PREPAREDステータスが表示されるのを待ちます。
      1. `play()`を呼び出します。
   * アイテムがバッファリングされている場合：

      1. バッファー準備イベントを待ちます。
      1. `play()`を呼び出します。