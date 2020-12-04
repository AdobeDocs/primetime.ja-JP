---
description: 再生に広告が含まれる場合、TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。
seo-description: 再生に広告が含まれる場合、TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。
seo-title: 広告イベントの順序
title: 広告イベントの順序
uuid: 34a6a606-2f2e-42de-88fd-c91202cafddf
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれる場合、TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する場合、イベントの順序は次のとおりです。

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* 次は、広告の時間内の各広告に対してディスパッチされます。

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` （広告の再生中に複数回）
   * `AdClickEvent.AD_CLICK` （クリックごと）
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

次の例に、広告再生イベントの一般的な流れを示します。

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

