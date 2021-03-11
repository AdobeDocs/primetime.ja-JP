---
description: CRSは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にできます。
title: CRSを使用したID3時間指定メタデータタグの挿入
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# CRSを使用したID3時間指定メタデータタグの挿入{#using-crs-to-inject-id-timed-metadata-tags}

CRSは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にできます。

クライアントプレイヤーは、フレーム精度の高い広告追跡を可能にするために、ID3メタデータを読み取ります。

>[!NOTE]
>
>ID3時間指定メタデータ挿入は、iOSのSafariでのみ機能します。

## ID3挿入用CRSのワークフロー{#workflow-for-crs-for-id3-injection}

ID3挿入のワークフローは、[JIT再パッケージ化の詳細ワークフローのワークフローと同じです。](../~old-creative-repackaging-service/jit-repackage.md) マニフェストサーバーは、 `ptplayer=ios-mobileweb` パラメーターを受け取ると、CDNサーバーにアップロードする前に、ID3パケットをトランスコードされた広告クリエイティブに挿入するようCRSに指示します。

>[!NOTE]
>
>マルチCDN設定では、マニフェストサーバーはブートストラップURLの`ptcdn`パラメーターを使用して、広告クリエイティブをアップロードするCDNサーバーを識別します。