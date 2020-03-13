---
description: すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告追跡の有効化に依存する機能を提供する必要があります。
seo-description: すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告追跡の有効化に依存する機能を提供する必要があります。
seo-title: ビデオプレーヤーの要件
title: ビデオプレーヤーの要件
uuid: 29593d67-2901-4d9e-a08f-23c8a7667283
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# ビデオプレーヤーの要件 {#video-player-requirements}

すべてのビデオプレーヤーは、マニフェストサーバーが広告の挿入と広告追跡の有効化に依存する機能を提供する必要があります。

Primetime ad insertion APIを使用するには、ビデオプレーヤーが次の条件を満たす必要があります。

* コンテンツの再生中に再生ヘッドの位置を追跡できます。
* 指定された時刻の追跡URLをリクエストできます。
* HLS v3以降をサポートするデバイスプラットフォーム上で実行します。次の機能が含まれます。

   * PTSでの不連続性(タグでマーク `EXT-X-DISCONTINUITY` )
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* HTTPリダイレクトとJSONの解析をサポートするプラットフォームで実行します。
* CORSをサポートするプラットフォームで実行します。