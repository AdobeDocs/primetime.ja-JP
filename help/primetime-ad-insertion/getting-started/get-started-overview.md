---
title: Adobe PrimetimeAd Insertionの概要
description: Adobe PrimetimeAd Insertionの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Adobe PrimetimeAd Insertionの概要 {#ptai-get-started}

PrimetimeAd Insertionは、コンテンツと広告を提供し、パーソナライズされたインストリーム広告エクスペリエンスを作成し、広告主の広告再生を追跡するシステムを調整します。

PrimetimeAd Insertionは、ビデオマニフェストを書き直すことでビデオ配信クライアントアプリケーションとやり取りし、各ビューアに対してターゲットとなる広告とパーソナライズされたエクスペリエンスを提供します。 これらのマニフェストは、広告サーバーから配信されるコンテンツと広告を組み合わせ、オプションで詳細な広告追跡手順を含むメタデータを含めることができます。 PrimetimeAd Insertionは、クライアント側とサーバー側の両方の広告トラッキングをサポートしています。

システムが正しく設定されると、一般的なワークフローは次のようになります。

1. クライアントアプリケーションが [BootstrapURL](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) ビデオストリームに関する情報を含む。また、GETリクエストを PrimetimeAd Insertionに送信します。  PrimetimeAd Insertionは、様々な広告シグナリング形式で HLS と DASH をサポートしています。

1. PrimetimeAd Insertionは、パブリッシャーの CDN からクライアントアプリケーションにコンテンツマニフェストを送り返すことで応答します。

1. クライアントアプリケーションは、生成されたマニフェスト内の適切なストリームを選択して再生し、PrimetimeAd Insertionにリクエストを送信します。

1. PrimetimeAd Insertionは、コンテンツ CDN から要求されたストリームを取得し、キュー情報を解析/読み取り、広告サーバーを呼び出し、必要に応じて広告ブレークを置き換えます。

1. PrimetimeAd Insertionは、リソース URL を書き換え、広告クリエイティブでトランスコードが必要かどうかを検出することで、マニフェストを正規化します。詳しくは、 [ジャストインタイムの広告トランスコード](/help/primetime-ad-insertion/just-in-time-transcoding/jit-transcoding-overview.md).

1. PrimetimeAd Insertionは、必要な広告クリエイティブを取得し、適切なフラグメントをマニフェストに挿入します。

1. PrimetimeAd Insertionは、再生用に、広告を含む最終的なステッチされたマニフェストをクライアントアプリケーションに配信します。

1. 広告配信と視認性は、クライアントまたはサーバー側の広告トラッキングを通じて測定できます。詳しくは、 [広告トラッキングの設定](/help/primetime-ad-insertion/getting-started/set-up-ad-tracking.md).

PrimetimeAd Insertionは、ほとんどの HLS/DASH クライアントおよびプレーヤー設定をサポートしています。 サポートされる特定の広告シグナリング形式について詳しくは、 [サポートされるキューの形式](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md).
