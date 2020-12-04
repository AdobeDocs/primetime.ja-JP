---
description: エラーを処理する場所を1つ設定できます。
seo-description: エラーを処理する場所を1つ設定できます。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---


# {#set-up-error-handling}の処理エラーの設定

エラーを処理する場所を1つ設定できます。

1. `MediaPlayerEvent.STATUS_CHANGED`のイベントコールバック関数を実装します。

   TVSDKは、`MediaPlayerStatusChangeEvent`オブジェクトなどのイベント情報を渡します。
1. コールバックで、返されたステータスが`MediaPlayerStatus.ERROR`の場合、すべてのエラーを処理するロジックを指定します。
1. エラーの処理後、`MediaPlayer`オブジェクトをリセットするか、新しいメディアリソースを読み込みます。

   `MediaPlayer`オブジェクトがエラー状態の場合、`MediaPlayer.reset`メソッドを使用してリセットするまで、その状態がそのままです。

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

