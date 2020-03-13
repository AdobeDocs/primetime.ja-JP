---
description: 'null'
seo-description: 'null'
seo-title: チャプターサポートの実装
title: チャプターサポートの実装
uuid: 6e2c3994-d28b-489f-ae60-9b876125a871
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# チャプターサポートの実装 {#implement-chapter-support}

TVSDKベースのアプリケーションで、ビ *デオトラッキングの* カスタムチャプターを定義し、追跡できます。

カスタムチャプターは、アプリケーションによって管理され、CMSデータまたはアプリケーションがチャプターを定義する別の方法に基づいています。

>[!CAUTION]
>
>デフォルトのチャプターは、3.0 Android TVSDKではサポートされていません。

カスタムチャプターを定義し、追跡します。

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
