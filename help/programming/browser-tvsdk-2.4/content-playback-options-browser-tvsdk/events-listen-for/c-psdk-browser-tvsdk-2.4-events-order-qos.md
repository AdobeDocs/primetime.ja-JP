---
description: ブラウザー TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークイベントなど、QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoS イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# QoS イベント{#qos-events}

ブラウザー TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークイベントなど、QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべての QoS 関連イベントに関する通知を受け取るには、 `AdobePSDK.QOSProvider` MediaPlayer インスタンスをこれに接続します。 `QOSProvider` インスタンス：

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

アプリケーションでタイマーを設定し、定期的に `playbackInformation` のプロパティ `qosProvider` インスタンス。 The `playbackInformation` プロパティは、現在の再生統計のスナップショットを提供します。 例：

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```
