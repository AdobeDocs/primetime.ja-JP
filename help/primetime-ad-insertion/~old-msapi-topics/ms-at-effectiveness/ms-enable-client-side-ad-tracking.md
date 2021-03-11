---
description: BootstrapURLリクエストにpttrackingmodeパラメーターとpttrackingversionパラメーターを追加することで、クライアント側の広告トラッキングを有効にできます。
title: クライアント側の広告トラッキングの有効化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 2%

---


# クライアント側の広告トラッキングを有効にする{#enable-client-side-ad-tracking}

BootstrapURLリクエストに`pttrackingmode`パラメーターと`pttrackingversion`パラメーターを追加することで、クライアント側の広告追跡を有効にできます。

クライアント側の広告トラッキングを有効にすると、トラッキングAPI URLを使用して広告トラッキングメタデータを取得することもできます。 詳しくは、[クエリパラメーター](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)を参照してください。

クライアント側の広告トラッキングを実行するには、トラッキングAPIのURLを使用します。

1. マニフェストサーバー追加リクエストURLに対する次のクエリパラメーター。

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

例：

```URL
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
