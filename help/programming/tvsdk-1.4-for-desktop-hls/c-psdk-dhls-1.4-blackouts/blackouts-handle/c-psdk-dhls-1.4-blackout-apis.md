---
description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装に役立つAPIエレメントを提供します。
title: ブラックアウトAPI要素
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# ブラックアウトAPI要素{#blackout-api-elements}

TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装に役立つAPIエレメントを提供します。

プレイヤーにブラックアウトソリューションを実装する場合は、以下を使用できます。

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。このメソッドの後に`replaceCurrentResource`が呼び出されると、`unregisterCurrentBackgroundItem`を呼び出すまで、TVSDKはバックグラウンドアイテムのマニフェストのダウンロードを続行します。

   * `unregisterCurrentBackgroundItem`  現在設定されているバックグラウンドリソースをクリアし、バックグラウンドマニフェストのフェッチおよび解析を停止します。

* **BlackoutMetadataブラ** ックアウトに固有のMetadata型です。

   これにより、TVSDKにシーク不可能範囲（`nonseekableRange`と呼ばれる追加の`TimeRange`属性）を設定できます。 TVSDKは、ユーザーがシークするたびに、（目的のシーク位置が`nonseekableRange`内にあるかどうか）これらの範囲をチェックします。 この変数が設定され、ユーザーがシーク不可能な範囲をシークした場合、TVSDKは視聴者を強制的に`seekableRange`の終了時間にします。

* **開始HERE NEXTDefaultMetadataKeysライブストリームのプリロールを有効または無効にするには、trueまたはfalse** ****  `ENABLE_LIVE_PREROLL` に設定します。falseの場合、TVSDKは、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しを行わないので、プリロールは再生されません。 これは、ミッドロールには影響しません。 デフォルトはtrueです。

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` イベントサブタイプ — TVSDKがバックグラウンドマニフェスト内でサブスクライブ済みのタグを検出した場合にディスパッチされます。

* **通知**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロードでエラーが発生しました。
   * `SeekEvent.SEEK_POSITION_ADJUSTED` シーク不可能な範囲でシークが試行された場合にディスパッチされます。


