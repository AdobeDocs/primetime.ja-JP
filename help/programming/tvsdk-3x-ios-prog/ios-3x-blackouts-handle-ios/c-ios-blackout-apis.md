---
description: TVSDK は、メソッド、メタデータ、通知などのブラックアウトを実装する際に役立つ API エレメントを提供します。
title: ブラックアウト API 要素
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ブラックアウト API 要素 {#blackout-api-elements}

TVSDK は、メソッド、メタデータ、通知などのブラックアウトを実装する際に役立つ API エレメントを提供します。

プレーヤーにブラックアウトソリューションを実装する際には、次の機能を使用できます。

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` 現在読み込まれているリソースをバックグラウンドリソースとして保存します。 次の場合 `replaceCurrentItemWithPlayerItem` がこのメソッドの後に呼び出されると、を呼び出すまで、 TVSDK はバックグラウンドアイテムのマニフェストのダウンロードを続行します。 `unregisterCurrentBackgroundItem` , `stop`または `reset` .

   * `unregisterCurrentBackgroundItem` バックグラウンドアイテムを nil に設定し、バックグラウンドマニフェストの取得と解析を停止します。

* **PTMetadata.PTBlackoutMetadata** A `PTMetadata` ブラックアウトに固有のクラス。

  これにより、シーク不能な範囲 ( `CMTimeRanges`) を TVSDK に追加します。 TVSDK は、ユーザーがシークするたびに、これらの範囲を確認します。 設定済みで、ユーザーがシーク不可能範囲にシークした場合、 TVSDK は視聴者をシーク不可能範囲の終わりまで強制的に移動させます。

* **次へ** **PTAdMetadata** ライブストリーム上のプリロールを有効または無効にするには、 `enableLivePreroll` を「はい」または「いいえ」に設定します。 NO の場合、 TVSDK は、コンテンツ再生前にプリロール広告に対する明示的な広告サーバー呼び出しをおこなわないので、プリロールは再生されません。 ミッドロールには影響しません。 デフォルトは YES です。

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - TVSDK がバックグラウンドマニフェスト内にサブスクライブ済みのタグを検出し、新しい `PTTimedMetadata` インスタンスがそのインスタンスから準備されます。 通知のオブジェクトは、 `PTMediaPlayerItem` 現在再生中のインスタンス。 次を取得： `PTTimedMetadata` 通知の `userInfo` 辞書 `PTTimedMetadataKey` キー。

   * `PTBackgroundManifestErrorNotification`  — メディアプレーヤーがバックグラウンドマニフェストの読み込みに完全に失敗した、つまり、すべてのストリーム URL がエラーまたは無効な応答を返した場合に投稿されます。 通知のオブジェクトは、 `PTMediaPlayerItem` 現在再生中のインスタンス。

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * コード：204000
      * タイプ：警告
      * バックグラウンドマニフェストのダウンロード中にエラーが発生しました。

   * `INVALID_SEEK_WARNING` シーク不可能な範囲 ( `nonSeekableRanges` 設定する `PTBlackoutMetadata`) をクリックします。
