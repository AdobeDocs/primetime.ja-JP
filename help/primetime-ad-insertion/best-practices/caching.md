---
title: キャッシュ
description: キャッシュ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# HTTP キャッシュ {#caching}

PrimetimeAd Insertionは、広告クリエイティブおよびコンテンツを取得する際に、デフォルトで HTTP キャッシュ制御ヘッダーに従います。  これにより、すべてのクライアントをまたいで CDN に対して PrimetimeAd Insertionがおこなうのに必要なネットワークリクエストの量を大幅に削減できます。  キャッシュの場合、Adobeでは次の設定を推奨し、HTTP ヘッダーの送信を含めます。 `max-age` を CDN から取得します。  CDN 担当者に連絡して、ビデオストリームおよび広告ストリームでこれらのヘッダーを有効にしてもらってください。

## ライブ/リニアコンテンツの場合 {#caching-live-linear-content}

* マスターマニフェスト： 24 時間、または Cache-Control: max-age=86400
* メディアマニフェスト： 1 秒、または Cache-Control: max-age=1

## VOD コンテンツの場合 {#caching-vod-content}

* マスターマニフェスト： 24 時間、または Cache-Control: max-age=86400
* メディアマニフェスト： 24 時間、または Cache-Control: max-age=86400
