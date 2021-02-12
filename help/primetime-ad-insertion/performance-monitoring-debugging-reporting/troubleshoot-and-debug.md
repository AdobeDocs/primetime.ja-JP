---
title: トラブルシューティングとデバッグ
description: null
translation-type: tm+mt
source-git-commit: 242b5a2875ebc0e0020296ce9489dd54438b5ad0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# トラブルシューティングとデバッグ{#troubleshooting-debugging}

PrimetimeAd Insertionオファーツールを使用して、ビデオ配信のすべてのフェーズで発生する可能性のある問題(CDN配信エラー、クリエイティブエラー、クライアント接続エラーなど)を識別し、診断します。

PrimetimeAd Insertionは、ブートストラップURLへの[BootstrapAPIパラメーター](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true`または`ptdebug=AdCall`を介した詳細ログをサポートします。 ログは、HTTP応答ヘッダーとPrimetimeAd Insertionコンソールの両方に出力されます。 このパラメーターは、ローカライズされたテストのみを目的としており、実稼動ストリームには使用しません。 詳細ログが有効な場合のメッセージの種類について詳しくは、詳細ログの[ptdebugログイベント](verbose-logging.md#ptdebug-logging-events)を参照してください。

また、PrimetimeAd Insertionは、X-ADBE-AI-X1ヘッダーを持つすべてのリクエストに対してパフォーマンスデバッグを提供します。このヘッダーは、任意のリクエストに対するパフォーマンスと広告挿入を測定するのに使用できます。 この要求ヘッダーは、詳細ログが有効になっているかどうかに関係なく使用できます。 詳しくは、[詳細ヘッダーを参照してください。X-ADBE-PTAI-X1](debugging-headers.md)。
