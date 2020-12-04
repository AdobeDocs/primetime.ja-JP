---
description: エラーを処理する場所を1か所設定します。
seo-description: エラーを処理する場所を1か所設定します。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: a3182fce-85ac-4dad-bdb3-f9bfbdb2c62d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---


# エラー処理の設定{#set-up-error-handling}

エラーを処理する場所を1か所設定します。

1. `MediaPlayerEvent.STATUS_CHANGED`のイベントコールバック関数を実装します。

   TVSDKは、`MediaPlayerStatusChangeEvent`オブジェクトなどのイベント情報を渡します。
1. コールバックで、返された状態が`MediaPlayerState.ERROR`の場合、すべてのエラーを処理するロジックを指定します。
1. エラーの処理後、`MediaPlayer`オブジェクトをリセットするか、新しいメディアリソースを読み込みます。

   `MediaPlayer`オブジェクトがerror状態の場合、`MediaPlayer.reset`メソッドを使用してリセットするまで、その状態が維持されます。

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

