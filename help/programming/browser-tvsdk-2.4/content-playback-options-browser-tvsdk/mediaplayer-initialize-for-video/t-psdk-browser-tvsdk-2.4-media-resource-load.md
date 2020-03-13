---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
seo-description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。
seo-title: MediaPlayerへのメディアリソースの読み込み
title: MediaPlayerへのメディアリソースの読み込み
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# MediaPlayerへのメディアリソースの読み込み {#load-a-media-resource-in-the-mediaplayer}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。

1. オブジェクト `MediaPlayer` の再生可能な項目を、再生する新しいリソースで設定します。

   既存のインスタンスを呼 `MediaPlayer` び出して渡すことで、既存のオブジェクトの現在再 `replaceCurrentResource` 生可能な項目を置き換 `MediaResource` えます。

1. 次のいずれかと等しい値で、ブラウ `AdobePSDK.MediaPlayerStatusChangeEvent` ザーTVSDK `event.status` がディスパッチされるのを待ちます。

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      これらのイベントを通じて、MediaPlayerオブジェクトは、メディアリソースが正常に読み込まれたかどうかをアプリケーションに通知します。

1. メディアプレイヤーの状態がに変わったら、 `MediaPlayerStatus.INITIALIZED`を呼び出すことができま `MediaPlayer.prepareToPlay`す。

   INITIALIZED状態は、メディアが正常に読み込まれたことを示します。 を呼び出す `prepareToPlay` と、広告の解決および配置プロセスが開始されます（存在する場合）。
1. ブラウザーTVSDKが、メディアスト `MediaPlayerStatus.PREPARED` リームが正常に読み込まれ（MediaPlayerItemが作成され）、再生の準備が完了したイベントをディスパッチするとき。

障害が発生した場合は、に切 `MediaPlayer` り替わります `MediaPlayerStatus.ERROR`。

また、イベントをディスパッチすることで、アプリケーションに通知 `MediaPlayerStatus.ERROR` します。

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。

>```js>
>player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
>                                               onStatusChange); 
> 
>
onStatusChange = function (event) { 
>       var msg = ""; 
>       switch (event.status) { 
>               case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
>                       msg = "Player Status: INITIALIZED"; 
>                       console.log(msg); 
>                       player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
>                       break; 
> 
>        
       case AdobePSDK.MediaPlayerStatus.PREPARED: 
>               // The resource is successfully loaded and available 
>               // and the MediaPlayer is ready to start the playback. 
>               // Once the resource is loaded, the MediaPlayer can 
>               // provide a reference to the current "playable item" 
>                     MediaPlayerItem playerItem = player.currentItem; 
>                     if (playerItem != null) {  
>                           // here we can look at the properties of the  
>                           // loadedstream 
>                     } 
>                     break; 
>       } 
>}
>```>


