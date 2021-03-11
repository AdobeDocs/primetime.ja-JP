---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
title: メディアリソースをMediaPlayerに読み込む
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# メディアリソースをMediaPlayer {#load-a-media-resource-in-the-mediaplayer}に読み込む

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。

1. `MediaPlayer`オブジェクトの再生可能な項目を、再生する新しいリソースで設定します。

   `replaceCurrentResource`を呼び出し、既存の`MediaResource`インスタンスを渡すことで、既存の`MediaPlayer`オブジェクトの現在の再生可能な項目を置き換えます。

1. ブラウザーTVSDKが`AdobePSDK.MediaPlayerStatusChangeEvent`をディスパッチするまで待ちます。`event.status`は、次のいずれかに等しく、

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      これらのイベントを通じて、MediaPlayerオブジェクトは、メディアリソースが正常に読み込まれたかどうかをアプリケーションに通知します。

1. メディアプレイヤーの状態が`MediaPlayerStatus.INITIALIZED`に変わったら、`MediaPlayer.prepareToPlay`を呼び出すことができます。

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 `prepareToPlay`開始を呼び出すと、広告解決と配置プロセスが発生します（存在する場合）。
1. ブラウザーTVSDKが`MediaPlayerStatus.PREPARED`イベントをディスパッチすると、メディアストリームが正常に読み込まれ（MediaPlayerItemが作成されます）、再生の準備が行われます。

エラーが発生した場合、`MediaPlayer`は`MediaPlayerStatus.ERROR`に切り替わります。

また、`MediaPlayerStatus.ERROR`イベントをディスパッチして、アプリケーションに通知します。

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。

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
