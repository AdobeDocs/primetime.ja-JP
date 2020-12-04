---
description: サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
seo-description: サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
seo-title: サービス品質統計
title: サービス品質統計
uuid: b74cbc94-1d69-4b4b-b969-d0e985b4762b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# サービス品質統計{#quality-of-service-statistics}

サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

## 再生、バッファリング、デバイスに関するQOS統計を読み取ります{#section_9996406E2D814FA382B77E3041CB02BC}

`PTQOSProvider`クラスから再生、バッファリング、デバイスの統計を読み取ることができます。

`PTQOSProvider`クラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計情報を提供します。

また、モデル、オペレーティングシステム、製造元のデバイスIDなど、デバイスに関する情報も提供されます。

>[!TIP]
>
>再生バッファーのサイズは変更できませんが、デバッグや分析のためにバッファーサイズの状態を監視できます。 `PTPlaybackInformation` には、 `playbackBufferFull` およびなどのプロパティが含まれ `playbackLikelyToKeepUp`ます。

1. メディアプレイヤーをインスタンス化します。
1. `PTQOSProvider`オブジェクトを作成し、メディアプレイヤーに接続します。

   `PTQOSProvider`コンストラクタは、デバイス固有の情報を取得できるように、プレイヤーコンテキストを取得します。

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る方法の1つとして、`NSTimer`などのタイマーを使用し、`PTQOSProvider`から新しいQoS値を定期的に取り込みます。 例：

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

