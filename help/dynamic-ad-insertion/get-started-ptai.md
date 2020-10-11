---
title: Adobe PrimetimeAd Insertionの概要
description: Adobe PrimetimeAd Insertionの概要
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Adobe PrimetimeAd Insertionの概要 {#ptai-get-started}

PrimetimeAd Insertionは、コンテンツと広告を提供し、パーソナライズされたインストリーム広告エクスペリエンスを作成し、広告主の広告再生を追跡するシステムを調整します。

PrimetimeAd Insertionは、ビデオマニフェストを書き直して、各ビューアに対してターゲット広告とパーソナライズされたエクスペリエンスを提供することで、ビデオ配信のクライアントアプリケーションと対話します。 PrimetimeAd Insertionは、クライアント側とサーバー側の両方の広告トラッキングをサポートしています。

システムが正しく設定されると、一般的なワークフローは次のようになります。

1. クライアントアプリケーションは、ビデオストリームに関する情報を含む [BootstrapURL](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) 、PrimetimeAd InsertionにGETリクエストを送信します。

1. PrimetimeAd Insertionは、パブリッシャーのCDNからクライアントアプリケーションにコンテンツマニフェストを送り返すことで応答します。

1. クライアントアプリケーションは、生成されたマニフェスト内の適切なストリームを選択して再生し、PrimetimeAd Insertionにリクエストします。

1. PrimetimeAd Insertionは、コンテンツCDNから要求されたストリームを取得し、キュー情報を解析/読み取り、広告サーバーの呼び出しを行い、必要に応じて広告の時間を置き換えます。

1. PrimetimeAd Insertionは、リソースURLを書き換え、広告クリエイティブがトランスコードを必要とするかどうかを検出することでマニフェストを正規化します。 [ジャストインタイム広告トランスコード](just-in-time-transcoding.md) および [パッケージ化を参照してください](just-in-time-repackaging.md)。

1. PrimetimeAd Insertionは、必要な広告クリエイティブを取得し、マニフェストに適切なフラグメントを挿入します。

1. PrimetimeAd Insertionは、広告を含む最終的なステッチマニフェストをクライアントアプリケーションに配信して再生します。

1. 広告の配信と視聴性は、クライアントまたはサーバー側の広告トラッキングを通じて測定できます。詳しくは、広告トラッキングの [設定を参照してください](set-up-ad-tracking.md)。

PrimetimeAd Insertionは、HLS/DASHのほとんどのクライアント設定をサポートしています。
