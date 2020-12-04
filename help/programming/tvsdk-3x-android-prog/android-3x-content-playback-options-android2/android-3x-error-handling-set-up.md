---
description: エラーを処理する場所を1つ設定できます。
seo-description: エラーを処理する場所を1つ設定できます。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: 7c122830-6259-4e95-882e-fb1700454e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
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
