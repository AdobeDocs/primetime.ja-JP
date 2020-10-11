---
title: CDNの統合
description: CDNの統合
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# CDNの統合 {#integrating-cdn}

PrimetimeAd Insertionは、ビデオチャンク自体ではなく、クライアントアプリケーションとマニフェスト間のプロキシとして機能します。 BootstrapAPIを使用して、選択したCDNにコンテンツをデプロイし、PrimetimeAd InsertionにURLを渡します。<!-- For integration details, see [Supported CDNs](supported-cdns.md).-->

## サポートされるCDNトークン化スキーム {#cdn-tokenization-schemes}

CDNには、フラグメント認証のための異なるトークン化スキームが用意されていることがよくあります。 PrimetimeAd Insertionは、次のような主要なCDNネットワークをネイティブでサポートします。

* Akamai
* リメライト
* Centurylink / Level3
* サポートされるCDNの完全なリストについては、Primetimeのサポート担当者にお問い合わせください。

このパラメーターについて詳しくは、 `pttoken`[BootstrapAPIパラメーターの説明を参照してください](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。

## コンテンツCDNから配信する広告の設定 {#configure-ad-deliver-from-cdn}

同じCDNから広告とコンテンツを配信して、コンテンツのアフィニティを維持したり、広告ブロッカーを避けたり、クライアントアプリケーションから必要な接続数を最適化したりする場合があります。 PrimetimeAd Insertionは、フラグメントをコンテンツCDNにマッピングするためのフラグメント再記述ルールをサポートしています。

<!--## Increase start-up performance with your CDN {#increase-startup-performance}

For more information, see [Optimizing start-up](optimize-video-startup-time.md).-->

## マルチCDN機能 {#enable-multi-cdn-fetures}

マルチCDN機能を有効にする場合は、Primetimeのサポート担当者にお問い合わせください。
