---
description: エラーを処理する場所を 1 つ設定します。
title: エラー処理の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# エラー処理の設定{#set-up-error-handling}

エラーを処理する場所を 1 つ設定します。

1. のイベントコールバック関数を実装します。 `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK がイベント情報 ( `MediaPlayerStatusChangeEvent` オブジェクト。
1. コールバックで、返される状態が `MediaPlayerState.ERROR`、すべてのエラーを処理するロジックを指定します。
1. エラーが処理されたら、 `MediaPlayer` オブジェクトまたは新しいメディアリソースを読み込みます。

   次の場合に `MediaPlayer` オブジェクトはエラー状態にあり、を使用してリセットするまで、その状態のままです。 `MediaPlayer.reset` メソッド。

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

例：

```java
mediaPlayer.addEventListener( 
  MediaPlayerEvent.STATUS_CHANGED, new StatusChangedEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            // handle TVSDK error here 
        } 
    } 
});
```
