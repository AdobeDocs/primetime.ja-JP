---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。
title: メディアリソースをMediaPlayerに読み込む
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# メディアリソースをMediaPlayer{#load-a-media-resource-in-the-mediaplayer}に読み込む

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。

1. `MediaPlayer`オブジェクトの再生可能な項目を、再生する新しいリソースで設定します。

   `MediaPlayer.replaceCurrentResource`を呼び出し、既存の`MediaResource`インスタンスを渡すことで、既存のMediaPlayerの現在再生可能なアイテムを置き換えます。

1. 少なくとも次の変更を確認します。

   * INITIALIZED
   * PREPARED
   * ERROR

      これらのイベントを通じて、`MediaPlayer`オブジェクトは、メディアリソースが正常に読み込まれたことをアプリケーションに通知できます。

1. メディアプレイヤーの状態がINITIALIZEDに変わった場合は、`MediaPlayer.prepareToPlay`を呼び出すことができます

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 `prepareToPlay`開始を呼び出すと、広告解決と配置プロセスが発生します（存在する場合）。

1. メディアプレイヤーのステータスがPREPAREDに変わった場合、メディアストリームの読み込みが成功し、再生の準備が整います。

   メディアストリームが読み込まれると、`MediaPlayerItem`が作成されます。

エラーが発生した場合は、MediaPlayerのステータスがERRORに切り替わります。 また、`STATUS_CHANGED`イベントを`MediaPlayerStatusChangeEvent`コールバックにディスパッチすることで、アプリケーションに通知します。

これは、次のいくつかのパラメーターを渡します。
* 値`ERROR`を持つタイプ文字列の`type`パラメータ。

* エラーイベントに関する診断情報を含む通知を取得するために使用できる`MediaError`パラメーター。


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。

```
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register an event listener with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
   switch(event.status) { 
      case MediaPlayerStatus.INITIALIZED: 
          // at this point, the resource is successfully loaded 
          // the media player will provide a reference to the current 
          // "playable item" ( is guarantee to be valid and not-null). 
          var playerItem: MediaPlayerItem = mediaPlayer.currentItem; 
          // we can take a look at the media item characteristics like 
          // alternate audio tracks, profile information, if is a live stream 
          // if is drm protected 
          mediaPlayer.prepareToPlay(); 
          break; 
    case MediaPlayerStatus.PREPARED: 
         // at this point, the resource is successfully processed all  
         // advertisement placements have been executed and the the  
         // MediaPlayer is ready to start the playback 
        if (autoPlay) { 
            mediaPlayer.play(); 
        } 
        break; 
    case MediaPlayerStatus.ERROR: 
        // something bad happened - the resource cannot be loaded 
        // details about the problem are provided via the event.error property 
        break; 
        // implementation of the other methods in the PlaybackEventListener interface 
        ... 
    } 
}
```
