---
description: アプリケーション内の1か所を設定し、ERROR状態に応じてエラー処理を実行できます。
seo-description: アプリケーション内の1か所を設定し、ERROR状態に応じてエラー処理を実行できます。
seo-title: エラー処理の設定
title: エラー処理の設定
uuid: 9e650ea7-86cb-4489-a3fd-80cd2ccef41f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 2%

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

