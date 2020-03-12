---
description: デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。
seo-description: デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。
seo-title: 特定の時間にストリームを入力
title: 特定の時間にストリームを入力
uuid: 65a19192-b890-4d69-9cb1-582a22988d2b
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# 特定の時間にストリームを入力 {#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。

1. に位置を渡します `MediaPlayer.prepareToPlay`。

   TVSDKは、指定された位置をアセットの始点と見なし、シーク操作は不要です。 位置がシーク可能な範囲内にない場合、TVSDKはデフォルトの位置を使用します。 詳しくは、メディアプレイヤ [ーへのメディアリソースの読み込みを参照してくださ](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md)い。

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

