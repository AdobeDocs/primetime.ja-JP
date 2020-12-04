---
description: BootstrapURLリクエストにpttrackingmodeパラメーターとpttrackingversionパラメーターを追加することで、クライアント側の広告トラッキングを有効にできます。
seo-description: BootstrapURLリクエストにpttrackingmodeパラメーターとpttrackingversionパラメーターを追加することで、クライアント側の広告トラッキングを有効にできます。
seo-title: クライアント側の広告トラッキングの有効化
title: クライアント側の広告トラッキングの有効化
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 1%

---


# クライアント側の広告トラッキングを有効にする{#enable-client-side-ad-tracking}

BootstrapURLリクエストに`pttrackingmode`パラメーターと`pttrackingversion`パラメーターを追加することで、クライアント側の広告追跡を有効にできます。

クライアント側の広告トラッキングを有効にすると、トラッキングAPI URLを使用して広告トラッキングメタデータを取得することもできます。 詳しくは、[クエリパラメーター](../../msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)を参照してください。

クライアント側の広告トラッキングを実行するには、トラッキングAPIのURLを使用します。

1. マニフェストサーバー追加リクエストURLに対する次のクエリパラメーター。

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

例：

```
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
