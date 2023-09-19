---
description: デフォルトでは、再生を開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (MediaPlayer.LIVE_POINT) からそれぞれ開始されます。 デフォルトの動作を上書きできます。
title: 特定の時間にストリームを入力
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# 特定の時間にストリームを入力 {#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (MediaPlayer.LIVE_POINT) からそれぞれ開始されます。 デフォルトの動作を上書きできます。

1. 位置をに渡す `MediaPlayer.prepareToPlay`.

   TVSDK は、指定された位置をアセットの開始点と見なし、シーク操作は不要です。 位置がシーク可能な範囲内にない場合、 TVSDK はデフォルトの位置を使用します。 詳しくは、 [メディアプレーヤーへのメディアリソースの読み込み](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

   例：

   ```java
   long desiredPostion = // TODO : choose a value; 
   @Override 
   public void onStatusChanged(MediaPlayerStatusChangedEvent statusChangedEvent) {   
       switch (statusChangedEvent.getStatus()) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
           case PREPARING: 
               showBufferingSpinner(); 
               break; 
       } 
   }
   ```
