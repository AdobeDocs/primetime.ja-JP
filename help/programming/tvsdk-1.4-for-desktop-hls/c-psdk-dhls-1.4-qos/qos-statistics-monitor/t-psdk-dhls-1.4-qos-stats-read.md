---
description: QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。
seo-description: QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。
seo-title: QOS再生、バッファリング、デバイスの統計を読み取る
title: QOS再生、バッファリング、デバイスの統計を読み取る
uuid: 5ee631fc-cd6f-4f35-8621-2ffdc51a57c7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# QOS再生、バッファリング、デバイスの統計を読み取る{#read-qos-playback-buffering-and-device-statistics}

QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。

このク `QOSProvider` ラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計を提供します。

また、製造元、モデル、オペレーティングシステム、SDKのバージョン、画面のサイズ/密度など、デバイスに関する情報も提供されます。

1. メディアプレイヤーをインスタンス化します。
1. オブジェクト `QOSProvider` を作成し、メディアプレイヤーに接続します。

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る1つの方法は、タイマーを使用して、から新しいQoS値を定期的に取り込むことで `QOSProvider`す。 例：

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

