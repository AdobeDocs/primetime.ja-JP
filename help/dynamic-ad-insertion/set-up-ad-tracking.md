---
title: 広告トラッキングの設定
description: 広告トラッキングの設定
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# 広告トラッキングの設定 {#ser-up-ad-tracking}

ほとんどの広告主は、広告がいつ、どの程度の期間、どの程度正常に表示されたかに関する情報を必要とします。 PrimetimeAd Insertionは、クライアント側、サーバー側、ハイブリッド広告トラッキングをサポートしており、この情報を柔軟に収集できます。

## VMAP/JSONを使用したクライアント側の広告トラッキング {#client-side-ad-tracking-vmap-json}

クライアント側の広告トラッキングでは、サーバーは、広告関連付けプレイリストと共に、トラッキングイベントとURLを指定するJSON、VMAPまたはマニフェスト内構造をクライアントに送信します。

クライアント側の広告トラッキングを有効にするには、 [BootstrapAPIで次のパラメーターを指定します](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>を設定す `pttrackingmode=simple` ると、最初のブートストラップAPIリクエストがHLSやDASHドキュメントではなくJSON応答を返します。

形式について詳し `pttrackingmode`くは、次の `pttrackingversion`[APIリファレンスを参照してください。マニフェストサーバークエリパラメーター](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。

## サーバー側広告トラッキング {#server-side-ad-tracking}

この方法を使用すると、広告トラッキングデータはサーバー側でのみ計算されます。 これは、クライアントアプリケーションの更新を実行できない場合に役立ちます。 ただし、サーバー側の広告トラッキングは、クライアント側の再生アクティビティとは一致しない場合があります。 例えば、エンドユーザーが広告全体を表示していない場合でも、サーバーは、セグメントの配信後に広告が再生されると見なします。

サーバー側の広告トラッキングを有効にするには、 [BootstrapAPIで次のパラメーターを指定します](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。

`pttrackingmode=sstm`

詳しくは、 `pttrackingmode` BootstrapAPIの節を参照してください [](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。

すべての広告トラッキングビーコンは、以下のHTTPリクエストヘッダーと共に送信されます。

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

これらの値には、クライアント/プレーヤーのユーザーエージェントとクライアントのIPアドレスが含まれます。

## ハイブリッド広告トラッキング {#hybrid-ad-tracking}

このアプローチはサーバー側の追跡に似ていますが、クライアントアプリケーションは、詳細な追跡情報を取得するためにPrimetimeAd Insertionのサイドカーを要求することもあります。 ハイブリッド広告トラッキングは、オーバーレイや会社などの非線形広告をクライアントアプリケーションに配信する一方で、個々の広告トラッキングURLを送信する際にはPrimetimeAd Insertionに依存します。
ハイブリッド広告トラッキングを有効にするには、 `pttrackingmode` BootstrapAPIの [パラメーターを参照してください](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。
