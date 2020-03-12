---
description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 ブラウザーTVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 ブラウザーTVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-title: サービス品質統計
title: サービス品質統計
uuid: e4bb2617-d8a7-4da7-b669-d6ffab2864bb
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# サービス品質統計{#quality-of-service-statistics}

サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 ブラウザーTVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。

## QOS再生、バッファリング、デバイスの統計を読み取る {#read-qos-playback-buffering-and-device-statistics}

QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。

このク `QOSProvider` ラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計を提供します。

1. メディアプレイヤーをインスタンス化します。
1. オブジェクト `QOSProvider` を作成し、メディアプレイヤーに接続します。

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る1つの方法は、タイマーを使用して、から新しいQoS値を定期的に取り込むことで `QOSProvider`す。 例：

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
