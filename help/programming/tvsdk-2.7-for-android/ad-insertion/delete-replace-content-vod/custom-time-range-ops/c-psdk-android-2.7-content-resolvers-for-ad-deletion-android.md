---
description: 複数のコンテンツリゾルバーを使用して、異なるタイムライン操作を処理できます。
seo-description: 複数のコンテンツリゾルバーを使用して、異なるタイムライン操作を処理できます。
seo-title: 広告削除/置換用のコンテンツリゾルバー
title: 広告削除/置換用のコンテンツリゾルバー
uuid: ed168c52-ab7b-4fe6-8775-eb18018dc249
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# 広告削除/置換用のコンテンツリゾルバー {#content-resolvers-for-ad-deletion-replacement}

複数のコンテンツリゾルバーを使用して、異なるタイムライン操作を処理できます。

```java
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
    List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
    MediaPlayerItemConfig itemConfig = item.getConfig(); 
    if(itemConfig) { 
        CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
        if (customRanges) { 
            List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
 
            if (timeRanges && timeRanges.size() > 0) { 
                //CustomRangeResolver is activated by the presence of CustomRanges 
                resolvers.add(new CustomRangeResolver()); 
            } 
        } 
        AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
        if (metadata) { 
            if (metadata instanceOf AuditudeSettings)  
            resolvers.add(new AuditudeResolver(getContext());                                      
        } 
    } 
    //Add your custom resolver if any 
    resolvers.add(MyOpportunityGenerator(item)); 
    return resolvers; 
} 
```

