---
description: MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。
title: MediaPlayer でのメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# MediaPlayer でのメディアリソースの読み込み {#load-a-media-resource-in-the-mediaplayer}

MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。

1. MediaPlayer の再生可能な項目に、再生する新しいリソースを設定します。

   を呼び出して、既存の MediaPlayer の現在再生可能な項目を置き換えます。 `MediaPlayer.replaceCurrentItem` そして既存の `MediaResource` インスタンス。

1. の実装の登録 `MediaPlayer.PlaybackEventListener` とのインターフェイス `MediaPlayer` インスタンス。

   * `onPrepared`
   * `onStateChanged`をクリックし、INITIALIZED と ERROR を確認します。

1. メディアプレーヤーの状態が INITIALIZED に変わったら、を呼び出すことができます。 `MediaPlayer.prepareToPlay`

   INITIALIZED 状態は、メディアが正常に読み込まれたことを示します。 呼び出し `prepareToPlay` 広告の解決および配置プロセスを開始します（存在する場合）。

1. TVSDK が `onPrepared` コールバックの場合、メディアストリームは正常に読み込まれ、再生の準備が整います。

   メディアストリームが読み込まれると、 `MediaPlayerItem` が作成されました。

>エラーが発生した場合、 `MediaPlayer` ERROR ステータスに切り替えます。 また、 `PlaybackEventListener.onStateChanged`コールバック。
>
>これには、次の複数のパラメーターが渡されます。
>* A `state` 型のパラメーター `MediaPlayer.PlayerState` ～の価値を持つ `MediaPlayer.PlayerState.ERROR`.
>
>* A `notification` 型のパラメーター `MediaPlayerNotification` エラーイベントに関する診断情報が含まれている。

以下に、メディアリソースの読み込みプロセスを簡略化したサンプルコードを示します。

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
