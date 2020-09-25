---
title: BootstrapAPI
description: null
translation-type: tm+mt
source-git-commit: aa43834fea161c537c448b7616c9bd8f779d1a74
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# BootstrapAPI {#bootstrap-api}

必須パラメータブートストラップの生成

## パラメータの説明 {#parameter-description}

| parameter | description | 形式 |
|---|---|---|
| pabimode | ライブストリームに対して [部分的な広告ブレーク挿入](ad-insertion-live-linear-stream.md#partial-ad-break-support) を有効にします。 有効な値：trueを指定すると無効になります（デフォルトは無効） | HLS/DASH |
| ptadwindow | ルックバック広告判定時間の長さ（秒）。DVRユーザーがストリームに参加したときに、PrimetimeAd Insertionが広告キューを探す時間（秒）です。 値をゼロにすると、最初のマニフェスト内のミッドロール広告判定が無効になり、最初の更新後にのみ判定が再開されます。 このパラメーターは、数秒間しか続かないセッション(チャネルのフリップなど)への広告挿入を無効にする場合に便利です。 使用可能な値：数値文字列0 ～ 1800（デフォルトは1800） | HLSのみ |
| ptassetid | 投稿者によって割り当てられ、管理されるコンテンツの一意のIDです。  Akamai Ad Scalerと組み合わせて使用する場合は必須です。 | HLS/DASH |
| ptcdn | トランスコードされたアセットをホストするための1つ以上のCDNのリスト。 詳しくは、「 [マルチCDNのサポート](multi-cdn-support.md)」を参照してください。 可能な値：akamai、level3、lnw(limelight networks)、comcastデフォルトでは、PrimetimeAd InsertionCDNが使用されます。 | HLS/DASH |
| ptcueformat | ad decisioningを実行するために指定した形式（scte35など）。 可能な値：dpisimple、dpiscte35、elementalカスタムキュー形式の場合は、ユースケースに使用する値について、テクニカルアカウント担当者にお問い合わせください。 | HLS/DASH |
| ptfailover | マスタープレイリストで指定されているプライマリストリームとフェイルオーバーストリームを識別し、それらを別々のセットとして扱うようマニフェストサーバーに通知します。 これにより、フェイルオーバーが容易になり、タイミングエラーが発生するのを防ぎます。 （Apple HLSデバイスのみ） 詳しくは、HLSプレーヤーの [切り替えの容易化を参照してください](hls-switching-to-failover.md) | HLSのみ |
| ptmulticall | 有効にした場合、VODアセット内の各アバイルに対して個別の広告リクエストが行われます。  デフォルトでは、PrimetimeAd Insertionは、すべての利用可能な情報を収集し、それを1回のリクエストで広告サーバーに送信しようとします。 有効な値：trueを指定すると無効になります（デフォルトは無効） | HLS/DASH |
| pttagds | HLSヘッダにEXT-X-DISCONTINUITY-SEQUENCEタグを挿入できます。可能な値：trueは無効にする（デフォルト無効）を有効にします。 | HLSのみ |
| pttimeline | 広告を配置したいタイムラインとコンテンツを含む文字列。コンテンツストリーム内の広告の時間を上書きします。 [ VODタイムラインの形式を参照してください。 ] | HLS/DASH |
| pttoken | CDN用のコンテンツフラグメント/セグメント認証トークン保護スキームを有効にします。可能な値は次のとおりです。akamai、lnw(limelight)、ctl(centurylink)（デフォルトのトークン化は無効） | HLS/DASH |
| pttrackingmode | 広告トラッキングスキームの有効化：可能な値：クライアント側広告トラッキングの単純な値：サーバー側広告トラッキングの単純な値（ハイブリッドクライアント/サーバー広告トラッキングの場合、デフォルトでは広告トラッキングは実行されません） | HLS/DASH |
| pttrackingversion |  |  |
| ptadtimeout （20.9.2と同じ） |  |  |
| ptparallelstream （20.9.3の場合） |  |  |
