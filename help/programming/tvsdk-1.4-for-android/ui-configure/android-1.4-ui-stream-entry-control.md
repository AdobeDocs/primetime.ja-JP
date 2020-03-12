---
description: デフォルトでは、再生を開始すると、VODメディアは0(MediaPlayer.LIVE_POINT)から開始されます。 デフォルトの動作を上書きできます。
seo-description: デフォルトでは、再生を開始すると、VODメディアは0(MediaPlayer.LIVE_POINT)から開始されます。 デフォルトの動作を上書きできます。
seo-title: 特定の時間にストリームを入力
title: 特定の時間にストリームを入力
uuid: ac3479e2-46a1-4ac8-a9e8-68a23f5dd74d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 特定の時間にストリームを入力 {#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VODメディアは0(MediaPlayer.LIVE_POINT)から開始されます。 デフォルトの動作を上書きできます。

1. に位置を渡します `MediaPlayer.prepareToPlay`。

   TVSDKは、指定された位置をアセットの開始ポイントと見なします。 シーク操作は不要です。 位置がシーク可能な範囲内にない場合、TVSDKはデフォルトの位置を使用します。

   例：

   ```java
   long desiredPostion = //TODO : choose a value; 
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               _mediaPlayer.prepareToPlay(desiredPosition); 
               break; 
               case PREPARING: 
               showBufferingSpinner(); 
               break; 
           ... 
       } 
   } 
   ```

