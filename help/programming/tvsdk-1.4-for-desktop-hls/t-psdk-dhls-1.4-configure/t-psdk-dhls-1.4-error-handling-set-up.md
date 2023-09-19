---
description: エラーを処理する場所を 1 つ設定します。
title: エラー処理の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# エラー処理の設定{#set-up-error-handling}

エラーを処理する場所を 1 つ設定します。

1. のイベントコールバック関数を実装します。 `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK がイベント情報 ( `MediaPlayerStatusChangeEvent` オブジェクト。
1. コールバックで、イベントパラメーターからのステータスが `MediaPlayerStatus.ERROR`、すべてのエラーを処理するロジックを指定します。
1. エラーが処理されたら、 `MediaPlayer` オブジェクトまたは新しいメディアリソースを読み込みます。

   次の場合に `MediaPlayer` オブジェクトは ERROR 状態になっているので、 `MediaPlayer` オブジェクト ( `MediaPlayer.reset` メソッド ) を使用するか、新しいメディアリソース ( `MediaPlayer.replaceCurrentItem`) をクリックします。

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
