---
description: タイムライン更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
title: TimelineUpdatedEvent追加のリスナー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
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

