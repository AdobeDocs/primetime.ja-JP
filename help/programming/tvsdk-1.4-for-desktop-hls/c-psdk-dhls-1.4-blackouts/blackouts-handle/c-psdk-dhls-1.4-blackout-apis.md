---
description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。
seo-description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。
seo-title: ブラックアウトAPI要素
title: ブラックアウトAPI要素
uuid: 65e1668c-6a19-4910-83a2-46d364e94e5f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# ブラックアウトAPI要素{#blackout-api-elements}

TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。

プレイヤーにブラックアウトソリューションを実装する場合は、以下を使用できます。

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。 このメ `replaceCurrentResource` ソッドの後にを呼び出すと、TVSDKは、を呼び出すまでバックグラウンドアイテムのマニフェストのダウンロードを続行しま `unregisterCurrentBackgroundItem`す。

   * `unregisterCurrentBackgroundItem`  現在設定されているバックグラウンドリソースをクリアし、バックグラウンドマニフェストのフェッチと解析を停止します。

* **BlackoutMetadata** ：ブラックアウトに固有のMetadataタイプ。

   これにより、TVSDKでシーク不可能範囲(と呼ばれる追加の `TimeRange` 属性)を設 `nonseekableRange`定できます。 TVSDKは、ユーザーがシークするたびに、これらの範囲(目的のシーク位置がa内にある `nonseekableRange`かどうか)をチェックします。 設定され、ユーザーがシーク不可能な範囲をシークした場合、TVSDKはビューアを強制的に `seekableRange`

* **START HERE NEXT** DefaultMetadataKeys **** trueまたはfalseに設定して、ライブストリームのプリロールを有効または無効にし `ENABLE_LIVE_PREROLL` ます。 falseの場合、TVSDKは、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しを行わないので、プリロールは再生されません。 これはミッドロールには影響しません。 デフォルトはtrueです。

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` event subtype - TVSDKがバックグラウンドマニフェストでサブスクライブ済みのタグを検出した場合にディスパッチされます。

* **通知**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロード中にエラーが発生しました。
   * `SeekEvent.SEEK_POSITION_ADJUSTED` シーク不可能な範囲でシークが試行されたときにディスパッチされます。


