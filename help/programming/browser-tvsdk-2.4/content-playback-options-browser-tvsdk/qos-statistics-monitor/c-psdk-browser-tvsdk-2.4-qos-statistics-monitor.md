---
description: サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 ブラウザーTVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質統計
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 1%

---


# サービス品質統計{#quality-of-service-statistics}

サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 ブラウザーTVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

## 再生、バッファリング、デバイスに関するQOS統計を読み取ります{#read-qos-playback-buffering-and-device-statistics}

QOSProviderクラスから再生、バッファリング、デバイスの統計を読み取ることができます。

`QOSProvider`クラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計情報を提供します。

1. メディアプレイヤーをインスタンス化します。
1. `QOSProvider`オブジェクトを作成し、メディアプレイヤーに接続します。

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る方法の1つは、タイマーを設定して、`QOSProvider`から新しいQoS値を定期的に取り込むことです。 例：

   ```js
   var qosTimer = (function () { 
       var ref = null, 
       qosChangeInterval = 500, // in milliseconds 
   
       startTimer = function () { 
           var playbackInformation = qosProvider.playbackInformation; 
        console.log("Frame rate", playbackInformation.frameRate); 
           console.log ("Dropped frames", playbackInformation.droppedFrameCount); 
           console.log ("Bitrate", playbackInformation.bitrate); 
           console.log ("Buffering time", playbackInformation.bufferingTime); 
           console.log ("Buffer length", playbackInformation.bufferLength); 
           console.log ("Buffer time", playbackInformation.bufferTime); 
           console.log ("Empty buffer count", playbackInformation.emptyBufferCount); 
           console.log ("Time to load", playbackInformation.timeToLoad); 
           console.log ("Time to start", playbackInformation.timeToStart); 
           ref = window.setTimeout(startTimer, qosChangeInterval); 
       }; 
   
       return { 
           start: function () { 
               if (ref !== null) { 
                   // don't start another timeout if one already exists. 
                   return; 
               } 
               startTimer(); 
           }, 
   
           stop: function () { 
               window.clearTimeout(ref); 
               ref = null; 
           } 
       };  
   })() 
   
   qosTimer.start(); 
   ```

1. （オプション）デバイス固有の情報を読み取ります。

   ```js
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider().deviceInformation; 
   console.log("OS: "+ deviceInfo.getOS()); 
   console.log("Width: "+ deviceInfo.getWidthPixels() +  
               "Height: "+ deviceInfo.getHeightPixels() );
   ```
