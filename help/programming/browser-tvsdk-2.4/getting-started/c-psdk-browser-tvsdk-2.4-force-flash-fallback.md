---
description: ソースリストのforceflashフラグは、URLに対するFlashのフォールバックを強制します。 このURLの場合、Adobe Flash Playerを使用してコンテンツを再生できます。
seo-description: ソースリストのforceflashフラグは、URLに対するFlashのフォールバックを強制します。 このURLの場合、Adobe Flash Playerを使用してコンテンツを再生できます。
seo-title: メディアソースリストを使用したFlashフォールバックの強制
title: メディアソースリストを使用したFlashフォールバックの強制
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# メディアソースリストを使用したFlashフォールバックの強制{#forcing-the-flash-fallback-using-the-media-source-list}

ソースリストのforceflashフラグは、URLに対するFlashのフォールバックを強制します。 このURLの場合、Adobe Flash Playerを使用してコンテンツを再生できます。

メディアソースリスト（ファイル内など） `sources.js` で、をに設定で `forceflash` きます `true`。 例：

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

