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

1. コンテンツ、広告およびチャプターに対してコールバック関数を呼び出します。

   ```js
   vaObj.videoMetadataBlock = function() { 
       return { 
           "name" : "my-video", 
           "genre" : "comedy" 
       }; 
   } 
   
   vaObj.adMetadataBlock = function(ad) { 
       return { 
           "name" : "my-ad", 
           "category" : "automotive" 
       }; 
   } 
   
   vaObj.chapterMetadataBlock = function(chapter) { 
       return { 
           "name" : "my-chapter", 
           "type" : "quartile" 
       }; 
   }
   ```
