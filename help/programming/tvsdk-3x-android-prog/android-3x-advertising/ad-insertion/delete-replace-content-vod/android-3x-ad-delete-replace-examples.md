---
description: 広告を削除および置換するプロセスの例を以下に示します。
title: 広告の削除と置換の例
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# 広告の削除と置換の例 {#examples-to-delete-and-replace-ads}

広告を削除および置換するプロセスの例を以下に示します。

以下に、 `DELETE_RANGE`:

```java
// Assume that the 3 timerange specs are obtained through external means,  
// like a CMS. Assume mediaPlayer is an instance of a properly configured MediaPlayer 
// Use these 3 timerange specs to populate the RepaceTimeRange list 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, o)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.DELETE_RANGE); 
 
// create a MediaResource instance 
MediaResource mediaResource = ... ; 
 
// create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// prepare the content for playback by calling replaceCurrentResource  
mediaPlayer.replaceCurrentResource(mediaResource, config);
```

以下に、 `REPLACE_RANGE`:

```java
// Assume that the 3 timerange specs are obtained through external means, like 
//  a CMS. Assume mediaPlayer is an instance of a properly configured MediaPlayer 
// Use these 3 timerange specs to populate the RepaceTimeRange list 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 10000)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 20000)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 30000)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.REPLACE_RANGE); 
 
// create a MediaResource instance 
MediaResource mediaResource = ... ; 
 
// create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config = new MediaPlayerItemConfig(getActivity() 
    .getApplicationContext()); 
 
// Set Auditude settings, which are used for ad replacement, for this  
//  MediaPlayerItemConfig instance, 
 
... 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// prepare the content for playback by calling replaceCurrentResource 
mediaPlayer.replaceCurrentResource(mediaResource, config);
```
