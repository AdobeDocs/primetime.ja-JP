---
description: TVSDKは、QoS(QoS)イベントをディスパッチして、バッファリングやシークイベントなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoSイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '68'
ht-degree: 0%

---


# QoSイベント{#qos-events}

TVSDKは、QoS(QoS)イベントをディスパッチして、バッファリングやシークイベントなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

次の例に、これらのイベントの一般的な流れを示します。

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

