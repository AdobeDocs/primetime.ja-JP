---
description: デフォルトでは、再生を開始すると、VOD メディアは 0(MediaPlayer.LIVE_POINT) から開始されます。 デフォルトの動作を上書きできます。
title: 特定の時間にストリームを入力
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# 特定の時間にストリームを入力 {#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VOD メディアは 0(MediaPlayer.LIVE_POINT) から開始されます。 デフォルトの動作を上書きできます。

1. 位置をに渡す `MediaPlayer.prepareToPlay`.

   TVSDK は、指定された位置をアセットの開始点と見なします。 シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合、 TVSDK はデフォルトの位置を使用します。

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
