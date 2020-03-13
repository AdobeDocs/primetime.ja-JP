---
description: CRSは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にします。
seo-description: CRSは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にします。
seo-title: CRSを使用したID3時間指定メタデータタグの挿入
title: CRSを使用したID3時間指定メタデータタグの挿入
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: c2216a5089d23ca1fcbb77c87b4a01a6fa1807ff

---


# CRSを使用したID3時間指定メタデータタグの挿入 {#using-crs-to-inject-id-timed-metadata-tags}

CRSは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にします。

クライアントプレイヤーは、フレーム精度の高い広告追跡を有効にするために、ID3メタデータを読み取ります。

>[!NOTE]
>
>ID3時間指定メタデータの挿入は、iOSのSafariでのみ機能します。

## ID3挿入のCRSのワークフロー {#workflow-for-crs-for-id3-injection}

ID3挿入のワークフローは、JIT再パッケージ化の詳細なワ [ークフローのワークフローと同じです。](../creative-repackaging-service/jit-repackage.md) マニフェストサーバーは、パラメー `ptplayer=ios-mobileweb` ターを受け取ると、CDNサーバーにアップロードする前に、ID3パケットをトランスコードされた広告クリエイティブに挿入するようCRSに指示します。

>[!NOTE]
>
>マルチCDN設定では、マニフェストサーバーはブートストラップURLのパラメー `ptcdn` ターを使用してCDNサーバーを識別し、広告クリエイティブをアップロードします。