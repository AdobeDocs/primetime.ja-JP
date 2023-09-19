---
description: TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。
title: VOD ストリーム内の広告の削除と置換
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 広告の削除と置き換え API の変更 {#ad-deletion-and-replacement-api-changes}

TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除して置き換えることもできます。

TVSDK に次の変更が加えられ、広告の削除と置換がサポートされました。

**新しい API**

* `PTTimeRangeCollection` は、事前に定義された範囲とタイプのセットを定義するパブリッククラスです。

   * `property PTTimeRangeCollectionType type` 時間範囲のタイプを示します。
   * `property NSArray* ranges` は、時間範囲の設定に使用されます。

     配列内で期待されるオブジェクトのタイプは次のとおりです `PTReplacementTimeRange` または `CMTimeRange`.

     >[!TIP]
     >
     >配列のすべてのオブジェクトは同じ型である必要があります。

   * `PTTimeRangeCollectionType` は、 `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`：範囲のタイプは *トンボ*. この範囲は、コンテンツ内の範囲を広告としてマークするために使用されます。

      * `PTTimeRangeCollectionTypeDeleteRanges`：範囲のタイプは削除です。 定義された範囲は、広告挿入の前にメインコンテンツから削除されます。
      * `PTTimeRangeCollectionTypeReplaceRanges`：範囲のタイプは「置換」です。 定義された範囲は、メインから広告に置き換えられます ( 広告シグナリングモードは、 `PTAdSignalingModeCustomTimeRanges`) をクリックします。

* `PTReplacementTimeRange`  — 単一の範囲を定義する新しいパブリッククラス `PTTimeRangeCollection`:

   * `property CMTimeRange range`  — 範囲の開始と期間を定義します。
   * `property long replacementDuration` - `TimeRangeCollection` 次に該当 `PTTimeRangeCollectionTypeReplaceRanges`、 `replacementDuration` は、 `replacementDuration`. 次の場合、 `replacementDuration` が設定されていない場合、広告サーバーは、その配置オポチュニティの広告の期間と数を決定します。

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges`  — 新しいタイプの `PTAdSignalingMode`. このモードは、 `PTTimeRangeCollection` タイプ `PTTimeRangeCollectionReplace` 置換範囲に基づく広告挿入の場合。

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection`  — 再生コンテンツの範囲のマーク/削除/置換で使用される時間範囲を設定する場合。

* 警告ログ：

   * `UNDEFINED_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 広告シグナリングモードは、カスタム範囲として定義されますが、カスタム範囲は定義されません。

   * `INVALID_TIME_RANGES`

      * タイプ — 警告
      * 説明 — 1 つ以上の時間範囲が無効で、無視または変更されます。

**非推奨（廃止予定）の API**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges`  — このプロパティは、以前、マーキングの C3 範囲を定義するために使用されていました。 これらの範囲は `PTTimeRangeCollection`.
