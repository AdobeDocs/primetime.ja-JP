---
description: 複数のコンテンツリゾルバーを使用して、異なるタイムライン操作を処理できます。
title: 広告削除/置換用のコンテンツリゾルバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '34'
ht-degree: 0%

---

# 広告削除/置換用のコンテンツリゾルバー {#content-resolvers-for-ad-deletion-replacement}

複数のコンテンツリゾルバーを使用して、異なるタイムライン操作を処理できます。

```java
List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
MetadataNode metadata = (MetadataNode) resource.getMetadata(); 
if (metadata != null) { 
    if (metadata.containsKey(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue())) { 
        String timeRangeType = metadata.getValue(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue()); 
        if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_DELETE)) { 
            contentResolvers.add(new DeleteContentResolver()); 
        } else if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_REPLACE)) { 
            contentResolvers.add(new DeleteContentResolver()); 
        } else if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_MARK)) { 
            contentResolvers.add(new CustomAdMarkersContentResolver()); 
        } 
    } 
    if (metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue())) { 
        contentResolvers.add(new AuditudeResolver(context)); 
    } else if (metadata.containsKey(DefaultMetadataKeys.JSON_METADATA_KEY.getValue())) { 
        contentResolvers.add(new MetadataResolver()); 
    } 
} 
return contentResolvers;
```
