---
description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細なビューを提供します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-description: サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細なビューを提供します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。
seo-title: サービス品質統計
title: サービス品質統計
uuid: 3d66ed44-9d4a-4162-962f-e238575ff2dd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# サービス品質統計 {#quality-of-service-statistics}

サービス品質(QoS)は、ビデオエンジンのパフォーマンスの詳細なビューを提供します。 TVSDKは、再生、バッファリングおよびデバイスに関する詳細な統計情報を提供します。

TVSDKは、次のダウンロードされたリソースに関する情報も提供します。

* プレイリスト/マニフェストファイル
* ファイルフラグメント
* ファイルの追跡情報

## 読み込み情報を使用してフラグメントレベルで追跡 {#section_4439D91E8EDC45588EF1D7BE25697350}

フラグメントやトラックなど、ダウンロードされたリソースに関するサービス品質(QoS)情報をクラスから読み取ることがで `LoadInformation` きます。

1. イベントリスナーを実装し、 `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` 登録します。
1. を呼び出 `event.getLoadInformation()` して、コールバックに渡されるパラメ `event` ーターから関連データを読み取ります。

   >[!NOTE]
   >
   >詳しくは、 `LoadInformation`Android用 [3.0(Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html) APIドキュメントを参照してください。

## QOS再生、バッファリング、デバイスの統計を読み取る {#section_D21722600F324E67A9F06234D338B243}

クラスから再生、バッファリングおよびデバイスの統計を読み取ることがで `QOSProvider` きます。

このク `QOSProvider` ラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計を提供します。 また、製造元、モデル、オペレーティングシステム、SDKバージョン、製造元のデバイスID、画面のサイズ/密度など、デバイスに関する情報も提供されます。

1. メディアプレイヤーをインスタンス化します。
1. オブジェクト `QOSProvider` を作成し、メディアプレイヤーに接続します。

   コンストラ `QOSProvider` クターは、デバイス固有の情報を取得できるように、プレーヤーコンテキストを取得します。

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る1つの方法は、タイマーを使用して、から新しいQoS値を定期的に取り込むことで `QOSProvider`す。

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
