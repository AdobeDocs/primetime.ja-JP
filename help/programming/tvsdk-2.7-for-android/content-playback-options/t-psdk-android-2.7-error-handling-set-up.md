---
description: エラーを処理する場所を1つ設定できます。
seo-description: エラーを処理する場所を1つ設定できます。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# エラー処理の設定 {#set-up-error-handling}

エラーを処理する場所を1つ設定できます。

1. のイベントコールバック関数を実装しま `MediaPlayerEvent.STATUS_CHANGED`す。

   TVSDKは、オブジェクトなどのイベント情報を渡 `MediaPlayerStatusChangeEvent` します。
1. コールバックで、返されたステータスがになった場合、す `MediaPlayerStatus.ERROR`べてのエラーを処理するロジックを指定します。
1. エラーの処理後、オブジェクトをリセットするか、 `MediaPlayer` 新しいメディアリソースを読み込みます。

   オブジェクト `MediaPlayer` がエラーステータスの場合は、メソッドを使用してリセットするまで、そのステータスのままにな `MediaPlayer.reset` ります。

<!--<a id="example_E74BB605ED08450295B8902F1E4BB8F5"></a>-->

例：

```java
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
        // handle TVSDK error here 
        } 
    } 
});
```

