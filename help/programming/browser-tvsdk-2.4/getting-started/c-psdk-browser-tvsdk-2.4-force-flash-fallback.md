---
description: ソースリストのforceflashフラグは、URLに対してFlashのフォールバックを強制します。 このURLの場合、AdobeFlash Playerを使用してコンテンツを再生できます。
title: メディアソースリストを使用したFlashフォールバックの強制
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# メディアソースリスト{#forcing-the-flash-fallback-using-the-media-source-list}を使用したFlashフォールバックの強制

ソースリストのforceflashフラグは、URLに対してFlashのフォールバックを強制します。 このURLの場合、AdobeFlash Playerを使用してコンテンツを再生できます。

メディアソースリスト（例えば`sources.js`ファイル内）では、`forceflash`を`true`に設定できます。 例：

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

