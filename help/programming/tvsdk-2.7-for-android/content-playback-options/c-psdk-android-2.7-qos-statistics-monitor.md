---
description: サービス品質 (QoS) は、ビデオエンジンのパフォーマンスに関する詳細な表示を提供します。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質の統計
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# サービス品質の統計 {#quality-of-service-statistics}

サービス品質 (QoS) は、ビデオエンジンのパフォーマンスに関する詳細な表示を提供します。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

TVSDK は、以下のダウンロードされたリソースに関する情報も提供します。

* プレイリスト/マニフェストファイル
* ファイルフラグメント
* ファイルのトラッキング情報

## 読み込み情報を使用してフラグメントレベルで追跡 {#section_4439D91E8EDC45588EF1D7BE25697350}

フラグメントやトラックなど、ダウンロードされたリソースに関する Quality of Service(QoS) 情報を、 `LoadInformation` クラス。

1. を実装して登録します。 `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` イベントリスナー。
1. 通話 `event.getLoadInformation()` 関連するデータを `event` コールバックに渡されるパラメーター。

   >[!NOTE]
   >
   >詳しくは、 `LoadInformation`を参照してください。 [Android 版 2.7(Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html) API ドキュメント。

## 再生、バッファリング、デバイスに関する QOS 統計の読み取り {#section_D21722600F324E67A9F06234D338B243}

再生、バッファリング、デバイスの統計は、 `QOSProvider` クラス。

The `QOSProvider` クラスは、バッファリング、ビットレート、フレームレート、時間データなどに関する情報を含む様々な統計を提供します。 また、製造元、モデル、オペレーティングシステム、SDK バージョン、製造元のデバイス ID、画面サイズ/密度など、デバイスに関する情報も提供されます。

1. メディアプレーヤーをインスタンス化します。
1. の作成 `QOSProvider` オブジェクトを探し、メディアプレーヤーに接続します。

   The `QOSProvider` コンストラクターは、デバイス固有の情報を取得できるように、プレーヤーコンテキストを取得します。

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る 1 つの方法は、タイマーを使用することです。タイマーは、 `QOSProvider`.

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
