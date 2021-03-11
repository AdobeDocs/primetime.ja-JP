---
description: サービス品質(QoS)は、ビデオエンジンの動作状況に関する詳細な表示を提供します。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質統計
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---


# サービス品質統計{#quality-of-service-statistics}

サービス品質(QoS)は、ビデオエンジンの動作状況に関する詳細な表示を提供します。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

TVSDKは、以下のダウンロードされたリソースに関する情報も提供します。

* プレイリスト/マニフェストファイル
* ファイルフラグメント
* ファイルの追跡情報

## 読み込み情報{#section_4439D91E8EDC45588EF1D7BE25697350}を使用してフラグメントレベルで追跡

フラグメントやトラックなど、ダウンロードされたリソースに関するQoS(Quality Of Service)情報を`LoadInformation`クラスから読み取ることができます。

1. `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE`イベントリスナーを実装し、登録します。
1. `event.getLoadInformation()`を呼び出して、コールバックに渡される`event`パラメーターから関連するデータを読み取ります。

   >[!NOTE]
   >
   >`LoadInformation`について詳しくは、Android向け[3.0 (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html) APIドキュメントを参照してください。

## 再生、バッファリング、デバイスに関するQOS統計を読み取ります{#section_D21722600F324E67A9F06234D338B243}

`QOSProvider`クラスから再生、バッファリング、デバイスの統計を読み取ることができます。

`QOSProvider`クラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計情報を提供します。 製造元、モデル、オペレーティングシステム、SDKバージョン、製造元のデバイスID、画面のサイズ/密度など、デバイスに関する情報も提供します。

1. メディアプレイヤーをインスタンス化します。
1. `QOSProvider`オブジェクトを作成し、メディアプレイヤーに接続します。

   `QOSProvider`コンストラクタは、デバイス固有の情報を取得できるように、プレイヤーコンテキストを取得します。

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る方法の1つは、タイマーを設定して、`QOSProvider`から新しいQoS値を定期的に取り込むことです。

   例：

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation =  
                     _mediaQosProvider.getPlaybackInformation();  
                   setQosItem("Frame rate", (int) playbackInformation.getFrameRate());  
                   setQosItem("Dropped frames", (int) playbackInformation.getDroppedFrameCount()); 
                   setQosItem("Bitrate", (int) playbackInformation.getBitrate()); 
                   setQosItem("Buffering time", (int) playbackInformation.getBufferingTime());  
                   setQosItem("Buffer length", (int) playbackInformation.getBufferLength());  
                   setQosItem("Buffer time", (int) playbackInformation.getBufferTime());  
                   setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount());  
                   setQosItem("Time to load", (int) playbackInformation.getTimeToLoad());  
                   setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); 
                   setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); 
                   setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());   
                   playbackInformation.getPerceivedBandwidth()); 
               } 
           }); 
       }; 
   }; 
   ```

1. （オプション）デバイス固有の情報を読み取ります。

   ```java
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider(parent.getApplicationContext()). 
                                  getDeviceInformation(); 
   tv = (TextView) view.findViewById(R.id.aboutDeviceModel); 
   tv.setText(parent.getString(R.string.aboutDeviceModel) + " " +  
     deviceInfo.getManufacturer() + " - " + deviceInfo.getModel()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceSoftware); 
   tv.setText(parent.getString(R.string.aboutDeviceSoftware) + " " +  
     deviceInfo.getOS() + ", SDK: " + deviceInfo.getSDK()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceResolutin); 
   String orientation = parent.getResources().getConfiguration().orientation ==  
     Configuration.ORIENTATION_LANDSCAPE ? "landscape" : "portrait"; 
   tv.setText(parent.getString(R.string.aboutDeviceResolution) + " " +  
     deviceInfo.getWidthPixels() + "x" + deviceInfo.getHeightPixels() +  
     " (" + orientation + ")"); 
   ```
