---
description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-description: MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。
seo-title: メディアリソースをメディアプレイヤーに読み込む
title: メディアリソースをメディアプレイヤーに読み込む
uuid: 0334fa69-1d92-44d8-8891-2bc90a1ea498
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# メディアリソースをメディアプレイヤーに読み込む {#load-a-media-resource-in-the-media-player}

MediaResourceを直接インスタンス化し、再生するビデオコンテンツを読み込むことで、リソースを読み込みます。 これは、メディアリソースを読み込む1つの方法です。

1. 新しいリソースを再生するメディアプレイヤーを設定します。

   既存のインスタンスを呼び出して渡すことで、現 `MediaPlayer.replaceCurrentResource()` 在再生可能な項目を置き換 `MediaResource` えます。

   これにより、リソースの読み込みプロセスが開始されます。

1. イベントをイ `MediaPlayerEvent.STATUS_CHANGED` ンスタンスに登録 `MediaPlayer` します。 コールバックで、少なくとも次のステータス値を確認します。

   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.ERROR`
   これらのイベントを通じて、オブジェ `MediaPlayer` クトは、メディアリソースが正常に読み込まれたことをアプリケーションに通知します。
1. メディアプレイヤーのステータスがに変わった `INITIALIZED`ら、を呼び出すことができま `MediaPlayer.prepareToPlay()`す。

   このステータスは、メディアが正常に読み込まれたことを示します。 新しいファイル `MediaPlayerItem` は再生の準備が整いました。 を呼び出す `prepareToPlay()` と、広告の解決および配置プロセスが開始されます（存在する場合）。

障害が発生した場合、メディアプレイヤーはステータスに切り替わ `ERROR` ります。

以下のサンプルコードは、メディアリソースの読み込みプロセスを簡単に示しています。
>```java>
>// mediaResource is a properly configured MediaResource instance 
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
