---
description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(MediaPlayer.LIVE_POINT)のライブメディア開始が発生します。 デフォルトの動作を上書きできます。
title: 特定の時間にストリームを開始
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 1%

---


# 特定の時刻にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(MediaPlayer.LIVE_POINT)のライブメディア開始が発生します。 デフォルトの動作を上書きできます。

1. `MediaPlayer.prepareToPlay`に位置を渡します。

   TVSDKは、指定された位置をアセットの開始点と見なすので、シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合、TVSDKはデフォルトの位置を使用します。 詳しくは、[メディアプレイヤーへのメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md)を参照してください。

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
