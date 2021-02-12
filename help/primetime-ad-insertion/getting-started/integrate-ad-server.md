---
title: 広告サーバーの統合
description: 広告サーバーの統合
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# 広告サーバーを統合{#integrate-ad-server}

開始を行うには、PrimetimeAd Insertionコンソールにアクセスするためのログインが与えられます。PrimetimeAd Insertionが、広告リクエストを任意の広告サーバーに転送する際に使用するルールを設定します。 PrimetimeAd Insertionは、VASTまたはVMAPに準拠した広告サーバーのほとんどをサポートしています。

>[!NOTE]
>
>[IAB VASTページ](https://www.iab.com/guidelines/digital-video-ad-serving-template-vast)

## マクロのサポート{#macro-support}

PrimetimeAd Insertionは、すべてのストリームに対して次の広告サーバーマクロを有効にします。

* キャッシュバスティング
* アプリケーションコンテキストまたはページURL
* 利用期間
* 現在のビデオアセット

その他のマクロが必要な場合は、Adobe Primetimeサポート担当者にお問い合わせください。

## 高度な機能{#advanced-features}

PrimetimeAd Insertionには、高度な機能を有効にするルールベースの判定機能もあります。 これは、在庫権限に基づいて異なる広告サーバーに広告をルーティングする場合や、個々の広告の周波数制限を有効にする場合に重要です。 詳しくは、[高度な機能](/help/primetime-ad-insertion/advanced-features/route-ads-based-on-rules.md)を参照してください。
