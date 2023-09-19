---
description: ジャストインタイムトランスコーディングでは、ID3 時間指定メタデータを広告クリエイティブに挿入して、クライアント側の広告トラッキングを容易にすることができます。
title: ジャストインタイムトランスコーディングを使用した ID3 時間指定メタデータタグの挿入
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# ジャストインタイムトランスコーディングを使用した ID3 時間指定メタデータタグの挿入 {#using-crs-to-inject-id-timed-metadata-tags}

CRS は、ID3 時間指定メタデータを広告クリエイティブに挿入して、クライアント側の広告トラッキングを容易にできます。

クライアントプレーヤーは、フレーム精度の広告トラッキングを有効にするために、ID3 メタデータを読み取ります。

>[!NOTE]
>
>ID3 時間指定メタデータ挿入は、Safari/iOSに対してのみ機能します。

## ID3 インジェクション用 CRS のワークフロー {#workflow-for-crs-for-id3-injection}

PrimetimeAd Insertionが `ptplayer=ios-mobileweb` パラメーターを渡すと、トランスコードされた広告クリエイティブに ID3 パケットが挿入されてから、適切な広告ストレージ CDN にアップロードされます。
