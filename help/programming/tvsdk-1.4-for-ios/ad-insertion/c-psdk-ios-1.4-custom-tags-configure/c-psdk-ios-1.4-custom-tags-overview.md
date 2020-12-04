---
seo-title: カスタマイズされたVODアセットの例
title: カスタマイズされたVODアセットの例
uuid: e0dfaa72-d62f-4fb3-b7c5-ad94f0dc7ce0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# カスタマイズされたVODアセットの例{#example-of-a-customized-vod-asset}

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

アプリケーションで次のシナリオを設定できます。

* `#EXT-X-ASSET`タグまたはサブスクライブした他のカスタムタグ名のセットがファイルに存在する場合の通知。
* `#EXT-X-AD`タグまたは他のカスタムタグ名がストリーム内で見つかった場合に広告を挿入します。

