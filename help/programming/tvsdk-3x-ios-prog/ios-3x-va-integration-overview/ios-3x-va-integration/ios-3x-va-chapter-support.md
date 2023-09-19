---
title: チャプターサポートの実装
description: チャプターサポートの実装
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# チャプターサポートの実装 {#implement-chapter-support}

TVSDK ベースのアプリケーションで、ビデオトラッキングのチャプターを次の方法で定義および追跡できます。

* デフォルトのチャプター。TVSDK が内部的に管理します。

  チャプターは、各広告ブレークの間の時間として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間は、最初のチャプターとして定義されます。
* カスタムチャプター。アプリケーションで管理され、CMS データまたはチャプターを定義するためにアプリケーションが使用する別の方法に基づいています。

  デフォルトのチャプターまたはカスタムチャプターを定義し、追跡します。

  ```
  // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
  
      vaTrackingMetadata.enableChapterTracking = YES; 
  
  // For custom chapter definitions, provide an array of chapters through the metadata:  
  // For example, 3 chapters of 60 second duration each: 
  
      NSMutableArray *chapters = [[[NSMutableArray alloc] init] autorelease]; 
  
      int chapterDuration = 60; 
      for (int i = 0; i < 3; i++) 
      { 
          PTVideoAnalyticsChapterData *chapterData =  
            [[[PTVideoAnalyticsChapterData alloc] init] autorelease]; 
          chapterData.name = [NSString stringWithFormat:@"chapter_%d", (i+1)]; 
          chapterData.range =  
            CMTimeRangeMake(CMTimeMakeWithSeconds(i * chapterDuration, 10000),  
            CMTimeMakeWithSeconds(chapterDuration, 10000)); 
  
          [chapters addObject:chapterData]; 
      } 
  
      vaTrackingMetadata.chapters = chapters; 
  
  // For default chapters, the application must not set custom chapters on the tracking metadata  
  // and simply enable chapters to be tracked by setting the boolean value as defined above.
  ```
