---
title: ビデオの開始アップ時間の最適化
description: ビデオの開始アップ時間の最適化
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# ビデオの開始アップ時間の最適化の概要{#optimize-video-start-up-times}

PrimetimeAd Insertionには、キャッシュやルート/プロトコルの最適化のルールなど、ビデオ開始のアップタイムを最適化する機能がいくつか用意されています。 PrimetimeAd Insertionを使用する場合に、ビデオの開始を高速化するためのその他の推奨事項を次に示します。

* コンテンツ配信ネットワーク(CDN)からすべての広告とコンテンツを提供

* PrimetimeAd InsertionとCDN間のTLSハンドシェイクを減らすか、削除します。 詳しくは、[ルートとプロトコルの最適化](optimize-routes-protocols.md)を参照してください。

* 同じCDNから広告とコンテンツフラグメントを提供する

* ライブ/VODコンテンツおよびマニフェスト用のキャッシュ制御ヘッダーの挿入

* 応答が遅い広告プロバイダーまたは広告クリエイティブを減らすか、削除します。
