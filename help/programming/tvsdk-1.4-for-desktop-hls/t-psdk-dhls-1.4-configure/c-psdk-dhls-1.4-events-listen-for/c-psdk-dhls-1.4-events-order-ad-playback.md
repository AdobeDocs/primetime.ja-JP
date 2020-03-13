---
description: 再生に広告が含まれる場合、TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-description: 再生に広告が含まれる場合、TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-title: 広告イベントの順序
title: 広告イベントの順序
uuid: 34a6a606-2f2e-42de-88fd-c91202cafddf
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれる場合、TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する場合、イベントの順序は次のとおりです。

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* 広告の時間内のすべての広告に対して、次がディスパッチされます。

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` （広告の再生中に複数回）
   * `AdClickEvent.AD_CLICK` （クリックごと）
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

次の例は、広告再生イベントの一般的な流れを示しています。

```
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_STARTED, onAdBreakStarted); 
private function onAdBreakStarted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED, onAdBreakCompleted); 
private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
private function onAdStarted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_PROGRESS, onAdProgress); 
private function onAdProgress(event:AdBreakPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad;  
    var progress:uint = event.progress; 
    ... 
} 
mediaPlayer.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
private function onAdCompleted(event:AdPlaybackEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    ... 
} 
mediaPlayer.addEventListener(AdClickEvent.AD_CLICK, onAdClick); 
private function onAdClick(event:AdClickThroughEvent):void { 
    var adBreak:AdBreak = event.adBreak; 
    var ad:Ad = event.ad; 
    var info:AdClick = event.adClick; 
    ... 
} 
```

