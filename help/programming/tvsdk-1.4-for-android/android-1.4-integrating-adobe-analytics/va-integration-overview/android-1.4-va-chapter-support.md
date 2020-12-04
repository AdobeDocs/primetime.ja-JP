---
description: 'null'
seo-description: 'null'
seo-title: チャプターサポートの実装
title: チャプターサポートの実装
uuid: 5b39e494-85ad-43bb-ab56-a55797aa4ef7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# チャプターサポートの実装{#implement-chapter-support}

以下の方法で、TVSDKベースのアプリケーションでビデオトラッキング用のチャプターを定義し、追跡できます。

* デフォルトチャプター。TVSDKが内部的に管理します。

   チャプターは、各広告の時間の間隔として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間は、最初のチャプターとして定義されます。
* カスタムチャプター。アプリケーションで管理され、CMSデータまたはアプリケーションがチャプターを定義する際に使用する別の方法に基づいています。

1. デフォルトチャプターまたはカスタムチャプターを定義し、追跡します。

   ```java
   // First, enable chapter tracking by setting  
   // the Boolean 'enableChapterTracking' to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide an array list of chapters  
   // through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters = new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   // For default chapters, the application must not set  
   // custom chapters on the tracking metadata 
   // and simply enable chapters to be tracked by setting  
   // the boolean value as defined above.
   ```
