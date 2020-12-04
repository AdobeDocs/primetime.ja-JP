---
description: 'null'
seo-description: 'null'
seo-title: チャプターサポートの実装
title: チャプターサポートの実装
uuid: f62a8244-6393-4a38-9ae2-8ac31f6a8a06
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# チャプターサポートの実装{#implement-chapter-support}

TVSDKベースのアプリケーションで、ビデオトラッキング用の&#x200B;*カスタム*&#x200B;チャプターを定義して追跡できます。

カスタムチャプターは、アプリケーションによって管理され、CMSデータや、アプリケーションがチャプターを定義する際に使用する別の方法に基づいています。

>[!CAUTION]
>
>デフォルトチャプターは、2.5 Android TVSDKではサポートされていません。

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

