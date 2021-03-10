---
description: ブラウザーTVSDKは、QoS(Quality of Service)イベントをディスパッチして、バッファリングやシークイベントなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoSイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# QoSイベント{#qos-events}

ブラウザーTVSDKは、QoS(Quality of Service)イベントをディスパッチして、バッファリングやシークイベントなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべてのQoS関連イベントに関して通知を受けるには、`AdobePSDK.QOSProvider`のインスタンスを作成し、MediaPlayerインスタンスをこの`QOSProvider`インスタンスに接続します。

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

アプリケーションでタイマーを設定し、`qosProvider`インスタンスの`playbackInformation`プロパティを定期的に確認します。 `playbackInformation`プロパティは、現在の再生統計のスナップショットを提供します。 例：

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

