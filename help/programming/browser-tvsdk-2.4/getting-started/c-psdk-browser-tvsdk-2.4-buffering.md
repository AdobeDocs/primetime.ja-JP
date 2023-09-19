---
description: ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。
title: バッファリング
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# バッファリング{#buffering}

ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。

次をリッスン： `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` および `AdobePSDK.PSDKEventType.BUFFERING_END` イベント。 例：

```js
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_BEGIN,  
                        function (event) { 
                            buffering = true; 
                            // add buffering layer 
                        }); 
  
player.addEventListener(AdobePSDK.PSDKEventType.BUFFERING_END,  
                        function (event) { 
                           buffering = false; 
                           // remove buffering layer 
                        });
```

UI フレームワークは、次に示すように拡張できるデフォルトのバッファリングオーバーレイ動作実装を提供します。

```js
// Using UI Framework 
function myBufferingOverlayBehavior (element, configuration, player, localize, baseLog) { 
    return ptp.bufferingOverlayBehavior(element, configuration, player, localize, baseLog); 
} 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource:'Specify Resource URL', 
        bufferingOverlay: { 
            behavior: myBufferingOverlayBehavior, 
            classNames: 'ptp-buffering-overlay my_buffering_overlay_bar' 
        } 
    } 
 
}); 
```

DOM の結果は次のようになります。

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```
