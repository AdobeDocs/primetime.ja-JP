---
description: デフォルトでは、再生開始、0のVODメディア開始、クライアントのライブポイント(MediaPlayer.LIVE_POINT)でのライブメディア開始が発生します。 デフォルトの動作を上書きできます。
seo-description: デフォルトでは、再生開始、0のVODメディア開始、クライアントのライブポイント(MediaPlayer.LIVE_POINT)でのライブメディア開始が発生します。 デフォルトの動作を上書きできます。
seo-title: 特定の時間にストリームを開始
title: 特定の時間にストリームを開始
uuid: 5db73b50-0629-4fb1-8f12-6c88e4cd7109
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 1%

---


# 特定の時刻にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生開始、0のVODメディア開始、クライアントのライブポイント(MediaPlayer.LIVE_POINT)でのライブメディア開始が発生します。 デフォルトの動作を上書きできます。

1. `MediaPlayer.prepareToPlay`に位置を渡します。
1. ブラウザーTVSDKは、この位置をアセットの開始点として使用します。

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

