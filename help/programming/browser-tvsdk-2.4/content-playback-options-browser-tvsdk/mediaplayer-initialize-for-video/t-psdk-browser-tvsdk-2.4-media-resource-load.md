---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
seo-description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
seo-title: メディアリソースをMediaPlayerに読み込む
title: メディアリソースをMediaPlayerに読み込む
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 7d61a6cd8cb2c381f85a19d9ccac3d235ffceaf1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# メディアリソースをMediaPlayerに読み込む {#load-a-media-resource-in-the-mediaplayer}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。

1. 再生する新しいリソースで `MediaPlayer` オブジェクトの再生可能な項目を設定します。

   既存の `MediaPlayer` インスタンスを呼び出して渡すことで、既存の `replaceCurrentResource` オブジェクトの現在再生可能な項目 `MediaResource` を置き換えます。

1. 次のいずれかと等しい値 `AdobePSDK.MediaPlayerStatusChangeEvent` を持つブラウザーTVSDKがディスパッチ `event.status` されるまで待ちます。

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      これらのイベントを通じて、MediaPlayerオブジェクトは、メディアリソースが正常に読み込まれたかどうかをアプリケーションに通知します。

1. メディアプレイヤーの状態がに変わった場合 `MediaPlayerStatus.INITIALIZED`、を呼び出すことができ `MediaPlayer.prepareToPlay`ます。

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 広告の解決および配置プロセスがある場合は、 `prepareToPlay` 開始を呼び出します。
1. ブラウザーTVSDKが、メディアストリームの読み込みが成功した（MediaPlayerItemが作成された） `MediaPlayerStatus.PREPARED` イベントをディスパッチし、再生の準備を行う。

エラーが発生した場合は、に `MediaPlayer` 切り替わり `MediaPlayerStatus.ERROR`ます。

また、 `MediaPlayerStatus.ERROR` イベントをディスパッチして申込書に通知します。

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
