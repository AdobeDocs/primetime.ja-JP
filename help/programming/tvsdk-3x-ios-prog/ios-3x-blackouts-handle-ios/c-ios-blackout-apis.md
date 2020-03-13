---
description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。
seo-description: TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。
seo-title: ブラックアウトAPI要素
title: ブラックアウトAPI要素
uuid: f87f4ed0-3f97-48bd-bceb-28357a978964
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ブラックアウトAPI要素 {#blackout-api-elements}

TVSDKは、メソッド、メタデータ、通知など、ブラックアウトの実装時に役立つAPI要素を提供します。

プレイヤーにブラックアウトソリューションを実装する場合は、以下を使用できます。

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。 このメ `replaceCurrentItemWithPlayerItem` ソッドの後にを呼び出すと、、、またはを呼び出すまで、TVSDKはバックグラウンドアイテムのマニフェストのダ `unregisterCurrentBackgroundItem` ウンロー `stop`ドを続行しま `reset` す。

   * `unregisterCurrentBackgroundItem` バックグラウンドアイテムをnilに設定し、バックグラウンドマニフェストのフェッチと解析を停止します。

* **PTMetadata.PTBlackoutMetadata** ブラック `PTMetadata` アウトに固有のクラス。

   これにより、TVSDKでシーク不可能範囲（の配列）を設定 `CMTimeRanges`できます。 TVSDKは、ユーザーがシークするたびにこれらの範囲をチェックします。 設定され、ユーザーがシーク不可能な範囲をシークした場合、TVSDKは、ビューアをシーク不可能な範囲の最後まで強制的に移動させます。

* **START HERE NEXT** PTAdMetadata **「はい」または「いいえ」に設定して、ライブストリームのプリロールを有効**`enableLivePreroll` または無効にします。 NOの場合、TVSDKは、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しを行わないので、プリロールは再生されません。 これはミッドロールには影響しません。 デフォルトはYESです。

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - TVSDKがバックグラウンドマニフェスト内でサブスクライブされたタグを検出し、そこから新しいインスタ `PTTimedMetadata` ンスを作成した場合にポストされます。 通知のオブジェクトは、現在再生中の `PTMediaPlayerItem` インスタンスです。 キーを使用して、通 `PTTimedMetadata` 知のディクショナリからインスタ `userInfo` ンスを取得で `PTTimedMetadataKey` きます。

   * `PTBackgroundManifestErrorNotification`  — メディアプレイヤーがバックグラウンドマニフェストの読み込みに完全に失敗した、つまり、すべてのストリームURLがエラーまたは無効な応答を返した場合にポストされます。 通知のオブジェクトは、現在再生中の `PTMediaPlayerItem` インスタンスです。

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロード中にエラーが発生しました。
   * `INVALID_SEEK_WARNING` シーク不可能な範囲（で設定）でシークが試行されたと `nonSeekableRanges` きにディスパッ `PTBlackoutMetadata`チされます。