---
description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-title: カスタムメタデータサポートの実装
title: カスタムメタデータサポートの実装
uuid: eb8d383f-a3e8-402d-84e8-f4209df0f954
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# カスタムメタデータサポートの実装{#implement-custom-metadata-support}

コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。

コールバック関数は、トラッキング呼び出しの直前に呼び出されるので、アプリケーションは、広告またはチャプターに固有のメタデータを添付できます。

コンテンツ、広告およびチャプターのコールバック関数を呼び出します。

```
// Video Metadata Block 
    vaTrackingMetadata.videoMetadataBlock = ^NSDictionary *() 
    { 
        return @{ 
                 @"myvideoid": @"1234", 
                 @"mysdkversion": [PTSDK apiVersion] 
                 }; 
    }; 
      
// Ad Metadata Block invoked on every ad start 
    vaTrackingMetadata.adMetadataBlock = ^NSDictionary *(PTAd *ad) 
    { 
        return @{ 
                 @"myadid": @"ad-1234", 
                 @"myad-sdkversion": [PTSDK apiVersion] 
                 }; 
    }; 
      
// Chapter Metadata Block invoked on every chapter start 
    vaTrackingMetadata.chapterMetadataBlock = ^NSDictionary *(PTVideoAnalyticsChapterData *chapter) 
    { 
        return @{ 
                 @"mychapterid": @"chapter-1234", 
                 @"mychapter-sdkversion": [PTSDK apiVersion] 
                 }; 
    };
```

