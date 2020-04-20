---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-title: MediaPlayerへのメディアリソースの読み込み
title: MediaPlayerへのメディアリソースの読み込み
uuid: 6ee8032f-0728-423f-a1d2-5030aa7db14f
translation-type: tm+mt
source-git-commit: 4ef05be045334a2e723da4c7c6a7ee22fb0f776c

---


# MediaPlayerへのメディアリソースの読み込み {#load-a-media-resource-in-the-mediaplayer}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。

1. 再生する新しいリソースをMediaPlayerの再生可能な項目に設定します。

   既存のインスタンスを呼び出して渡すことで、既存のMediaPlayerの現在再生可能な `MediaPlayer.replaceCurrentItem` 項目を置き換 `MediaResource` えます。

1. インターフェイスの実装をイ `MediaPlayer.PlaybackEventListener` ンスタンスに登録 `MediaPlayer` します。

   * `onPrepared`
   * `onStateChanged`に設定され、INITIALIZEDとERRORを確認します。

1. メディアプレイヤーの状態がINITIALIZEDに変わった場合、 `MediaPlayer.prepareToPlay`

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 広告の解 `prepareToPlay` 決と配置プロセス（ある場合）を開始に呼び出します。

1. TVSDKがコールバックを呼び出す `onPrepared` と、メディアストリームは正常に読み込まれ、再生の準備が整います。

   メディアストリームが読み込まれると、が作 `MediaPlayerItem` 成されます。

>障害が発生した場合は、ERROR `MediaPlayer` ステータスに切り替わります。 また、コールバックを呼び出すことで、アプリケーションに通知 `PlaybackEventListener.onStateChanged`します。
>
>これは、次のいくつかのパラメータを渡します。
>* の値 `state` を持つタ `MediaPlayer.PlayerState` イプのパラメータ `MediaPlayer.PlayerState.ERROR`。
   >
   >
* エラー `notification` 情報に関する `MediaPlayerNotification` 診断情報を含むタイプのイベント。


以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。

```java
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer  
instancemediaPlayer.addEventListener( 
  MediaPlayer.Event.PLAYBACK, 
  new MediaPlayer.PlaybackEventListener()) { 
    @Overridepublic void onPrepared() { 
        // at this point, the resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback 
        // once the resource is loaded, the MediaPlayer is able to 
        // provide a reference to the current "playable item" 
 
        MediaPlayerItem playerItem = mediaPlayer.CurrentItem(); 
 
        if (playerItem != null) {     
            // here we can take a look at the properties of the     
            // loaded stream 
        } 
    } @Overridepublic void onStateChanged( 
        MediaPlayer.PlayerState state,  
        MediaPlayerNotification notification) { 
        if (state == MediaPlayer.PlayerState.ERROR) { 
            // something bad happened - the resource cannot be loaded    
            // details about the problem are provided via the  
            // MediaPlayerNotification instance 
        }  
        elseif (state == MediaPlayer.PlayerState.INITIALIZED) {     
            mediaPlayer.prepareToPlay(); 
        } 
    } 
    // implementation of the other methods in the PlaybackEventListener interface... 
} 
```
