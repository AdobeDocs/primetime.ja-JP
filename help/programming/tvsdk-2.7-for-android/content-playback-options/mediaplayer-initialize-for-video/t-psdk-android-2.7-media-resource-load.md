---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。
title: メディアリソースをメディアプレイヤーに読み込む
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# メディアリソースをメディアプレイヤーに読み込む{#load-a-media-resource-in-the-media-player}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む方法の1つです。

1. 新しいリソースを再生するようにメディアプレイヤーを設定します。

   `MediaPlayer.replaceCurrentResource()`を呼び出し、既存の`MediaResource`インスタンスを渡して、現在再生可能な項目を置き換えます。

   これは、リソースの読み込みプロセスを開始します。

1. `MediaPlayerEvent.STATUS_CHANGED`イベントを`MediaPlayer`インスタンスに登録します。 このコールバックで、少なくとも次のステータス値を確認します。

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`

   これらのイベントを通じて、`MediaPlayer`オブジェクトは、メディアリソースが正常に読み込まれたことをアプリケーションに通知します。
1. メディアプレイヤーのステータスが`INITIALIZED`に変わったら、`MediaPlayer.prepareToPlay()`を呼び出すことができます。

   このステータスは、メディアが正常に読み込まれたことを示します。 新しい`MediaPlayerItem`は再生の準備ができました。 `prepareToPlay()`開始を呼び出すと、広告解決と配置プロセスが発生します（存在する場合）。

エラーが発生した場合は、メディアプレイヤーのステータスが`ERROR`に切り替わります。

以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。

```java
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
