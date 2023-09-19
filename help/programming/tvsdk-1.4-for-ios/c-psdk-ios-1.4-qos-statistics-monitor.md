---
description: サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質の統計
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# サービス品質の統計{#quality-of-service-statistics}

サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

## 再生、バッファリング、デバイスに関する QOS 統計の読み取り {#section_9996406E2D814FA382B77E3041CB02BC}

再生、バッファリング、デバイスの統計は、 `PTQOSProvider` クラス。

The `PTQOSProvider` クラスは、バッファリング、ビットレート、フレームレート、時間データなどに関する情報を含む様々な統計を提供します。

また、モデル、オペレーティングシステム、製造元のデバイス ID など、デバイスに関する情報も提供されます。

>[!TIP]
>
>再生バッファーのサイズは変更できませんが、デバッグや分析のために、バッファーサイズのステータスを監視することができます。 `PTPlaybackInformation` 次のようなプロパティを含みます。 `playbackBufferFull` および `playbackLikelyToKeepUp`.

1. メディアプレーヤーをインスタンス化します。
1. の作成 `PTQOSProvider` オブジェクトを探し、メディアプレーヤーに接続します。

   The `PTQOSProvider` コンストラクターは、デバイス固有の情報を取得できるように、プレーヤーコンテキストを取得します。

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る 1 つの方法は、タイマー ( `NSTimer`を呼び出し、 `PTQOSProvider`. 例：

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
