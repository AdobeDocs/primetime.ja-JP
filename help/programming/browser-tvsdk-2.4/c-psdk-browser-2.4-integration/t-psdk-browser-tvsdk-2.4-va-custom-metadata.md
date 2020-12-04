---
description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-title: カスタムメタデータサポートの実装
title: カスタムメタデータサポートの実装
uuid: 6e23311c-a393-4485-919e-4cf6412789b1
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# カスタムメタデータサポートの実装{#implement-custom-metadata-support}

コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。

コールバック関数は、トラッキング呼び出しの直前に呼び出されるので、アプリケーションは、広告またはチャプターに固有のメタデータを添付できます。

1. コンテンツ、広告およびチャプターのコールバック関数を呼び出します。

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

