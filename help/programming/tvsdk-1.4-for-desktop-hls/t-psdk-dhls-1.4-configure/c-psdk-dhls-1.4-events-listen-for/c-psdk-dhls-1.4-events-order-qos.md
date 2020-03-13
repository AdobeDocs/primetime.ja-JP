---
description: TVSDKは、サービス品質(QoS)イベントをディスパッチして、QoS統計の計算に影響を与える可能性のあるイベント（バッファリングやシークイベントなど）をアプリケーションに通知します。
seo-description: TVSDKは、サービス品質(QoS)イベントをディスパッチして、QoS統計の計算に影響を与える可能性のあるイベント（バッファリングやシークイベントなど）をアプリケーションに通知します。
seo-title: QoSイベント
title: QoSイベント
uuid: e6ba1e9b-435b-480d-bea9-bff41b4e0b21
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# QoSイベント{#qos-events}

TVSDKは、サービス品質(QoS)イベントをディスパッチして、QoS統計の計算に影響を与える可能性のあるイベント（バッファリングやシークイベントなど）をアプリケーションに通知します。

次の例は、これらのイベントの一般的な流れを示しています。

```
// For buffering 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_BEGIN, onBufferingBegin); 
private function onBufferingBegin(event:BufferEvent):void { ... } 
 
mediaPlayer.addEventListener(BufferEvent.BUFFERING_END, onBufferingCompleted); 
private function onBufferingCompleted(event:BufferEvent):void { ... } 
 
// For seeking 
mediaPlayer.addEventListener(SeekEvent.SEEK_BEGIN, onSeekBegin); 
private function onSeekBegin(event:SeekEvent):void { ... } 
 
mediaPlayer.addEventListener(SeekEvent.SEEK_COMPLETED, onSeekCompleted); 
private function onSeekCompleted(event:SeekEvent):void { ... } 
 
...  SeekEvent.SEEK_POSITION_ADJUSTED...  //if the desired 
// seek position is modified by the current advertising policies 
```

