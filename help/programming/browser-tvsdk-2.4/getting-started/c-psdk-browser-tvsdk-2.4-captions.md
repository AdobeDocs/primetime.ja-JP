---
description: ビデオコンテンツの再生時にキャプションを表示できます。
seo-description: ビデオコンテンツの再生時にキャプションを表示できます。
seo-title: キャプション
title: キャプション
uuid: 4dedcedc-50e5-4983-bb09-3f316337117e
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 3%

---


# キャプション{#captions}

ビデオコンテンツの再生時にキャプションを表示できます。

キャプションを処理するには、 `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` イベントリスナーを追加する必要があります。

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.CAPTIONS_UPDATED,  
                        onCaptionsUpdateEvent); 
... 
function onCaptionsUpdateEvent (event) { 
  // code to show the captions icon and any settings button. 
<pre>
   For example: 
  var btnCC = document.getElementById("btn_captions"); 
   btnCC.classList.remove("invisible"); 
   
  var btnSettings = document.getElementById("btn_settings"); 
   btnSettings.classList.remove("invisible"); 
 } 
</pre>
```

UIフレームワークには、デフォルトのキャプション動作実装が用意されており、これは変更できます。 クローズドキャプションの動作は、デフォルトのクローズドキャプションの動作を拡張することでも変更できます。 例：

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer(‘.videoDiv', { 
player:{ 
    mediaResource: 'Specify Resource URL', 
    ccStyle: { 
    font:AdobePSDK.TextFormat.CURSIVE, 
    fontColor:AdobePSDK.TextFormat.BRIGHT_WHITE, 
    edgeColor:AdobePSDK.TextFormat.BLUE, 
    backgroundColor:AdobePSDK.TextFormat.BLACK, 
    fillColor:AdobePSDK.TextFormat.BLUE, 
    size:AdobePSDK.TextFormat.MEDIUM, 
    fontOpacity:100, 
    backgroundOpacity:1, 
    fillOpacity:1 
   } 
 } 
 
}); 
```
