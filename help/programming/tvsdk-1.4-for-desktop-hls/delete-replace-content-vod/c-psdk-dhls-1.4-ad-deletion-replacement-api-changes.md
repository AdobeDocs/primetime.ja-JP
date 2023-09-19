---
description: TVSDK に加えられた以下の変更は、広告の削除と置き換えをサポートします。
title: 広告の削除と置き換え API の変更
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 広告の削除と置き換え API の変更 {#ad-deletion-and-replacement-api-changes}

TVSDK に加えられた以下の変更は、広告の削除と置き換えをサポートします。

* `AdSignalingMode` 追加済み `CUSTOM_RANGES` シグナリングモード。

* `OpportunityGenerator`  `extractAdSignalingMode()`  — 設定 `AdSignalingMode.CUSTOM_RANGES` 置換範囲がメタデータ内にある場合。

* `PlacementType` 追加済み `CUSTOM_RANGE` タイプ。

* `PlacementMode`

   * 追加済み `DELETE` モード。
   * 追加済み `MARK` mode
   * 追加済み `FreeReplace` mode — このモードはデュレーションを持ちますが、純粋な挿入です。

* `TimeRange` 今後の a は不要 `final` クラス

* 追加済み `ReplaceTimeRange()` メソッド

  拡張 `TimeRange` 持っている `replacementDuration` プロパティ。 MARK とDELETEの場合 `replacementDuration` は 0 です。

* `TimeRangeCollection`

   * 追加済み `toReplaceMetadata()` 抽出するユーティリティ機能 `timeRanges`.

   * を操作するように変更されました `DELETE` および `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * 追加済み `createCustomTimeRangesFrom()` - JSON ファイルから MARK/DELETE/REPLACE ユースケースのメタデータを作成します。
   * 削除済み `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * 追加済み `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * 追加済み `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` （変更されませんでした）

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * 追加済み `CustomRangesOpportunityGenerator` （メタデータにカスタム範囲が含まれる場合）

   * `doRetrieveResolvers()`

      * 追加 `CustomRangeResolver` ( メタデータにDELETEと置換のカスタム範囲が存在する場合 )
      * 移動済み `CustomAdMarkerResolver` ～より前に `AuditudeResolver`

* 追加済み `CustomRangeOpportunityGenerator`

   * `doUpdate()` 空のまま — 更新なし、VOD
   * `doProcess()` 新しいタイプの新しい配置を作成します `Placement.Delete_Range`

   * 追加済み `CustomRangeOppotunityGenerator` を `DefaultContentFactory`の場合、削除範囲は、広告挿入の前に処理されます。

   * 追加済み `createCustomRangeOpportunities` すべての商談を作成するには

     MARK — 有効なマーク範囲ごとに 1 つの商談 `PlacementType.CUSTOM_RANGE` および `PlacementMode.MARK`

     DELETE — 次の有効な削除範囲ごとに 1 つのオポチュニティ `PlacementType.CUSTOM_RANGE` および `PlacementMode.DELETE`

     REPLACE — 有効な置換範囲ごとに 2 つのオポチュニティ：

      1. 次の範囲を削除する機会： `PlacementType.CUSTOM_RANGE` および `PlacementMode.DELETE`.

      1. 次の Primetime ad decisioning 広告オポチュニティ `PlacementType.MID_ROLL` または `PlacementType.PRE_ROLL` および `PlacementMode.FREEREPLACE`

* 追加済み `CustomRangeResolver`:

   * `doCanResolve()` 戻り値 `true` （範囲を削除する場合）

   * 追加済み `createDeleteRangeOperation()` を作成します。 `DeleteRange` 配置の

* 追加済み `CustomRangeHelper`:

   * マーク/削除/置換を抽出する共通ユーティリティクラス `timeRanges` そしてそれらを処理する。
   * 追加済み `extractCustomRangesMetadata()`
   * 追加済み `extractCustomRanges()`
   * 追加済み `mergeRanges()`  — 競合とサブセット/結合を解決します。

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()`( 操作が `DeleteRange`、操作でメソッドを削除するための呼び出しを追加しました。

   * In `executeOperation()`( 操作が `NOPTimelineOperation` ( 空 `AdBreaks` サーバーから戻る )、クリアするための呼び出しを追加しました。

   * 追加済み `onDeleteRangeComplete()`
   * 追加済み `removeRange()`
   * In `adjustPlacement()`の場合は `PlacementMode.FREEREPLACE` モードで、デュレーションをゼロにします。 リクエスト時に、この期間がより早く必要です `AdBreaks`の場合は、この時点で、純粋な挿入にするにはゼロにする必要があります。

* `VideoEngineTimeline` 追加済み `removeC3Ad()`  — 呼び出し `removeByLocalTime()` 範囲を削除

* `AdSignalingModeGenerator`

   * `doConfigure()`  — オポチュニティが生成されない場合は解決しない
   * `createInitialOpportunity()`  — 次の初期オポチュニティを生成しない `AdSignalingMode.CUSTOM_RANGE`. The `CustomRangeOpportunityGenerator` 既にこれをカバーしています。

* `DeleteRange`

   * 拡張 `TimelineOperation`.
   * 作成者 `CustomRangeResolver` 削除および置換（置換の削除部分）

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5`  — 梱包を許可
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` The `accepts()` 異なる配置タイプ（プリロール、ミッドロール、ポストロール）の保圧を可能にするようにメソッドを変更しました。

* `AuditudeRequestHelper` 広告パラメーターのサーバー上書きを許可するバグを修正しました。

* `AuditudeResolver` The `canBePacked()` メソッドは、保圧を許可するように変更されました

* `CustomAdResolver` The `timeRange` 抽出関数は削除されました。 一度に 1 つの場所を取得し、それを `AdBreakPlacement timelineOperation`.
