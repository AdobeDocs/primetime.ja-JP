---
description: MediaPlayerItemLoader を使用すると、 MediaPlayer インスタンスをインスタンス化しなくても、メディアストリームに関する情報を取得できます。 これは、遅延なく再生が開始できるよう、プリバッファリングストリームで特に役立ちます。
title: MediaPlayerItemLoader を使用したメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# MediaPlayerItemLoader を使用したメディアリソースの読み込み {#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoader を使用すると、 MediaPlayer インスタンスをインスタンス化しなくても、メディアストリームに関する情報を取得できます。 これは、遅延なく再生が開始できるよう、プリバッファリングストリームで特に役立ちます。

The `MediaPlayerItemLoader` クラスは、現在の `MediaPlayerItem` にビューを取り付けずに `MediaPlayer` インスタンス。ビデオのデコードハードウェアリソースを割り当てます。 DRM で保護されたコンテンツには追加の手順が必要ですが、このマニュアルでは説明しません。

>[!IMPORTANT]
>
>TVSDK は、単一の `QoSProvider` 両者を相手に働く `itemLoader` および `MediaPlayer`. アプリケーションがインスタントオンを使用する場合、アプリケーションは 2 つを維持する必要があります。 `QoS` インスタンスと両方のインスタンスを管理します。 詳しくは、 [即時オン](../../android-3x-content-playback-options-android2/buffering-configuration/android-3x-instant-on.md) を参照してください。

1. のインスタンスを作成 `MediaPlayerItemLoader`.

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
   >の別のインスタンスを作成 `MediaPlayerItemLoader` リソースごとに 使用しない `MediaPlayerItemLoader` インスタンスを使用して、複数のリソースを読み込みます。

1. の実装 `ItemLoaderListener` から通知を受け取るクラス `MediaPlayerItemLoader` インスタンス。

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

   Adobe Analytics の `onLoadComplete()` callback、次のいずれかの操作を行います。

   * WebVTT やオーディオトラックの選択など、バッファリングに影響を与える可能性があるすべてが完了していることを確認し、を呼び出します。 `prepareBuffer()` 即座に利用する
   * 項目を `MediaPlayer` を使用してインスタンスを作成する `replaceCurrentItem()`.

   を呼び出す場合 `prepareBuffer()`に値を指定する場合、 `onBufferPrepared` ハンドラーを使用します。
1. 通話 `load` の `MediaPlayerItemLoader` 読み込むリソース、（オプションで）コンテンツ ID、および `MediaPlayerItemConfig` インスタンス。

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. ストリームの先頭以外のポイントからバッファリングするには、を呼び出します。 `prepareBuffer()` バッファリングを開始する位置（ミリ秒）を指定します。
1. 以下を使用します。 `replaceCurrentItem()` および `play()` ～の方法 `MediaPlayer` その時点から遊び始める
1. アイドル状態になってから、 `replaceCurrentItem`.
1. 項目を再生します。

   * 項目が読み込まれ、バッファされていない場合：

      1. 初期化済みステータスを待ちます。
      1. 通話 `prepareToPlay()`.
      1. PREPARED ステータスが表示されるまで待ちます。
      1. 通話 `play()`.

   * アイテムがバッファされる場合：

      1. バッファー準備イベントを待ちます。
      1. 通話 `play()`.
