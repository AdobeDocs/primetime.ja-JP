---
description: バリアントプレイリストに同じビットレートの複数のレンディションが含まれ、1 つのレンディションの動作が停止した場合に、フェイルオーバー処理が発生します。 TVSDK はレンディションを切り替えます。
title: フェイルオーバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# フェイルオーバー{#failover}

バリアントプレイリストに同じビットレートの複数のレンディションが含まれ、1 つのレンディションの動作が停止した場合に、フェイルオーバー処理が発生します。 TVSDK はレンディションを切り替えます。

次の例は、同じビットレートのフェールオーバー URL を持つバリアントプレイリストを示しています。

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

TVSDK は、バリアントプレイリストを読み込むと、同じビットレートのコンテンツのすべてのレンディションの URL を保持するキューを作成します。 URL のリクエストが失敗した場合、 TVSDK は、フェイルオーバーキューから同じビットレートの次の URL を使用します。 特定の障害が発生した場合、 TVSDK は、正しく機能する URL が見つかるか、使用可能な URL がすべて試行されるまで、使用可能な URL をすべて 1 回繰り返します。 TVSDK が使用可能なすべての URL を試行し、URL が機能しなかった場合、 TVSDK はコンテンツの再生を停止します。

フェイルオーバーは M3U8 レベルでのみ発生します。つまり、次のことを意味します。

* VOD の場合、フェイルオーバーは、再生が開始された後ではなく、再生が開始されたときにのみ発生します。
* ライブストリーミングの場合、ストリームの途中でフェイルオーバーが発生する可能性があります。

>[!TIP]
>
>Apple AV Foundation プレーヤーではなく、 TVSDK がフェイルオーバー処理を提供します。
