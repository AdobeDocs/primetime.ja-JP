---
description: ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。
seo-description: ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。
seo-title: バッファリング
title: バッファリング
uuid: da9498ee-c736-4093-97a2-250d3ad56d49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 2%

---


# バッファリング{#buffering}

ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。

`AdobePSDK.PSDKEventType.BUFFERING_BEGIN`と`AdobePSDK.PSDKEventType.BUFFERING_END`イベントをリッスンします。 例：

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

UIフレームワークには、次に示すように拡張できる、デフォルトのバッファリングオーバーレイ動作の実装が用意されています。

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

結果のDOMは次のようになります。

```
<div id=" videoDiv" class="ptp-root-element"> 
<div name="videoPlayer" value="videoPlayer" class="ptp-main-video-div-style"> 
<div name="bufferingOverlay" value="bufferingOverlay" class="ptp-buffering-overlay my_buffering_overlay_bar'"></div> 
</div> 
</div> 
```

