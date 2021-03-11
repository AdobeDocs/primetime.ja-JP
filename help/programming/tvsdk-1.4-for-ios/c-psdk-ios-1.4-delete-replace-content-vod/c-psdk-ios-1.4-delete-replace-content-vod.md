---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。
title: VODストリーム内の広告の削除と置換
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# 広告削除および置換APIの変更{#ad-deletion-and-replacement-api-changes}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張するものです。 カスタム広告マーカーは、メインコンテンツの一部を広告関連コンテンツ期間としてマークします。 これらの時間範囲をマークするだけでなく、時間範囲を削除したり置き換えたりすることもできます。

TVSDKで次の変更は、広告の削除と置換をサポートしています。

**新しいAPI**

* `PTTimeRangeCollection` は、定義済みの範囲と型を定義するパブリッククラスです。

   * `property PTTimeRangeCollectionType type` 時間範囲のタイプを示します。
   * `property NSArray* ranges` は、時間範囲の設定に使用されます。

      配列内のオブジェクトのタイプは`PTReplacementTimeRange`または`CMTimeRange`です。

      >[!TIP]
      >
      >配列のすべてのオブジェクトは同じ型である必要があります。

   * `PTTimeRangeCollectionType` は、次の `PTTimeRangeCollection`

      * `PTTimeRangeCollectionTypeMarkRanges`:範囲のタイプは *マーク*。この範囲は、コンテンツ内の範囲を広告としてマークするために使用されます。

      * `PTTimeRangeCollectionTypeDeleteRanges`:範囲のタイプは「削除」です。定義された範囲は、広告挿入の前にメインコンテンツから削除されます。
      * `PTTimeRangeCollectionTypeReplaceRanges`:範囲のタイプは「置換」です。定義された範囲は、メインから広告に置き換えられます（広告シグナリングモードは`PTAdSignalingModeCustomTimeRanges`に設定されます）。

* `PTReplacementTimeRange`  — 次の単一の範囲を定義する新しいパブリッククラス `PTTimeRangeCollection`:

   * `property CMTimeRange range`  — 範囲の開始と期間を定義します。
   * `property long replacementDuration`  — のタイプ `TimeRangeCollection` が「次の値」の場合 `PTTimeRangeCollectionTypeReplaceRanges`、が使用 `replacementDuration` され、期間が「」の配置オポチュニティ（広告挿入）が作成され `replacementDuration`ます。`replacementDuration`が設定されていない場合、広告サーバーは、その配置オポチュニティの広告の長さと数を決定します。

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges`  — の新しいタイプを追加し `PTAdSignalingMode`ました。このモードは、置換範囲に基づいて広告挿入用にタイプ`PTTimeRangeCollectionReplace`の`PTTimeRangeCollection`と組み合わせて使用されます。

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection`  — 範囲のマーク/削除/置換に使用する時間範囲を再生コンテンツで設定する場合。

* 警告ログ：

   * `UNDEFINED_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 広告シグナリングモードは、カスタム範囲として定義されますが、カスタム範囲は定義されません。
   * `INVALID_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 1つ以上の時間範囲が無効で、無視または変更されます。


**非推奨のAPI**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges`  — このプロパティは、以前は、マーキング用のC3範囲を定義するために使用されていました。`PTTimeRangeCollection`を介してこれらの範囲が設定されるので、現在は非推奨です。