---
description: イベントハンドラーを使用すると、Browser TVSDK はイベントに応答できます。
title: イベントリスナーとコールバックの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# イベントリスナーとコールバックの実装{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、Browser TVSDK はイベントに応答できます。

イベントが発生すると、Browser TVSDK のイベントメカニズムが登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

アプリケーションは、アプリケーションに影響を与える Browser TVSDK イベント用のイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必須イベント**：すべての再生イベントをリッスンします。

     >[!IMPORTANT]
     >
     >再生イベント `STATUS_CHANGED` は、エラーを含むプレーヤーの状態を示します。 どの状態も、プレーヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**：アプリケーションに応じて、オプションです。

     例えば、再生に広告を組み込む場合は、 `AdBreakPlaybackEvent` および `AdPlaybackEvent` イベント。

1. 各イベントのイベントリスナーを実装します。

   ブラウザー TVSDK は、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   例：

   * イベントタイプ： `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * イベントプロパティ： `MediaPlayerStatus.<event>` 次のように使用されます。

```js
player.addEventListener( 
            AdobePSDK.PSDKEventType.STATUS_CHANGED,  
            onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break;
```

1. コールバックリスナーを `MediaPlayer` 使用してオブジェクトを `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
