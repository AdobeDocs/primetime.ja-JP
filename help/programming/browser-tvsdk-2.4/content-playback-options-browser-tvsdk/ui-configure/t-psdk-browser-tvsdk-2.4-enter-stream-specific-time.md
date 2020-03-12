---
description: デフォルトでは、再生が開始されると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。
seo-description: デフォルトでは、再生が開始されると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。
seo-title: 特定の時間にストリームを入力
title: 特定の時間にストリームを入力
uuid: 5db73b50-0629-4fb1-8f12-6c88e4cd7109
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 特定の時間にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生が開始されると、VODメディアは0から、ライブメディアはクライアントのライブポイント(MediaPlayer.LIVE_POINT)からそれぞれ開始されます。 デフォルトの動作を上書きできます。

1. に位置を渡します `MediaPlayer.prepareToPlay`。
1. ブラウザーTVSDKは、この位置をアセットの開始点として使用します。

   >[!NOTE]
   >
   >シーク操作は不要です。

1. 位置がシーク可能な範囲内にない場合は、デフォルトの位置が使用されます。

   例：

   ```js
   var desiredPostion = //choose a value; 
   onStatusChange = function (event) { 
       case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
           console.log("Player Status: INITIALIZED"); 
           player.prepareToPlay(desiredPostion); 
           break; 
   } 
   ```

