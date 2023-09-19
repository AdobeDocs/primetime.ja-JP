---
title: 広告トラッキングの設定
description: 広告トラッキングの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 広告トラッキングの設定 {#ser-up-ad-tracking}

ほとんどの広告主は、広告がいつ、どのくらいの時間、どの程度正常に表示されたかに関する情報を必要とします。 PrimetimeAd Insertionは、クライアント側、サーバー側、ハイブリッドの広告トラッキングをサポートし、この情報を柔軟に収集できます。

## VMAP/JSON を使用したクライアント側広告トラッキング {#client-side-ad-tracking-vmap-json}

クライアント側の広告トラッキングでは、サーバーは、広告ステッチされたプレイリストと共に、トラッキングイベントと URL を指定する JSON、VMAP、またはマニフェスト内構造をクライアントに送信します。

クライアント側の広告トラッキングを有効にするには、 [BootstrapAPI](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>の設定 `pttrackingmode=simple` によって、最初のブートストラップ API リクエストが HLS や DASH ドキュメントではなく JSON 応答を返します。

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## サーバーサイド広告トラッキング {#server-side-ad-tracking}

この方法を使用すると、広告トラッキングデータは完全にサーバー側で計算されます。 これは、クライアントアプリケーションを更新できない場合に役立ちます。 ただし、サーバーサイド広告トラッキングは、クライアントサイド再生アクティビティと一致しない場合があります。 例えば、エンドユーザーが広告全体を表示しない場合でも、サーバーはセグメントの配信後に広告が再生されると見なします。

サーバーサイド広告トラッキングを有効にするには、 [BootstrapAPI](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

詳しくは、 `pttrackingmode` のセクション [BootstrapAPI](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

すべての広告トラッキングビーコンは、次の HTTP リクエストヘッダーで送信されます。

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

これらの値には、クライアント/プレーヤーのユーザーエージェントとクライアントの IP アドレスが含まれます。

## ハイブリッド広告トラッキング {#hybrid-ad-tracking}

この方法はサーバー側の追跡に似ていますが、詳細な追跡情報を得るために、クライアントアプリケーションは PrimetimeAd Insertionのサイドカーをリクエストすることもあります。 ハイブリッド広告トラッキングは、オーバーレイや会社などの非線形広告をクライアントアプリケーションに配信できますが、PrimetimeAd Insertionに依存して個々の広告トラッキング URL を送信します。
ハイブリッド広告トラッキングを有効にするには、 `pttrackingmode` パラメーターを [BootstrapAPI](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).
