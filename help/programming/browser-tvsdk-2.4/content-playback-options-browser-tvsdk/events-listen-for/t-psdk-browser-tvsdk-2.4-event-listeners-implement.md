---
description: イベントハンドラーを使用すると、ブラウザーTVSDKがイベントに応答できます。
seo-description: イベントハンドラーを使用すると、ブラウザーTVSDKがイベントに応答できます。
seo-title: イベントリスナーとコールバックの実装
title: イベントリスナーとコールバックの実装
uuid: 63f62c60-505e-4f83-bc0d-58895d85a75a
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# イベントリスナーとコールバックの実装{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、ブラウザーTVSDKがイベントに応答できます。

イベントが発生すると、ブラウザーTVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

アプリケーションは、アプリケーションに影響を与えるブラウザーTVSDKイベントのイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必要なイベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベントは、 `STATUS_CHANGED` エラーを含むプレーヤーの状態を提供します。 どの状態でも、プレイヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、再生に広告を組み込む場合は、すべてのイベントとイベントをリス `AdBreakPlaybackEvent` ンし `AdPlaybackEvent` ます。

1. 各イベントのイベントリスナーを実装します。

   ブラウザーTVSDKは、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   例：

   * イベントタイプ： `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * イベントプロパティ：次のよ `MediaPlayerStatus.<event>` うに使用します。

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

1. を使用して、コールバックリスナーをオブジ `MediaPlayer` ェクトに登録しま `MediaPlayer.addEventListener`す。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
