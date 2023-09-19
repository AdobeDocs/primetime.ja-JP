---
description: サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 ブラウザー TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質の統計
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# サービス品質の統計{#quality-of-service-statistics}

サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 ブラウザー TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

## 再生、バッファリング、デバイスに関する QOS 統計の読み取り {#read-qos-playback-buffering-and-device-statistics}

QOSProvider クラスから、再生、バッファリング、デバイスの統計を読み取ることができます。

The `QOSProvider` クラスは、バッファリング、ビットレート、フレームレート、時間データなどに関する情報を含む様々な統計を提供します。

1. メディアプレーヤーをインスタンス化します。
1. の作成 `QOSProvider` オブジェクトを探し、メディアプレーヤーに接続します。

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る 1 つの方法は、タイマーを使用することです。タイマーは、 `QOSProvider`. 例：

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
