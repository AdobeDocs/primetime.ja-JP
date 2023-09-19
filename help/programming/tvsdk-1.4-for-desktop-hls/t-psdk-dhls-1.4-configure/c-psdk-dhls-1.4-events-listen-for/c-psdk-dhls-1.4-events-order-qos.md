---
description: TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークイベントなど、QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoS イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '68'
ht-degree: 0%

---

# QoS イベント{#qos-events}

TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークイベントなど、QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

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
