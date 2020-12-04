---
description: タイムライン更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-description: タイムライン更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-title: TimelineUpdatedEvent追加のリスナー
title: TimelineUpdatedEvent追加のリスナー
uuid: 7d742e15-5a55-4155-93a7-7b79f21c1472
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# TimelineUpdatedEvent追加{#add-listeners-for-timelineupdatedevent}のリスナー

タイムライン更新に関する通知を受け取るには、適切なイベントリスナーを登録します。

タイムラインが更新されるたびに、`MediaPlayer`は`AdobePSDK.PSDKEventType.TIMELINE_UPDATED`型で`AdobePSDK.TimelineEvent`をディスパッチします。
1. 適切なリスナーを実装します。

   ```js
   function onTimelineUpdatedEvent(event) { 
       var timelineMarkers = event.timeline.timelineMarkers; 
       //add code to remove old timeline markers from scrub-bar. 
       var range = player.playbackRange; 
       //iterate through the list of timelineMarkers 
       for(var i = 0; i < timelineMarkers.length; i++) 
       { 
           var markerLocalTime = timelineMarkers[i].localRange.begin; 
           var markerVirtualTime = timelineMarkers[i].virtualRange.begin; 
           var duration = timelineMarkers[i].duration; 
        // add code to draw a particular marker on scrub-bar 
       }      
   }
   ```

1. イベントリスナーを登録します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMELINE_UPDATED,  
       onTimelineUpdatedEvent);
   ```

