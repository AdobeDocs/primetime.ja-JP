---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-title: 広告削除および置換APIの変更
title: 広告削除および置換APIの変更
uuid: 3689d31f-4feb-4ea5-ac49-ef2e71472f4b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# 広告削除および置換APIの変更 {#ad-deletion-and-replacement-api-changes}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除および置き換えることもできます。

<!--<a id="section_7A90BFE99F1A4D908D6DDB0B49FA1199"></a>-->

TVSDKに関する次の変更は、広告の削除と置換をサポートしています。

**新しいAPI**

* `PTTimeRangeCollection` は、事前定義された範囲と型のセットを定義するパブリッククラスです。

   * `property PTTimeRangeCollectionType type` 時間範囲のタイプを示します。
   * `property NSArray* ranges` は、時間範囲の設定に使用されます。

      配列内で期待されるオブジェクトのタイプは、または `PTReplacementTimeRange` です `CMTimeRange`。

      >[!TIP]
      >
      >配列のすべてのオブジェクトは同じ型である必要があります。

   * `PTTimeRangeCollectionType` は、次のURLで定義されている範囲の動作を定義する列挙で `PTTimeRangeCollection`す。

      * `PTTimeRangeCollectionTypeMarkRanges`:範囲のタイプは *Markです*。 この範囲は、コンテンツ内の範囲を広告としてマークするために使用されます。

      * `PTTimeRangeCollectionTypeDeleteRanges`:範囲のタイプは「削除」です。 定義された範囲は、広告挿入前にメインコンテンツから削除されます。
      * `PTTimeRangeCollectionTypeReplaceRanges`:範囲のタイプは「置換」です。 定義された範囲は、メインから広告に置き換えられます(広告シグナリングモードは、に設定さ `PTAdSignalingModeCustomTimeRanges`れます)。

* `PTReplacementTimeRange`  — 次の単一の範囲を定義する新しいパブリッククラス `PTTimeRangeCollection`:

   * `property CMTimeRange range`  — 範囲の開始と期間を定義します。
   * `property long replacementDuration`  — のタイプが「」の場合、 `TimeRangeCollection` は、 `PTTimeRangeCollectionTypeReplaceRanges`の期 `replacementDuration` 間を持つ配置オポチュニティ（広告挿入）の作成に使用されます `replacementDuration`。 が設定され `replacementDuration` ていない場合、広告サーバーは、その配置オポチュニティの広告の長さと数を判断します。

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges`  — の新しいタイプを追加しまし `PTAdSignalingMode`た。 このモードは、置換範囲に基づいて、広告 `PTTimeRangeCollection` 挿入のタ `PTTimeRangeCollectionReplace` イプを持つと組み合わせて使用されます。

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection`  — 再生コンテンツの範囲をマーク/削除/置換で使用する時間範囲を設定する場合。

* 警告ログ：

   * `UNDEFINED_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 広告シグナリングモードは、カスタム範囲として定義されますが、カスタム範囲は定義されません。
   * `INVALID_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 1つ以上の時間範囲が無効で、無視または変更されます。


**非推奨のAPI**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges`  — このプロパティは、以前はマーキング用のC3範囲を定義するために使用されていました。 これらの範囲はを介して設定されるので、現在は非推奨で `PTTimeRangeCollection`す。