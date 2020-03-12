---
description: QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。
seo-description: QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。
seo-title: QOS再生、バッファリング、デバイスの統計を読み取る
title: QOS再生、バッファリング、デバイスの統計を読み取る
uuid: 19228a50-3721-4dc1-89b6-97458518e272
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# QOS再生、バッファリング、デバイスの統計を読み取る{#read-qos-playback-buffering-and-device-statistics}

QOSProviderクラスから、再生、バッファリングおよびデバイスの統計を読み取ることができます。

このク `QOSProvider` ラスは、バッファリング、ビットレート、フレームレート、時間データなど、様々な統計を提供します。

また、製造元、モデル、オペレーティングシステム、SDKバージョン、製造元のデバイスID、画面のサイズ/密度など、デバイスに関する情報も提供されます。

1. メディアプレイヤーをインスタンス化します。
1. オブジェクト `QOSProvider` を作成し、メディアプレイヤーに接続します。

   コンストラ `QOSProvider` クターは、デバイス固有の情報を取得できるように、プレーヤーコンテキストを取得します。

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る1つの方法は、タイマーを使用して、から新しいQoS値を定期的に取り込むことで `QOSProvider`す。 例：

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation = _mediaQosProvider.getPlaybackInformation();  
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
   DeviceInformation deviceInfo =  
     new QOSProvider(parent.getApplicationContext()).getDeviceInformation(); 
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

