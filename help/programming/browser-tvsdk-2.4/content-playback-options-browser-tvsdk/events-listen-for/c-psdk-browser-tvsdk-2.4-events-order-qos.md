---
description: ブラウザーTVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークイベントなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-description: ブラウザーTVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークイベントなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-title: QoSイベント
title: QoSイベント
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# QoSイベント{#qos-events}

ブラウザーTVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークイベントなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべてのQoS関連イベントに関する通知を受け取るには、MediaPlayerインスタンスを作成し、 `AdobePSDK.QOSProvider` このインスタンスにMediaPlayerインスタンスをアタッチ `QOSProvider` します。

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

インスタンスのプロパティを定期的に確認するように、アプリケ `playbackInformation` ーションでタイマーを設 `qosProvider` 定します。 このプロ `playbackInformation` パティは、現在の再生統計のスナップショットを提供します。 例：

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

