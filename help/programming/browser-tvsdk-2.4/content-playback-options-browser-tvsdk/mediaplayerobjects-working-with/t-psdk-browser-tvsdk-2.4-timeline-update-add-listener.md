---
description: タイムラインの更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-description: タイムラインの更新に関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-title: TimelineUpdatedEventのリスナーの追加
title: TimelineUpdatedEventのリスナーの追加
uuid: 7d742e15-5a55-4155-93a7-7b79f21c1472
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# TimelineUpdatedEventのリスナーの追加{#add-listeners-for-timelineupdatedevent}

タイムラインの更新に関する通知を受け取るには、適切なイベントリスナーを登録します。

タイムラインが更新されるたびに、タイ `MediaPlayer` プでディス `AdobePSDK.TimelineEvent` パッチされま `AdobePSDK.PSDKEventType.TIMELINE_UPDATED`す。
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

