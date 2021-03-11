---
description: アプリケーション内の1か所を設定し、ERROR状態に応じてエラー処理を実行できます。
title: エラー処理の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 3%

---


# エラー処理の設定{#set-up-error-handling}

アプリケーション内の1か所を設定し、ERROR状態に応じてエラー処理を実行できます。

1. &lt;a0追加/>のイベントリスナー。`AdobePSDK.MediaPlayerStatusChangeEvent`

   例：

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. イベントリスナーで、`event.status`が`AdobePSDK.MediaPlayerStatus.ERROR`の場合、すべてのエラーを処理するロジックを指定します。
1. エラーの処理後、`MediaPlayer`オブジェクトをリセットするか、新しいメディアリソースを読み込みます。

       MediaPlayerオブジェクトがERROR状態の場合、次のいずれかのタスクが完了するまで、この状態を終了することはできません。
   
   * `MediaPlayer.reset`メソッドを使用して、MediaPlayerオブジェクトをリセットします。
   * `MediaPlayer.replaceCurrentResource`メソッドを使用して、新しいメディアリソースを読み込みます。

<!--<a id="example_342CA5A8CD7C45BD88233C5BDBB17220"></a>-->

例：

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
onStatusChange = function (event) { 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            //handle error 
            break; 
    } 
} 
```

