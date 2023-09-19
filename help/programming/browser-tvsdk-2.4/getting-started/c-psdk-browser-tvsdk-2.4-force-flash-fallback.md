---
description: ソースリストの forceflash フラグは、URL のFlashフォールバックを強制します。 この URL では、AdobeFlash Playerを使用してコンテンツを再生できます。
title: メディアソースリストを使用したFlashフォールバックの強制
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# メディアソースリストを使用したFlashフォールバックの強制{#forcing-the-flash-fallback-using-the-media-source-list}

ソースリストの forceflash フラグは、URL のFlashフォールバックを強制します。 この URL では、AdobeFlash Playerを使用してコンテンツを再生できます。

メディアソースリスト内 ( 例： `sources.js` ファイル )、 `forceflash` から `true`. 例：

```js
{ 
        "title":"Title of the item listed in the media source list",
        "description":"Description of the item listed in the media source list",
        "isLive":true,
        "content":[ 
            { 
                "format":"HLS",
                "url":"https://path_to_HLS_stream.m3u8"
            },
 
        ],
        "forceflash" : true
},
```
