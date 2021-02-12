---
title: Adobe PrimetimeAd Insertionの概要
description: Adobe PrimetimeAd Insertionの概要
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Adobe PrimetimeAd Insertionを使い始める{#ptai-get-started}

PrimetimeAd Insertionは、コンテンツと広告を提供し、パーソナライズされたインストリーム広告エクスペリエンスを作成し、広告主の広告再生を追跡するシステムを調整します。

PrimetimeAd Insertionは、ビデオマニフェストを書き直すことでビデオ配信のクライアントアプリケーションと対話し、各ビューアに対してターゲット広告とパーソナライズされたエクスペリエンスを提供します。 これらのマニフェストは、広告サーバーから配信されるコンテンツと広告を組み合わせ、必要に応じて、詳細な広告追跡手順を含むメタデータを含めることができます。 PrimetimeAd Insertionは、クライアント側とサーバー側の両方の広告トラッキングをサポートしています。

システムが正しく設定されると、一般的なワークフローは次のようになります。

1. クライアントアプリケーションは、ビデオストリームに関する情報と共に[BootstrapURL](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md)を生成し、GETリクエストをPrimetimeAd Insertionに送信します。  PrimetimeAd Insertionは、様々な広告シグナリング形式でHLSとDASHをサポートしています。

1. PrimetimeAd Insertionは、パブリッシャーのCDNからクライアントアプリケーションにコンテンツマニフェストを送り返すことで応答します。

1. クライアントアプリケーションは、生成されたマニフェスト内の適切なストリームを選択して再生し、PrimetimeAd Insertionにリクエストします。

1. PrimetimeAd Insertionは、コンテンツCDNから要求されたストリームを取得し、キュー情報を解析/読み取り、広告サーバーの呼び出しを行い、必要に応じて広告の時間を置き換えます。

1. PrimetimeAd Insertionは、リソースURLを書き換え、広告クリエイティブがトランスコードを必要とするかどうかを検出することでマニフェストを正規化します。詳しくは、[ジャストインタイム広告トランスコード](/help/primetime-ad-insertion/just-in-time-transcoding/jit-transcoding-overview.md)を参照してください。

1. PrimetimeAd Insertionは、必要な広告クリエイティブを取得し、マニフェストに適切なフラグメントを挿入します。

1. PrimetimeAd Insertionは、広告を含む最終的なステッチマニフェストをクライアントアプリケーションに配信して再生します。

1. 広告の配信と視聴率は、クライアントまたはサーバー側の広告トラッキングを通じて測定できます。[広告トラッキングの設定](/help/primetime-ad-insertion/getting-started/set-up-ad-tracking.md)を参照してください。

PrimetimeAd Insertionは、ほとんどのHLS/DASHクライアント設定とプレーヤー設定をサポートしています。 サポートされる特定の広告シグナリング形式について詳しくは、[サポートされるキュー形式](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md)を参照してください。
