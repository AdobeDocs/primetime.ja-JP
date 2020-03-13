---
seo-title: カスタマイズされたVODアセットの例
title: カスタマイズされたVODアセットの例
uuid: 21e83b47-d7e2-4a2d-8a0b-80dd09e253a8
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# カスタマイズされたVODアセットの例 {#example-of-a-customized-vod-asset}

カスタマイズされたVODアセットの例を次に示します。

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

* ファイルにタ `#EXT-X-ASSET` グや、登録したその他のカスタムタグ名のセットが存在する場合の通知。
* タグまたはその他のカ `#EXT-X-AD` スタムタグ名がストリーム内に見つかった場合に広告を挿入します。

