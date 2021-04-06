---
title: トランスコードと正規化
description: トランスコードと正規化
copied-description: true
exl-id: 48d9d971-4b15-4f1b-8740-c21983a3e835
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# トランスコードと正規化{#transcoding-and-normalization}

PrimetimeAd Insertionは、次の条件を満たすことで、コンテンツと広告で一貫した表示エクスペリエンスを得ることを試みます。

1. ソースストリームコーデックとビットレート。トランスコード時には常に最高の品質/ビットレートクリエイティブを選択します。

1. ソースストリームフラグメントのサイズ(HLS/#EXT-X-TARGETDURATION)

1. トランスコードに適したクリエイティブ形式

1. オーディオのオートレベリングを使用して、すべての広告クリエイティブで一貫したdBレベルを確保。

>[!NOTE]
>
>PrimetimeAd Insertionのジャストインタイムトランスコードで生成されたHLSアセットは、コンテンツで定義されているHLSバージョンに関係なく、バージョン3のHLSアセットを生成します。
