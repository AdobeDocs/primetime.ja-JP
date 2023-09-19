---
title: カスタマイズされた VOD アセットの例
description: カスタマイズされた VOD アセットの例
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# カスタマイズされた VOD アセットの例 {#example-of-a-customized-vod-asset}

カスタマイズされた VOD アセットの例を次に示します。

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

アプリケーションでは、次のシナリオを設定できます。

* 通知： `#EXT-X-ASSET` タグ、または購読したその他のカスタムタグ名のセットがファイルに存在します。
* 広告を挿入する `#EXT-X-AD` タグ、またはその他のカスタムタグ名がストリーム内に見つかります。
