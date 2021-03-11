---
description: すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告トラッキングの有効化に依存する機能を提供する必要があります。
title: ビデオプレーヤーの要件
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# ビデオプレーヤーの要件{#video-player-requirements}

すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告トラッキングの有効化に依存する機能を提供する必要があります。

Primetime ad insertion APIを使用するには、ビデオプレーヤーが次の条件を満たす必要があります。

* コンテンツの再生時に再生ヘッドの位置を追跡できます。
* 指定された時刻の追跡URLをリクエストできます。
* HLS v3以降をサポートする、以下を含むデバイスプラットフォーム上で実行

   * `EXT-X-DISCONTINUITY`タグで示されたPTSの不連続性
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* HTTPリダイレクトとJSONの解析をサポートするプラットフォームで実行します。
* CORSをサポートするプラットフォームで実行します。