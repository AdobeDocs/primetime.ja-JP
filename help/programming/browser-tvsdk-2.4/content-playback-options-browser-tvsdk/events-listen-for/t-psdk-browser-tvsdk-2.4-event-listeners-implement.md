---
description: イベントハンドラーを使用すると、Browser TVSDKがイベントに応答できます。
title: イベントリスナーとコールバックの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# イベントリスナーとコールバックの実装{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、Browser TVSDKがイベントに応答できます。

イベントが発生すると、Browser TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

アプリケーションで、アプリケーションに影響を与えるBrowser TVSDKイベント用のイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要があるイベントを決定します。

   * **必須イベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベント`STATUS_CHANGED`は、エラーを含むプレイヤーの状態を提供します。 状態によっては、プレイヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、再生に広告を組み込む場合は、すべての`AdBreakPlaybackEvent`および`AdPlaybackEvent`イベントをリッスンします。

1. 各イベントにイベントリスナーを実装します。

   ブラウザーTVSDKは、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、リスナーで使用して適切なアクションを実行できるイベントに関する関連情報を提供します。

   例：

   * イベントタイプ:`AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * イベントプロパティ：`MediaPlayerStatus.<event>`は次のように使用されます。

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

1. `MediaPlayer.addEventListener`を使用して、`MediaPlayer`オブジェクトにコールバックリスナーを登録します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
