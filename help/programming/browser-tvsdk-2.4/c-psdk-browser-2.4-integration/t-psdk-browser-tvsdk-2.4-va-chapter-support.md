---
title: チャプターサポートの実装
description: チャプターサポートの実装
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---


# チャプターサポートの実装{#implement-chapter-support}

チャプターは、各広告の時間の間隔として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間は、最初のチャプターとして定義されます。 カスタムチャプターを使用して、ブラウザーTVSDKベースのアプリケーションで、ビデオトラッキング用のチャプターを定義および追跡できます。 カスタムチャプターは、アプリケーションによって管理され、CMSデータまたはアプリケーションがチャプターを定義する別の方法に基づいています。

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

