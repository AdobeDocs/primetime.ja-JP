---
title: チャプターサポートの実装
description: チャプターサポートの実装
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# チャプターサポートの実装{#implement-chapter-support}

以下の方法で、TVSDKベースのアプリケーションでビデオトラッキング用のチャプターを定義し、追跡できます。

* デフォルトチャプター。TVSDKが内部的に管理します。

   チャプターは、各広告の時間の間隔として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間は、最初のチャプターとして定義されます。
* カスタムチャプター。アプリケーションで管理され、CMSデータまたはアプリケーションがチャプターを定義する際に使用する別の方法に基づいています。

   デフォルトチャプターまたはカスタムチャプターを定義し、追跡します。

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
