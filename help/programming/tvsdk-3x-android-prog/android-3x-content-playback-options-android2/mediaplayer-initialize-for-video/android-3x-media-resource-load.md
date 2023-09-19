---
description: MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。
title: メディアプレーヤーへのメディアリソースの読み込み
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# メディアプレーヤーへのメディアリソースの読み込み {#load-a-media-resource-in-the-media-player}

MediaResource を直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースの読み込み方法の 1 つです。

1. 新しいリソースを再生するメディアプレーヤーを設定します。

   を呼び出して、現在再生可能な項目を置き換える `MediaPlayer.replaceCurrentResource()` そして既存の `MediaResource` インスタンス。

   リソースの読み込みプロセスが開始されます。

1. を登録します。 `MediaPlayerEvent.STATUS_CHANGED` イベント `MediaPlayer` インスタンス。 このコールバックで、少なくとも次のステータス値を確認します。

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   これらのイベントを通じて、 `MediaPlayer` オブジェクトは、メディアリソースが正常に読み込まれた場合に、アプリケーションに通知します。
1. メディアプレーヤーのステータスが `INITIALIZED`を呼び出すと、 `MediaPlayer.prepareToPlay()`.

   このステータスは、メディアが正常に読み込まれたことを示します。 新しい `MediaPlayerItem` は再生の準備ができています。 呼び出し `prepareToPlay()` 広告の解決および配置プロセスを開始します（存在する場合）。

エラーが発生した場合、メディアプレーヤーは `ERROR` ステータス。

以下に、メディアリソースの読み込みプロセスを簡略化したサンプルコードを示します。

```java>
// mediaResource is a properly configured MediaResource instance 
// mediaPlayer is a MediaPlayer instance 
// register a PlaybackEventListener implementation with the MediaPlayer instance 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatus status) { 
        if(event.getStatus() == MediaPlayerStatus.PREPARED) { 
            // The resource is successfully loaded and available. The  
            // MediaPlayer is ready to start the playback and can 
            // provide a reference to the current playable item 
            MediaPlayerItem playerItem = mediaPlayer.getCurrentItem(); 
            if (playerItem != null) { 
                // We can look at the properties of the loaded stream 
            } 
        } 
        else if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            //Something bad happened - the resource cannot be loaded. 
            // The Metadata object in the event provides details. 
        } 
        else if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
    } 
} 
```
