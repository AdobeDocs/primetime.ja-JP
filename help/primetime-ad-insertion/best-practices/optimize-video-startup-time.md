---
title: ビデオの開始時間の最適化
description: ビデオの開始時間の最適化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# ビデオの開始時間の最適化の概要 {#optimize-video-start-up-times}

PrimetimeAd Insertionは、キャッシュやルート/プロトコルの最適化のルールなど、ビデオの起動時間を最適化するいくつかの機能を提供します。 PrimetimeAd Insertionを使用する際に、ビデオの起動時間を短縮するための推奨事項を次に示します。

* コンテンツ配信ネットワーク (CDN) からすべての広告とコンテンツを提供する

* Primetime と CDN との間での TLS のハンドシェイクを減らすか削除しますAd Insertion。 詳しくは、 [ルートとプロトコルの最適化](optimize-routes-protocols.md).

* 同じ CDN から広告フラグメントとコンテンツフラグメントを提供する

* ライブ/VOD コンテンツおよびマニフェスト用の cache-control ヘッダーを挿入します

* 応答が遅い広告プロバイダーや広告クリエイティブを減らす、または削除する
