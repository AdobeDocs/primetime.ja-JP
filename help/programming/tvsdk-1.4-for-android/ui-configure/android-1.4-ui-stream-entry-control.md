---
description: デフォルトでは、再生を開始すると、VODメディア開始は0(MediaPlayer.LIVE_POINT)になります。 デフォルトの動作を上書きできます。
title: 特定の時間にストリームを開始
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# 特定の時刻にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VODメディア開始は0(MediaPlayer.LIVE_POINT)になります。 デフォルトの動作を上書きできます。

1. `MediaPlayer.prepareToPlay`に位置を渡します。

   TVSDKは、指定された位置をアセットの開始点と見なします。 シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合、TVSDKはデフォルトの位置を使用します。

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

