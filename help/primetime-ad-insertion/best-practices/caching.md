---
title: キャッシュ
description: null
translation-type: tm+mt
source-git-commit: 76dc54fabdae400ad708ba83fcf6f7fd5caa2b22
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# HTTPキャッシュ{#caching}

PrimetimeAd Insertionは、デフォルトで、広告クリエイティブおよびコンテンツをフェッチする際に、HTTPキャッシュ制御ヘッダーに従います。  これにより、PrimetimeAd InsertionがすべてのクライアントのCDNに対して行うために必要なネットワークリクエストの量を大幅に削減できます。  キャッシュの場合、Adobeでは次の設定を推奨し、CDNからHTTPヘッダー`max-age`を送信することを推奨します。  ビデオストリームおよび広告ストリームでこれらのヘッダーを有効にするには、CDNの担当者にお問い合わせください。

## ライブ/リニアコンテンツ{#caching-live-linear-content}

* マスターマニフェスト：24時間、またはCache-Control:max-age=86400
* メディアマニフェスト：1秒またはCache-Control:max-age=1

## VODコンテンツ用{#caching-vod-content}

* マスターマニフェスト：24時間、またはCache-Control:max-age=86400
* メディアマニフェスト：24時間、またはCache-Control:max-age=86400
