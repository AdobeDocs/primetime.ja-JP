---
description: TVSDK は、メソッド、メタデータ、通知などのブラックアウトを実装する際に役立つ API エレメントを提供します。
title: ブラックアウト API 要素
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# ブラックアウト API 要素{#blackout-api-elements}

TVSDK は、メソッド、メタデータ、通知などのブラックアウトを実装する際に役立つ API エレメントを提供します。

プレーヤーにブラックアウトソリューションを実装する際には、次の機能を使用できます。

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。 次の場合 `replaceCurrentResource` がこのメソッドの後に呼び出されると、を呼び出すまで、 TVSDK はバックグラウンドアイテムのマニフェストのダウンロードを続行します。 `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  現在設定されているバックグラウンドリソースをクリアし、バックグラウンドマニフェストの取得と解析を停止します。

* **BlackoutMetadata** ブラックアウトに固有のメタデータタイプ。

  これにより、シーク不能な範囲 ( `TimeRange` 呼び出された属性 `nonseekableRange`) を TVSDK に追加します。 TVSDK は、これらの範囲をチェックします ( 目的のシーク位置が `nonseekableRange`) を探すたびに繰り返します。 設定済みで、ユーザーがシーク不可能な範囲にシークした場合、 TVSDK はビューアを `seekableRange`.

* **次へ** **DefaultMetadataKeys** ライブストリーム上のプリロールを有効または無効にするには、 `ENABLE_LIVE_PREROLL` を true または false に設定します。 false の場合、 TVSDK は、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しをおこなわないので、プリロールは再生されません。 ミッドロールには影響しません。 デフォルトは true です。

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` event subtype - TVSDK がバックグラウンドマニフェスト内でサブスクライブ済みのタグを検出するとディスパッチされます。

* **通知**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロード中にエラーが発生しました。

   * `SeekEvent.SEEK_POSITION_ADJUSTED` シーク不能な範囲でシークが試行されると、ディスパッチされます。
