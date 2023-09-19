---
description: コールバック関数を使用して、コンテンツ、広告、チャプタートラッキングコールに関するカスタムメタデータを提供できます。
title: カスタムメタデータサポートの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# カスタムメタデータサポートの実装 {#implement-custom-metadata-support}

コールバック関数を使用して、コンテンツ、広告、チャプタートラッキングコールに関するカスタムメタデータを提供できます。

コールバック関数は、トラッキングコールがおこなわれる直前に呼び出されるので、アプリケーションは、広告またはチャプターに固有のメタデータをアタッチできます。

コンテンツ、広告およびチャプターに対してコールバック関数を呼び出します。

```java
// Video Metadata Block 
vaMetadata.setVideoMetadataBlock(new VideoAnalyticsMetadata.VideoMetadataBlock() { 
    @Override 
    public HashMap<String, String> call() { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myvideoid", "1234"); 
        result.put("mysdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Ad Metadata Block invoked on every ad start 
vaMetadata.setAdMetadataBlock(new VideoAnalyticsMetadata.AdMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(Ad ad) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myadid", "ad-1234"); 
        result.put("myad-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Chapter Metadata Block invoked on every chapter start 
vaMetadata.setChapterMetadataBlock(new VideoAnalyticsMetadata.ChapterMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(VideoAnalyticsChapterData chapter) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("mychapterid", "chapter-1234"); 
        result.put("mychapter-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
});
```
