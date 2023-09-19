---
description: デフォルトでは、再生が開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (MediaPlayer.LIVE_POINT) から開始されます。 デフォルトの動作を上書きできます。
title: 特定の時間にストリームを入力
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 特定の時間にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生が開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (MediaPlayer.LIVE_POINT) から開始されます。 デフォルトの動作を上書きできます。

1. 位置をに渡す `MediaPlayer.prepareToPlay`.
1. ブラウザー TVSDK は、この位置をアセットの開始点として使用します。

   >[!NOTE]
   >
   >シーク操作は必要ありません。

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
