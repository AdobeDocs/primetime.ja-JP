---
description: 再生に広告が含まれている場合、 TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。
title: 広告イベントの順序
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれている場合、 TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する際のイベントの順序は次のとおりです。

* `AdBreakPlaybackEvent.AD_BREAK_STARTED`
* 広告ブレークの各広告に対して、次の情報がディスパッチされます。

   * `AdPlaybackEvent.AD_STARTED`
   * `AdPlaybackEvent.AD_PROGRESS` （広告の再生中に複数回）
   * `AdClickEvent.AD_CLICK` （クリックごと）
   * `AdPlaybackEvent.AD_COMPLETED`

* `AdBreakPlaybackEvent.AD_BREAK_COMPLETED`

次の例に、広告再生イベントの一般的な進行を示します。

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
