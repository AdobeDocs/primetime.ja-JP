---
description: アプリケーション内の 1 か所を設定して、ERROR 状態に応じてエラー処理を実行できます。
title: エラー処理の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# エラー処理の設定{#set-up-error-handling}

アプリケーション内の 1 か所を設定して、ERROR 状態に応じてエラー処理を実行できます。

1. のイベントリスナーを追加 `AdobePSDK.MediaPlayerStatusChangeEvent`.

   例：

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. イベントリスナーで、 `event.status` 次に該当 `AdobePSDK.MediaPlayerStatus.ERROR`」で、すべてのエラーを処理するロジックを指定します。
1. エラーが処理されたら、 `MediaPlayer` オブジェクトまたは新しいメディアリソースを読み込みます。

       MediaPlayer オブジェクトが ERROR 状態の場合、次のタスクの 1 つを完了するまで、この状態を終了することはできません。
   
   * 次を使用して、 MediaPlayer オブジェクトをリセットします。 `MediaPlayer.reset` メソッド。
   * を使用して新しいメディアリソースを読み込む `MediaPlayer.replaceCurrentResource` メソッド。

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
