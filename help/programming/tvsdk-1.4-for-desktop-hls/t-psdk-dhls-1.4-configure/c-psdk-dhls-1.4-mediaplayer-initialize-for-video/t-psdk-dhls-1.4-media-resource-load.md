---
description: MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。
title: MediaPlayer でのメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# MediaPlayer でのメディアリソースの読み込み{#load-a-media-resource-in-the-mediaplayer}

MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。

1. を `MediaPlayer` 再生する新しいリソースを含むオブジェクトの再生可能な項目。

   を呼び出して、既存の MediaPlayer の現在再生可能な項目を置き換えます。 `MediaPlayer.replaceCurrentResource` そして既存の `MediaResource` インスタンス。

1. 少なくとも次の変更を確認してください。

   * 初期化済み
   * 準備済み
   * エラー

     これらのイベントを通じて、 `MediaPlayer` オブジェクトは、メディアリソースが正常に読み込まれたときにアプリケーションに通知できます。

1. メディアプレーヤーの状態が INITIALIZED に変わったら、を呼び出すことができます。 `MediaPlayer.prepareToPlay`

   INITIALIZED 状態は、メディアが正常に読み込まれたことを示します。 呼び出し `prepareToPlay` 広告の解決および配置プロセスを開始します（存在する場合）。

1. メディアプレーヤーのステータスが「準備済み」に変わると、メディアストリームは正常に読み込まれ、再生の準備が整います。

   メディアストリームが読み込まれると、 `MediaPlayerItem` が作成されました。

エラーが発生した場合、 MediaPlayer は ERROR ステータスに切り替わります。 また、 `STATUS_CHANGED` イベントに `MediaPlayerStatusChangeEvent` コールバック。

これには、次の複数のパラメーターが渡されます。
* A `type` 値を持つ文字列型のパラメーター `ERROR`.

* A `MediaError` エラーイベントに関する診断情報を含む通知を取得するために使用できるパラメーター。


<!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

以下に、メディアリソースの読み込みプロセスを簡略化したサンプルコードを示します。

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
