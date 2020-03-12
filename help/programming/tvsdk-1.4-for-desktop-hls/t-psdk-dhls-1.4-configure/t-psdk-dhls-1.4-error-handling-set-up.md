---
description: エラーを処理する場所を1つ設定します。
seo-description: エラーを処理する場所を1つ設定します。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# エラー処理の設定{#set-up-error-handling}

エラーを処理する場所を1つ設定します。

1. のイベントコールバック関数を実装しま `MediaPlayerStatusChangeEvent.STATUS_CHANGED`す。

   TVSDKは、オブジェクトなどのイベント情報を渡 `MediaPlayerStatusChangeEvent` します。
1. コールバックでは、イベントパラメーターのステータスがになっている場合、す `MediaPlayerStatus.ERROR`べてのエラーを処理するロジックを指定します。
1. エラーの処理後、オブジェクトをリセットするか、 `MediaPlayer` 新しいメディアリソースを読み込みます。

   オブジェクト `MediaPlayer` がERROR状態の場合、（メソッドを使用して）オブジェクトをリセットするか、新しいメディアリソースを読み込む( `MediaPlayer` )まで、こ `MediaPlayer.reset``MediaPlayer.replaceCurrentItem`の状態を終了することはできません。

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

