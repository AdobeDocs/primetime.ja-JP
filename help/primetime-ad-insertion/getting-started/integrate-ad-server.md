---
title: 広告サーバーの統合
description: 広告サーバーの統合
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# 広告サーバーの統合 {#integrate-ad-server}

まず、PrimetimeAd Insertionコンソールにアクセスするためのログインが与えられます。このコンソールでは、PrimetimeAd Insertionが広告リクエストを目的の広告サーバーに転送する際に使用するルールを設定します。 PrimetimeAd Insertionは、ほとんどの VAST または VMAP 準拠の広告サーバーをサポートします。

>[!NOTE]
>
>[IAB VAST ページ](https://www.iab.com/guidelines/digital-video-ad-serving-template-vast)

## マクロのサポート {#macro-support}

PrimetimeAd Insertionは、すべてのストリームで次の広告サーバーマクロを有効にします。

* キャッシュバスティング
* アプリケーションコンテキストまたはページ URL
* 利用期間
* 現在のビデオアセット

追加のマクロが必要な場合は、Adobe Primetimeサポート担当者にお問い合わせください。

## 高度な機能 {#advanced-features}

PrimetimeAd Insertionには、高度な機能を有効にするルールベースの決定機能も備わっています。 これは、在庫権限に基づいて異なる広告サーバーに広告をルーティングする場合、または個々の広告に対して頻度キャップを有効にする場合に重要です。 詳しくは、 [高度な機能](/help/primetime-ad-insertion/advanced-features/route-ads-based-on-rules.md).
