---
description: MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、遅延なく再生を開始できるように、プリバッファリングストリームで特に便利です。
seo-description: MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、遅延なく再生を開始できるように、プリバッファリングストリームで特に便利です。
seo-title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
title: MediaPlayerItemLoaderを使用したメディアリソースの読み込み
uuid: 43ca2470-1fd2-4f66-94fe-a12ed17b52d7
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# MediaPlayerItemLoaderを使用したメディアリソースの読み込み {#load-a-media-resource-using-mediaplayeritemloader}

MediaPlayerItemLoaderを使用すると、MediaPlayerインスタンスをインスタンス化することなく、メディアストリームに関する情報を取得できます。 これは、遅延なく再生を開始できるように、プリバッファリングストリームで特に便利です。

このク `MediaPlayerItemLoader` ラスは、ビューをインスタンスにアタッチせずに、メ `MediaPlayerItem` ディアリソースを現在のメディアリソースと交換するのに役立ちます。このインスタ `MediaPlayer` ンスは、ビデオデコードハードウェアリソースを割り当てます。 DRM保護コンテンツには追加の手順が必要ですが、本マニュアルでは説明しません。

>[!IMPORTANT]
>
>TVSDKは、との両方で機能する単一 `QoSProvider` のTVSDKをサポートして `itemLoader` いませ `MediaPlayer`ん。 アプリケーションで即時オンを使用する場合は、2つのインスタンスを維持し、情報の両方のイ `QoS` ンスタンスを管理する必要があります。 詳しく [は、即時オン](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) (instant-on)を参照してください。

1. のインスタンスを作成しま `MediaPlayerItemLoader`す。

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
   >各リソースに対して、の個別のイン `MediaPlayerItemLoader` スタンスを作成します。 複数のリソースを読み込む場合は、1 `MediaPlayerItemLoader` つのインスタンスを使用しないでください。

1. インスタンス `ItemLoaderListener` から通知を受け取るクラスを実装 `MediaPlayerItemLoader` します。

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

   コールバッ `onLoadComplete()` クで、次のいずれかの操作を行います。

   * バッファリングに影響を与える可能性のあるもの（例えば、WebVTTやオーディオトラックの選択）がすべて完了していることを確認し、インスタントオンを `prepareBuffer()` 利用するための呼び出しが実行されるようにします。
   * を使用して、項目をインスタ `MediaPlayer` ンスにアタッチしま `replaceCurrentItem()`す。
   を呼び出すと、 `prepareBuffer()`準備が完了した時点でハンドラにBUFFER_PREPARED `onBufferPrepared` イベントを受け取ります。

1. インスタ `load` ンスを `MediaPlayerItemLoader` 呼び出し、読み込むリソースと、オプションでコンテンツIDとインスタンスを渡 `MediaPlayerItemConfig` します。

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. ストリームの先頭以外のポイントからバッファーするには、バッファーを `prepareBuffer()` 開始する位置（ミリ秒）で呼び出します。
1. との方法を `replaceCurrentItem()` 使用 `play()` して、 `MediaPlayer` その時点から再生を開始します。
1. アイドル状態を待ってから、呼び出しを行いま `replaceCurrentItem`す。
1. 項目を再生します。

   * アイテムが読み込まれているがバッファされていない場合：

      1. 初期化状態を待ちます。
      1. 呼び出し `prepareToPlay()`ます。
      1. PREPAREDステータスが表示されるまで待ちます。
      1. 呼び出し `play()`ます。
   * アイテムがバッファされている場合：

      1. バッファー準備イベントを待ちます。
      1. 呼び出し `play()`ます。