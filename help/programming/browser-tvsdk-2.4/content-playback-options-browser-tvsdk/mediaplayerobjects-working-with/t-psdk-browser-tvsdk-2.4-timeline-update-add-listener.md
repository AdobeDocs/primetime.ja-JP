---
description: タイムラインの更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
title: TimelineUpdatedEvent のリスナーを追加
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# TimelineUpdatedEvent のリスナーを追加{#add-listeners-for-timelineupdatedevent}

タイムラインの更新に関する通知を受け取るには、適切なイベントリスナーを登録します。

タイムラインが更新されるたびに、 `MediaPlayer` ディスパッチ `AdobePSDK.TimelineEvent` タイプ `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`.
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
