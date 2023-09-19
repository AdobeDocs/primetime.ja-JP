---
description: ビデオコンテンツの再生時にキャプションを表示できます。
title: キャプション
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# キャプション{#captions}

ビデオコンテンツの再生時にキャプションを表示できます。

キャプションを処理するには、 `AdobePSDK.PSDKEventType.CAPTIONS_UPDATED` イベントリスナー：

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

UI フレームワークには、デフォルトのキャプション動作実装が用意されていますが、これは変更できます。 クローズドキャプションの動作は、デフォルトのクローズドキャプションの動作を拡張することでも変更できます。 例：

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
