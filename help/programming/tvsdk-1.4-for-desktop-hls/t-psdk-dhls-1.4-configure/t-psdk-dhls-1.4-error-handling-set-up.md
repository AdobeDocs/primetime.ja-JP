---
description: エラーを処理する場所を1か所設定します。
seo-description: エラーを処理する場所を1か所設定します。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---


# エラー処理の設定{#set-up-error-handling}

エラーを処理する場所を1か所設定します。

1. `MediaPlayerStatusChangeEvent.STATUS_CHANGED`のイベントコールバック関数を実装します。

   TVSDKは、`MediaPlayerStatusChangeEvent`オブジェクトなどのイベント情報を渡します。
1. コールバックで、イベントパラメーターからのステータスが`MediaPlayerStatus.ERROR`の場合、すべてのエラーを処理するロジックを指定します。
1. エラーの処理後、`MediaPlayer`オブジェクトをリセットするか、新しいメディアリソースを読み込みます。

   `MediaPlayer`オブジェクトがERROR状態の場合、`MediaPlayer.reset`メソッドを介して`MediaPlayer`オブジェクトをリセットするか、新しいメディアリソースを読み込む(`MediaPlayer.replaceCurrentItem`)までは、この状態を終了できません。

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

例：

```
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
 
private void onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    if (event.status == MediaPlayerStatus.ERROR) { 
        var error:MediaError = event.error; 
        // handle TVSDK error here 
    } 
} 
```

