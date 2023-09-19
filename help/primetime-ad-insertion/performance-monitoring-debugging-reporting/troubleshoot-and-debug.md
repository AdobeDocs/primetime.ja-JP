---
title: トラブルシューティングとデバッグ
description: トラブルシューティングとデバッグ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# トラブルシューティングとデバッグ {#troubleshooting-debugging}

PrimetimeAd Insertionは、CDN 配信エラー、クリエイティブエラー、クライアント接続エラーなど、ビデオ配信のすべてのフェーズで発生する可能性のある問題を識別および診断するためのツールを提供します。

PrimetimeAd Insertionは、 [BootstrapAPI パラメーター](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` または `ptdebug=AdCall` をブートストラップ URL に追加します。 ログは、HTTP 応答ヘッダーと Primetime 応答コンソールの両方にAd Insertionされます。 このパラメーターは、ローカライズされたテストのみを対象としています。本番ストリームでは対象としません。 詳細ログが有効な場合のメッセージタイプの詳細については、 [ptdebug ログイベントの詳細ログ](verbose-logging.md#ptdebug-logging-events).

また、PrimetimeAd Insertionは、X-ADBE-AI-X1 ヘッダーを持つすべてのリクエストでパフォーマンスデバッグを提供します。このヘッダーを使用して、特定のリクエストに対するパフォーマンスおよび広告挿入を測定できます。 このリクエストヘッダーは、詳細ログが有効になっているかどうかに関係なく使用できます。 詳しくは、 [詳細ヘッダー： X-ADBE-PTAI-X1](debugging-headers.md).
