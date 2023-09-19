---
description: エラーを処理する場所を 1 つ設定できます。
title: エラー処理の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# エラー処理の設定 {#set-up-error-handling}

エラーを処理する場所を 1 つ設定できます。

1. のイベントコールバック関数を実装します。 `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK がイベント情報 ( `MediaPlayerStatusChangeEvent` オブジェクト。
1. コールバックで、返されるステータスが `MediaPlayerStatus.ERROR`、すべてのエラーを処理するロジックを指定します。
1. エラーが処理されたら、 `MediaPlayer` オブジェクトまたは新しいメディアリソースを読み込みます。

   次の場合に `MediaPlayer` オブジェクトはエラーステータスのままです。 `MediaPlayer.reset` メソッド。

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
