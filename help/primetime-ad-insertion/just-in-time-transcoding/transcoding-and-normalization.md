---
title: トランスコードと正規化
description: トランスコードと正規化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# トランスコードと正規化 {#transcoding-and-normalization}

PrimetimeAd Insertionは、次の条件を一致させることで、コンテンツと広告全体で一貫した表示エクスペリエンスを実現しようとします。

1. ソースストリームコーデックとビットレート。トランスコード時には常に最高品質/ビットレートのクリエイティブを選択します。

1. ソースストリームフラグメントのサイズ (HLS/#EXT-X-TARGETDURATION)

1. トランスコード用の推奨されるクリエイティブ形式

1. オーディオのオートレベリングにより、すべての広告クリエイティブで一貫した dB レベルを確保。

>[!NOTE]
>
>PrimetimeAd Insertionのジャストインタイムトランスコーディングで生成された HLS アセットは、コンテンツで定義されている HLS バージョンに関係なく、バージョン 3 の HLS アセットを生成します。
