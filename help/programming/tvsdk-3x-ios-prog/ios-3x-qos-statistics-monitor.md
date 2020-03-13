---
description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-title: サービス品質統計
title: サービス品質統計
uuid: c08c1031-616a-4776-92e2-1c405467689b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# サービス品質統計 {#quality-of-service-statistics}

サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細を表示します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。

## QOS再生、バッファリング、デバイスの統計を読み取る {#section_9996406E2D814FA382B77E3041CB02BC}

クラスから再生、バッファリングおよびデバイスの統計を読み取ることがで `PTQOSProvider` きます。

このク `PTQOSProvider` ラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計を提供します。

また、モデル、オペレーティングシステム、製造元のデバイスIDなど、デバイスに関する情報も提供されます。

>[!TIP]
>
>再生バッファーサイズは変更できませんが、デバッグや分析のためにバッファーサイズのステータスを監視できます。 `PTPlaybackInformation` には、やなどのプロパティが含 `playbackBufferFull` まれま `playbackLikelyToKeepUp`す。

1. メディアプレイヤーをインスタンス化します。
1. オブジェクト `PTQOSProvider` を作成し、メディアプレイヤーに接続します。

   コンストラ `PTQOSProvider` クターは、デバイス固有の情報を取得できるように、プレーヤーコンテキストを取得します。

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る1つの方法は、タイマー（など）を使用して、から新し `NSTimer`いQoS値を定期的に取り込むことで `PTQOSProvider`す。 例：

   ```
   - (void)printPlaybackInfoLog { 
       PTPlaybackInformation *playbackInfo = qosProvider.playbackInformation;  
       if (playbackInfo) { 
           // For example: 
           NSString *infoLog = [NSString stringWithFormat:@"observedBitrate :  
                                  %f\n",playbackInfo.observedBitrate]; 
           [consoleView logMessage:@"====%@\n\n",infoLog]; 
       } 
   }
   ```

1. （オプション）デバイス固有の情報を読み取ります。

   ```
    PTDeviceInformation *devInfo = qosProvider.deviceInformation; 
   if (devInfo) { 
       [consoleView logMessage:@"=== qosDeviceInfo:==\n os =%@\n model =  
          %@\n id =%@\n\n", devInfo.os, devInfo.model, devInfo.id]; 
   } 
   [NSTimer scheduledTimerWithTimeInterval:2.0 target:self  
      selector:@selector(printPlaybackInfoLog) userInfo:nil repeats:YES];
   ```
