---
description: ジャストインタイムトランスコードは、ID3時間指定メタデータを広告クリエイティブに挿入して、クライアント側の広告追跡を容易にできます。
seo-description: ジャストインタイムトランスコードでは、ID3時間指定メタデータをHLS形式の広告クリエイティブに挿入して、クライアント側の広告追跡を容易にできます。
seo-title: ジャストインタイムトランスコードを使用したID3時間指定メタデータタグの挿入
title: ジャストインタイムトランスコードを使用したID3時間指定メタデータタグの挿入
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# ジャストインタイムトランスコードを使用したID3時間指定メタデータタグの挿入{#using-crs-to-inject-id-timed-metadata-tags}

CRSは、ID3時間指定メタデータを広告クリエイティブに挿入して、クライアント側の広告追跡を容易にできます。

クライアントプレイヤーは、フレーム精度の高い広告追跡を可能にするために、ID3メタデータを読み取ります。

>[!NOTE]
>
>ID3時間指定メタデータ挿入機能は、Safari/iOSでのみ有効です。

## ID3挿入用CRSのワークフロー{#workflow-for-crs-for-id3-injection}

PrimetimeAd Insertionが`ptplayer=ios-mobileweb`パラメーターを受け取ると、適切な広告ストレージCDNにアップロードする前に、トランスコードされた広告クリエイティブにID3パケットが挿入されます。
