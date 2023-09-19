---
description: すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告の追跡の有効化に使用する機能を提供する必要があります。
title: ビデオプレーヤーの要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# ビデオプレーヤーの要件 {#video-player-requirements}

すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告の追跡の有効化に使用する機能を提供する必要があります。

Primetime ad insertion API を使用するには、ビデオプレーヤーが次の条件を満たす必要があります。

* コンテンツの再生時に再生ヘッドの位置を追跡できます。
* 指定された時間にトラッキング URL をリクエストできます。
* HLS v3 以降をサポートするデバイスプラットフォーム上で実行します。以下が含まれます。

   * 次のマークが付いた PTS 不連続 `EXT-X-DISCONTINUITY` タグ
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* HTTP リダイレクトをサポートし、JSON の解析をサポートするプラットフォームで実行します。
* Web ベースのプレーヤーは、CORS をサポートするプラットフォームで実行する必要があります。
