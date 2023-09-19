---
description: ブラウザー TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。
title: 再生イベントの順序
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# 再生イベントの順序{#order-of-playback-events}

ブラウザー TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

<!--<a id="section_D247A5873A854A079EFA6AC2E80AB894"></a>-->

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* を介してメディアリソースを正常に読み込んだ場合 `replaceCurrentResource`の場合、イベントの順序は次のとおりです。

   * `AdobePSDK.MediaPlayerStatusChangeEvent` 次を使用 `event.status =`

      * `MediaPlayerStatus.INITIALIZING`
      * `MediaPlayerStatus.INITIALIZED`

* を使用して再生を準備する場合 `MediaPlayer.prepareToPlay`の場合、イベントの順序は次のとおりです。

   * `AdobePSDK.MediaPlayerStatusChangeEvent` 次を使用 `event.status =`

      * `MediaPlayerStatus.PREPARING`
      * `MediaPlayerStatus.PREPARED`

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

次の例に、イベントの一般的な流れを示します。

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                 onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
            console.log("Player Status: INITIALIZING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            console.log("Player Status: INITIALIZED"); 
            player.prepareToPlay(); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARING: 
            console.log("Player Status: PREPARING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
            console.log("Player Status: PREPARED"); 
            if (autoPlay) { 
                player.play(); 
            } 
            else { 
                dispatchEvent(ReferencePlayer.Events.PreparedEvent,  
                              {target: this}); 
            } 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PLAYING: 
            console.log("Player Status: PLAYING"); 
            //update UI play/pause to show pause icon 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PAUSED: 
            console.log("Player Status: PAUSED"); 
            //update UI play/pause to show play icon &  
            //display pause icon over video 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.SEEKING: 
            console.log("Player Status: SEEKING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.COMPLETE: 
            console.log("Player Status: COMPLETE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.RELEASED: 
            console.log("Player Status: RELEASED"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            console.log("Player Status: ERROR"); 
            break; 
    } 
};
```
