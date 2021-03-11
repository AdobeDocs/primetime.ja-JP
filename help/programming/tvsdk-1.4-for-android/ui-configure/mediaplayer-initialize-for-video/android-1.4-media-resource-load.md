---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。
title: メディアリソースをMediaPlayerに読み込む
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# メディアリソースをMediaPlayer {#load-a-media-resource-in-the-mediaplayer}に読み込む

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。

1. 再生する新しいリソースをMediaPlayerの再生可能な項目に設定します。

   `MediaPlayer.replaceCurrentItem`を呼び出し、既存の`MediaResource`インスタンスを渡すことで、既存のMediaPlayerの現在再生可能なアイテムを置き換えます。

1. `MediaPlayer.PlaybackEventListener`インターフェイスの実装を`MediaPlayer`インスタンスに登録します。

   * `onPrepared`
   * `onStateChanged`に値を入力し、INITIALIZEDとERRORを確認します。

1. メディアプレイヤーの状態がINITIALIZEDに変わった場合は、`MediaPlayer.prepareToPlay`を呼び出すことができます

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 `prepareToPlay`開始を呼び出すと、広告解決と配置プロセスが発生します（存在する場合）。

1. TVSDKが`onPrepared`コールバックを呼び出すと、メディアストリームの読み込みが成功し、再生の準備が整います。

   メディアストリームが読み込まれると、`MediaPlayerItem`が作成されます。

>エラーが発生した場合、`MediaPlayer`はERRORステータスに切り替わります。 また、`PlaybackEventListener.onStateChanged`コールバックを呼び出すことで、アプリケーションに通知します。
>
>これは、次のいくつかのパラメーターを渡します。
>* `MediaPlayer.PlayerState.ERROR`の値を持つタイプ`MediaPlayer.PlayerState`の`state`パラメータ。
   >
   >
* エラーイベントに関する診断情報を含む、タイプ`MediaPlayerNotification`の`notification`パラメーター。


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
