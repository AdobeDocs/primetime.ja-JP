---
description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装に役立つAPIエレメントを提供します。
title: ブラックアウトAPI要素
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ブラックアウトAPI要素{#blackout-api-elements}

TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装に役立つAPIエレメントを提供します。

プレイヤーにブラックアウトソリューションを実装する場合は、以下を使用できます。

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。このメソッドの後に`replaceCurrentItemWithPlayerItem`を呼び出すと、`unregisterCurrentBackgroundItem`、`stop`、または`reset`を呼び出すまで、TVSDKはバックグラウンドアイテムのマニフェストのダウンロードを続行します。

   * `unregisterCurrentBackgroundItem` バックグラウンドアイテムをnilに設定し、バックグラウンドマニフェストのフェッチおよび解析を停止します。

* **PTMetadata.** PTBlackoutMetadataブラックアウトに固有の `PTMetadata` クラス。

   これにより、TVSDKにシーク不能範囲（`CMTimeRanges`の配列）を設定できます。 TVSDKは、ユーザーがシークするたびに、これらの範囲をチェックします。 この変数が設定され、ユーザーがシーク不可能範囲をシークした場合、TVSDKは視聴者をシーク不可能範囲の終わりまで強制的に移動させます。

* **開始HERE** **** NEXTPTAdMetadataYesをYESまたはNOに設定して、ライブストリーム上のプリロール `enableLivePreroll` を有効または無効にします。NOの場合、TVSDKは、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しを行わないので、プリロールは再生されません。 これは、ミッドロールには影響しません。 デフォルトはYESです。

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - TVSDKは、バックグラウンドマニフェスト内でサブスクライブ済みのタグを検出し、そこから新しい `PTTimedMetadata` インスタンスを作成するとポストされます。通知のオブジェクトは、現在再生中の`PTMediaPlayerItem`インスタンスです。 `PTTimedMetadataKey`キーを使用して、`PTTimedMetadata`インスタンスを通知の`userInfo`ディクショナリから取得できます。

   * `PTBackgroundManifestErrorNotification`  — メディアプレイヤーがバックグラウンドマニフェストの読み込みに完全に失敗した、つまり、すべてのストリームURLがエラーまたは無効な応答を返す場合にポストされます。通知のオブジェクトは、現在再生中の`PTMediaPlayerItem`インスタンスです。

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロードでエラーが発生しました。
   * `INVALID_SEEK_WARNING` シーク不可能な範囲(に `nonSeekableRanges` 設定されている)でシークが試行された場合にディスパッチされ `PTBlackoutMetadata`ます。