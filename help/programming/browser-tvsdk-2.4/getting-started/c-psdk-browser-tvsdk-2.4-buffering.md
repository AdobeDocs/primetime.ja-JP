---
description: ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。
seo-description: ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。
seo-title: バッファ
title: バッファ
uuid: da9498ee-c736-4093-97a2-250d3ad56d49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# バッファ{#buffering}

ビジュアルを設定して、コンテンツがバッファリングされていることをユーザーに通知できます。

イベントをリッ `AdobePSDK.PSDKEventType.BUFFERING_BEGIN` スンし `AdobePSDK.PSDKEventType.BUFFERING_END` ます。 例：

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

UIフレームワークは、次に示すように拡張可能な、デフォルトのバッファリングオーバーレイ動作の実装を提供します。

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

