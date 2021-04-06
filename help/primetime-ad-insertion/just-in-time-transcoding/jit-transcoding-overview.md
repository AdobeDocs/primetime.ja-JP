---
title: ジャストインタイムトランスコード
description: ジャストインタイムトランスコード
copied-description: true
exl-id: 9577e1d5-1462-49d6-9d24-94e74dc9c019
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# ジャストインタイムトランスコード{#just-in-time-transcoding}

PrimetimeAd Insertionでは、ジャストインタイムのトランスコードとパッケージ化が機能し、互換性のない広告クリエイティブをコンテンツストリームで適切に再生できるようにします。 また、クライアント側の広告トラッキングで使用できる広告フラグメントにID3パケットを挿入することもできます。
一般的なワークフローは次のとおりです。

1. Adobe PrimetimeAd Insertionは、顧客の広告サーバーから広告/クリエイティブを取得します。

1. 広告のクリエイティブ形式がコンテンツストリームとネイティブに互換性がある場合、クリエイティブはマニフェストに挿入されます。

1. 広告のクリエイティブな形式にネイティブ互換性がない場合（.mp4、.mov、.webmなど）、PrimetimeAd Insertionは、指定したCDNからトランスコード済みの広告を検索します。 広告が見つかれば、その広告が挿入されます。それ以外の場合は、広告はトランスコード用のキューに入れられます。

1. 広告クリエイティブがトランスコードされた後、PrimetimeAd Insertionは、その広告アセットに対する以降のすべての要求をマニフェストにステッチします。

PrimetimeAd Insertionは、ほとんどのビデオおよびリニア形式でのトランスコードをサポートしています。 広告クリエイティブのトランスコードは通常3分以内に発生します。 詳しくは、Primetimeのサポート担当者にお問い合わせください。
