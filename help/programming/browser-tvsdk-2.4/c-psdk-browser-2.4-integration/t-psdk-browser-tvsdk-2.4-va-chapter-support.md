---
description: 'null'
seo-description: 'null'
seo-title: チャプターサポートの実装
title: チャプターサポートの実装
uuid: 70f10621-febe-4443-84e7-ce95bec53377
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# チャプターサポートの実装{#implement-chapter-support}

チャプターは、各広告の時間の間隔として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間が最初のチャプターとして定義されます。 カスタムチャプターを使用して、ブラウザーTVSDKベースのアプリケーションでビデオトラッキングのチャプターを定義し、追跡できます。 カスタムチャプターは、アプリケーションによって管理され、CMSデータまたはアプリケーションがチャプターを定義する別の方法に基づいています。

1. カスタムチャプターを定義し、追跡します。

   ```js
   vaObj.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata: 
   // For example: 3 chapters of 60 second duration each 
   var chapters = []; 
   var chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       var chapterData = new AdobePSDK.VA.VideoAnalyticsChapterData("chapter_" + (i+1), i * chapterDuration, chapterDuration, (i+1)); 
       chapters.push(chapterData); 
   } 
   
   vaObj.chapters = chapters;
   ```

