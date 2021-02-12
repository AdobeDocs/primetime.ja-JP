---
title: CDNの統合
description: CDNの統合
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# CDNを統合{#integrating-cdn}

PrimetimeAd Insertionは、ビデオチャンク自体ではなく、クライアントアプリケーションとマニフェスト間のプロキシとして機能します。 BootstrapAPIを使用して、選択したCDNにコンテンツをデプロイし、PrimetimeAd InsertionにURLを渡します。 統合の詳細については、[サポートされているCDN](/help/primetime-ad-insertion/technical-reference/supported-cdns.md)を参照してください。

## サポートされるCDNトークン化スキーム{#cdn-tokenization-schemes}

CDNには、フラグメント認証のための異なるトークン化スキームが用意されていることがよくあります。 PrimetimeAd Insertionは、次のような主要なCDNネットワークをネイティブでサポートします。

* Akamai
* リメライト
* Centurylink / Level3
* サポートされるCDNの完全なリストについては、Primetimeのサポート担当者にお問い合わせください。

`pttoken`パラメーターについて詳しくは、[BootstrapAPIパラメーターの説明](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description)を参照してください。

## コンテンツCDNから配信する広告の設定{#configure-ad-deliver-from-cdn}

同じCDNから広告とコンテンツを配信して、コンテンツのアフィニティを維持したり、広告ブロッカーを避けたり、クライアントアプリケーションから必要な接続数を最適化したりする場合があります。 PrimetimeAd Insertionは、フラグメントをコンテンツCDNにマッピングするためのフラグメント再記述ルールをサポートしています。 詳しくは、[マニフェストの書き直し](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md)を参照してください。

## CDNによる開始アップパフォーマンスの向上{#increase-startup-performance}

詳しくは、[開始アップの最適化](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md)を参照してください。

## マルチCDN機能{#enable-multi-cdn-fetures}

マルチCDN機能を有効にする場合は、Primetimeのサポート担当者にお問い合わせください。
