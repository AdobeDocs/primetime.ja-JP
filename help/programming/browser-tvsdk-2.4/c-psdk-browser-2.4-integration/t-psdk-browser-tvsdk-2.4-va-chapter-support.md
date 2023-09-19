---
title: チャプターサポートの実装
description: チャプターサポートの実装
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---

# チャプターサポートの実装{#implement-chapter-support}

チャプターは、各広告ブレークの間の時間として定義されます。 例えば、プリロール広告の時間と最初のミッドロールの間の時間は、最初のチャプターとして定義されます。 カスタムチャプターを使用して、Browser TVSDK ベースのアプリケーションで、ビデオ追跡のチャプターを定義および追跡できます。 カスタムチャプターは、アプリケーションによって管理され、CMS データまたはチャプターを定義するためにアプリケーションが使用する別の方法に基づいています。

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
