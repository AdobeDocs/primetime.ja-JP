---
description: QOSProviderクラスから再生、バッファリング、デバイスの統計を読み取ることができます。
seo-description: QOSProviderクラスから再生、バッファリング、デバイスの統計を読み取ることができます。
seo-title: 再生、バッファリング、デバイスに関するQOS統計の読み取り
title: 再生、バッファリング、デバイスに関するQOS統計の読み取り
uuid: 5ee631fc-cd6f-4f35-8621-2ffdc51a57c7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 1%

---


# 再生、バッファリング、デバイスに関するQOS統計を読み取ります{#read-qos-playback-buffering-and-device-statistics}

QOSProviderクラスから再生、バッファリング、デバイスの統計を読み取ることができます。

`QOSProvider`クラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計情報を提供します。

製造元、モデル、オペレーティングシステム、SDKバージョン、画面のサイズ/密度など、デバイスに関する情報も提供します。

1. メディアプレイヤーをインスタンス化します。
1. `QOSProvider`オブジェクトを作成し、メディアプレイヤーに接続します。

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る方法の1つは、タイマーを設定して、`QOSProvider`から新しいQoS値を定期的に取り込むことです。 例：

   ```
   var qosTimer:Timer = new Timer(1000); // every 1 second  
   qosTimer.addEventListener(TimerEvent.Timer, onQoSTimer);  
   qosTimer.start(); 
   private function onQoSTimer(event:TimerEvent):void { 
       var playbackInformation:PlaybackInformation = _mediaQosProvider.getPlaybackInformation(); 
       qosInfo["Frame rate"] = playbackInformation.frameRate.toFixed();  
       qosInfo["Dropped frames"] = playbackInformation.droppedFrameCount.toFixed(); 
       qosInfo["Bitrate"] = playbackInformation.bitrate.toFixed(); 
       qosInfo["Bandwidth"] = playbackInformation.perceivedBandwidth; 
       qosInfo["Buffering time"] = playbackInformation.bufferingTime.toFixed(); 
       qosInfo["Buffer length"] = playbackInformation.bufferLength.toFixed();  
       qosInfo["Buffer time"] = playbackInformation.bufferTime.toFixed(); 
       qosInfo["Empty buffer count"] = playbackInformation.emptyBufferCount.toFixed();  
       qosInfo["Time to load"] = playbackInformation.timeToLoad.toFixed();  
       qosInfo["Time to start"] = playbackInformation.timeToStart.toFixed(); 
       qosView.update(qosInfo); 
   }
   ```

1. （オプション）デバイス固有の情報を読み取ります。

   ```
   // Show device information 
   var deviceInfo:DeviceInformation = new QOSProvider.deviceInformation; 
   qosInfo["deviceModel"] = deviceInfo.manufacturer +"-" + deviceInfo.model; 
   qosInfo["os"] = deviceInfo.os;  
   qosInfo["runtime"] = deviceInfo.runtimeVersion;  
   qosInfo["widthPixels"] = deviceInfo.widthPixels;  
   qosInfo["heightPixels"] = deviceInfo.heightPixels; 
   qosView.update(qosInfo); 
   ```

