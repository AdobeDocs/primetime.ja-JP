---
title: チャプターサポートの実装
description: チャプターサポートの実装
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# チャプターサポートの実装 {#implement-chapter-support}

定義して追跡できます *カスタム* TVSDK ベースのアプリケーションでのビデオトラッキングの章です。

カスタムチャプターは、アプリケーションによって管理され、CMS データに基づくか、アプリケーションがチャプターを定義するために使用する別の方法に基づきます。

>[!CAUTION]
>
>2.5 Android TVSDK では、デフォルトのチャプターはサポートされていません。

1. カスタムチャプターを定義し、追跡します。

   ```java
   // First, enable chapter tracking by setting   
   // enableChapterTracking to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide  
   // an array list of chapters through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters =  
     new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   ```
