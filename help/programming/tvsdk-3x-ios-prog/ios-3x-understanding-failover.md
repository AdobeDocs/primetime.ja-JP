---
description: バリアントプレイリストに同じビットレートの複数のレンディションがあり、そのうちの1つのレンディションが機能を停止すると、フェイルオーバー処理が発生します。 TVSDKは、レンディションを切り替えます。
title: フェイルオーバー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# フェイルオーバー{#failover}

バリアントプレイリストに同じビットレートの複数のレンディションがあり、そのうちの1つのレンディションが機能を停止すると、フェイルオーバー処理が発生します。 TVSDKは、レンディションを切り替えます。

次の例は、同じビットレートのフェイルオーバーURLを持つバリアントプレイリストを示しています。

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

TVSDKは、バリアントプレイリストを読み込むとキューを作成し、同じビットレートのコンテンツのすべてのレンディションのURLを保持します。 URLのリクエストが失敗すると、TVSDKは、フェイルオーバーキューから同じビットレートの次のURLを使用します。 特定の失敗時に、TVSDKは、正しく機能するURLが見つかるか、使用可能なURLがすべて試行されるまで、使用可能なURLをすべて1回サイクルします。 TVSDKが使用可能なすべてのURLを試行し、URLが機能しない場合、TVSDKはコンテンツの再生試行を停止します。

フェイルオーバーはM3U8レベルでのみ発生し、次のことを意味します。

* VODの場合、フェイルオーバーは、再生の開始後ではなく、再生の試行が開始されたときにのみ発生できます。
* ライブストリーミングの場合、フェイルオーバーはストリームの途中で発生する可能性があります。

>[!TIP]
>
>フェイルオーバー処理は、Apple AV Foundationプレイヤーではなく、TVSDKが提供します。