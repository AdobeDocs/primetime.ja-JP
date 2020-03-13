---
description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-description: コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。
seo-title: カスタムメタデータのサポートの実装
title: カスタムメタデータのサポートの実装
uuid: 2186db58-10b0-43a6-840f-53ab289843ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタムメタデータのサポートの実装{#implement-custom-metadata-support}

コールバック関数を使用して、コンテンツ、広告およびチャプタートラッキングの呼び出しに関するカスタムメタデータを提供できます。

コールバック関数は、トラッキング呼び出しがおこなわれる直前に呼び出されるので、アプリケーションは、広告またはチャプターに固有のメタデータを添付できます。

1. コンテンツ、広告およびチャプターのコールバック関数を呼び出します。

   ```
   // Video Metadata Block 
   vaMetadata.videoMetadataBlock = function():Object { 
       return {"myvideoid":"1234", "mysdkversion":Version.version} 
   }; 
   
   // Ad Metadata Block invoked on every ad start 
   vaMetadata.adMetadataBlock = function(ad:Ad):Object { 
       return {"myadid":"ad-1234", "myad-sdkversion":Version.version} 
   }; 
   
   // Chapter Metadata Block invoked on every chapter start 
   vaMetadata.chapterMetadataBlock = function(chapter:VideoAnalyticsChapterData) { 
       return {"mychapterid":"chapter-1234", "mychapter-sdkversion":Version.version} 
   };
   ```

