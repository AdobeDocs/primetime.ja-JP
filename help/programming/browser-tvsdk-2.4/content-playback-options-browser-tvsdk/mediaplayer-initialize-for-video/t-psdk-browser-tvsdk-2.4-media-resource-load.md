---
description: MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
title: MediaPlayer でのメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# MediaPlayer でのメディアリソースの読み込み {#load-a-media-resource-in-the-mediaplayer}

MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。

1. を `MediaPlayer` 再生する新しいリソースを含むオブジェクトの再生可能な項目。

   既存の `MediaPlayer` を呼び出すことにより、オブジェクトの現在再生可能な項目 `replaceCurrentResource` そして既存の `MediaResource` インスタンス。

1. Browser TVSDK がディスパッチするのを待ちます。 `AdobePSDK.MediaPlayerStatusChangeEvent` 次を使用 `event.status` これは、次のいずれかと等しくなります。

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

     これらのイベントを通じて、 MediaPlayer オブジェクトはメディアリソースが正常に読み込まれたかどうかをアプリケーションに通知します。

1. メディアプレーヤーの状態が `MediaPlayerStatus.INITIALIZED`を呼び出すと、 `MediaPlayer.prepareToPlay`.

   INITIALIZED 状態は、メディアが正常に読み込まれたことを示します。 呼び出し `prepareToPlay` 広告の解決および配置プロセスを開始します（存在する場合）。
1. ブラウザー TVSDK が `MediaPlayerStatus.PREPARED` イベントは、メディアストリームが正常に読み込まれ（MediaPlayerItem が作成されます）、再生の準備が整います。

エラーが発生した場合、 `MediaPlayer` に切り替えます。 `MediaPlayerStatus.ERROR`.

また、 `MediaPlayerStatus.ERROR` イベント。

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

以下に、メディアリソースの読み込みプロセスを簡略化したサンプルコードを示します。

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                        onStatusChange); 
 
onStatusChange = function (event) { 
    var msg = ""; 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            msg = "Player Status: INITIALIZED"; 
            console.log(msg); 
            player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
        // The resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback. 
        // Once the resource is loaded, the MediaPlayer can 
        // provide a reference to the current "playable item" 
           MediaPlayerItem playerItem = player.currentItem; 
           if (playerItem != null) {  
              // here we can look at the properties of the  
              // loadedstream 
           } 
           break; 
    } 
}
```
