---
description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(MediaPlayer.LIVE_POINT)のライブメディア開始が発生します。 デフォルトの動作を上書きできます。
seo-description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(MediaPlayer.LIVE_POINT)のライブメディア開始が発生します。 デフォルトの動作を上書きできます。
seo-title: 特定の時間にストリームを開始
title: 特定の時間にストリームを開始
uuid: 65a19192-b890-4d69-9cb1-582a22988d2b
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 1%

---


# 特定の時刻にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(MediaPlayer.LIVE_POINT)のライブメディア開始が発生します。 デフォルトの動作を上書きできます。

1. `MediaPlayer.prepareToPlay`に位置を渡します。

   TVSDKは、指定された位置をアセットの開始点と見なすので、シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合、TVSDKはデフォルトの位置を使用します。 詳しくは、[メディアプレイヤーへのメディアリソースの読み込み](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md)を参照してください。

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

