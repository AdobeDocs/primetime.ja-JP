---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-title: MediaPlayerへのメディアリソースの読み込み
title: MediaPlayerへのメディアリソースの読み込み
uuid: 8af3e8d1-359d-483c-b394-b95054f7265a
translation-type: tm+mt
source-git-commit: 84924d84bfa436a8807c2e8d74d1dc268d457051

---


# MediaPlayerへのメディアリソースの読み込み{#load-a-media-resource-in-the-mediaplayer}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。

1. オブジェクト `MediaPlayer` の再生可能な項目を、再生する新しいリソースで設定します。

   既存のインスタンスを呼び出して渡すことで、既存のMediaPlayerの現在再生可能な `MediaPlayer.replaceCurrentResource` 項目を置き換 `MediaResource` えます。

1. 少なくとも次の変更を確認します。

   * INITIALIZED
   * PREPARED
   * エラー

      これらのイベントを通じて、メディ `MediaPlayer` アリソースが正常に読み込まれたことをオブジェクトがアプリケーションに通知できます。

1. メディアプレイヤーの状態がINITIALIZEDに変わった場合、 `MediaPlayer.prepareToPlay`

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 広告の解 `prepareToPlay` 決と配置プロセス（ある場合）を開始に呼び出します。

1. メディアプレイヤーのステータスがPREPAREDに変わると、メディアストリームは正常に読み込まれ、再生の準備が整います。

   メディアストリームが読み込まれると、が作 `MediaPlayerItem` 成されます。

障害が発生した場合、MediaPlayerはERRORステータスに切り替わります。 また、コールバックにイベントを送出することで、アプリケ `STATUS_CHANGED` ーションに通 `MediaPlayerStatusChangeEvent` 知します。

これは、次のいくつかのパラメータを渡します。
* 値を持 `type` つstring型のパラメータ `ERROR`ー。

* エラー `MediaError` 情報に関する診断情報を含む通知を取得するために使用できるイベント。


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
