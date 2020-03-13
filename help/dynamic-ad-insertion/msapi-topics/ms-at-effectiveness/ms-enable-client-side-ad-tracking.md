---
description: ブートストラップURLリクエストにpttrackingmodeおよびpttrackingversionパラメーターを追加することで、クライアント側の広告追跡を有効にできます。
seo-description: ブートストラップURLリクエストにpttrackingmodeおよびpttrackingversionパラメーターを追加することで、クライアント側の広告追跡を有効にできます。
seo-title: クライアント側の広告追跡の有効化
title: クライアント側の広告追跡の有効化
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# クライアント側の広告追跡の有効化 {#enable-client-side-ad-tracking}

ブートストラップURLリクエストにパラメーターとパラメーターを追加することで、ク `pttrackingmode` ライアント `pttrackingversion` 側の広告追跡を有効にすることができます。

クライアント側の広告トラッキングを有効にすると、トラッキングAPI URLを使用して広告トラッキングメタデータを取得することもできます。 詳しくは、「クエリパラメーター」を参 [照してくださ](../../msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)い。

クライアント側の広告トラッキングを実行するには、トラッキングAPIのURLを使用します。

1. マニフェストサーバーリクエストURLに次のクエリパラメーターを追加します。

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

例：

```
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
