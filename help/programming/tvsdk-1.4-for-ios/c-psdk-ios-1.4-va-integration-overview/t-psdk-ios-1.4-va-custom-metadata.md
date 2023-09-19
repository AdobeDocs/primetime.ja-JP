---
description: コールバック関数を使用して、コンテンツ、広告、チャプタートラッキングコールに関するカスタムメタデータを提供できます。
title: カスタムメタデータサポートの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# カスタムメタデータサポートの実装{#implement-custom-metadata-support}

コールバック関数を使用して、コンテンツ、広告、チャプタートラッキングコールに関するカスタムメタデータを提供できます。

コールバック関数は、トラッキングコールがおこなわれる直前に呼び出されるので、アプリケーションは、広告またはチャプターに固有のメタデータをアタッチできます。

コンテンツ、広告およびチャプターに対してコールバック関数を呼び出します。

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
