---
title: CDN の統合
description: CDN の統合
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# CDN の統合 {#integrating-cdn}

PrimetimeAd Insertionは、ビデオチャンク自体ではなく、クライアントアプリケーションとマニフェストの間のプロキシとして機能します。 コンテンツを任意の CDN にデプロイし、BootstrapAPI を使用して URL を PrimetimeAd Insertionに渡します。 統合の詳細については、 [サポートされる CDN](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## サポートされる CDN トークン化スキーム {#cdn-tokenization-schemes}

CDN には、多くの場合、フラグメント認証用に異なるトークン化スキームがあります。 PrimetimeAd Insertionは、次のような主要な CDN ネットワークをネイティブにサポートします。

* Akamai
* Limelight
* Centurylink / Level3
* サポートされる CDN の完全なリストについては、Primetime サポート担当者にお問い合わせください

詳しくは、 `pttoken` パラメーター： [BootstrapAPI パラメーターの説明](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## コンテンツ CDN から配信する広告の設定 {#configure-ad-deliver-from-cdn}

コンテンツの親和性を維持し、広告ブロッカーを回避し、クライアントアプリケーションからの必要な接続数を最適化するために、同じ CDN から広告とコンテンツを配信したい場合があります。 PrimetimeAd Insertionは、フラグメントをコンテンツ CDN にマッピングするためのフラグメント書き換えルールをサポートしています。 詳しくは、 [マニフェストの書き直し](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## CDN を使用した起動パフォーマンスの向上 {#increase-startup-performance}

詳しくは、 [最適化の開始](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## マルチ CDN 機能 {#enable-multi-cdn-fetures}

マルチ CDN 機能を有効にする場合は、Primetime サポート担当者にお問い合わせください。
