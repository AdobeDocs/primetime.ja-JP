---
description: TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-description: TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-title: 広告削除および置換APIの変更
title: 広告削除および置換APIの変更
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 広告削除および置換APIの変更 {#ad-deletion-and-replacement-api-changes}

TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。

* `AdSignalingMode` シグナリングモ `CUSTOM_RANGES` ードを追加しました。

* `OpportunityGenerator`  `extractAdSignalingMode()` — 置換範 `AdSignalingMode.CUSTOM_RANGES` 囲がメタデータ内にある場合に設定します。

* `PlacementType` タイプを追 `CUSTOM_RANGE` 加しました。

* `PlacementMode`

   * モードを追 `DELETE` 加しました。
   * モードの `MARK` 追加
   * 追加さ `FreeReplace` れたモード — このモードは継続時間を持ちますが、純粋な挿入です。

* `TimeRange` クラスを廃止しま `final` した

* メソッドの `ReplaceTimeRange()` 追加

   拡張がプ `TimeRange` ロパティを持つよ `replacementDuration` うになる。 MARKおよびDELETEの場合、は0 `replacementDuration` です。

* `TimeRangeCollection`

   * 抽出するユ `toReplaceMetadata()` ーティリティ関数を追加しまし `timeRanges`た。

   * およびで動作するように変更されま `DELETE` した `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * 追加 `createCustomTimeRangesFrom()` - JSONファイルからMARK/DELETE/REPLACEの使用例のメタデータを作成します。
   * 削除 `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * 追加済み `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * 追加済み `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` （変更なし）

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * メタデータ `CustomRangesOpportunityGenerator` にカスタム範囲が含まれる場合に対して追加されました。
   * `doRetrieveResolvers()`

      * DELETEおよ `CustomRangeResolver` びREPLACEカスタム範囲がメタデータに存在する場合に追加
      * 次より `CustomAdMarkerResolver` 前に移動 `AuditudeResolver`


* 追加済み `CustomRangeOpportunityGenerator`

   * `doUpdate()` 空のまま — 更新なし、VOD
   * `doProcess()` 新しいタイプの新しい配置を作成します `Placement.Delete_Range`

   * のジェ `CustomRangeOppotunityGenerator` ネレーターリストの先頭に追加されたので、 `DefaultContentFactory`広告挿入の前に削除範囲が処理されます。

   * すべてのオ `createCustomRangeOpportunities` ポチュニティを作成するために追加されました

      MARK — およびの有効なマーク範囲ごとに1つのオポチュニテ `PlacementType.CUSTOM_RANGE` ィ `PlacementMode.MARK`

      DELETE — およびの有効な削除範囲ごとに1つのオポチュニテ `PlacementType.CUSTOM_RANGE` ィ `PlacementMode.DELETE`

      REPLACE — 有効な置換範囲ごとに2つのオポチュニティ：

      1. およびの範囲の削除オポチュニテ `PlacementType.CUSTOM_RANGE` ィで `PlacementMode.DELETE`す。

      1. またはおよびのPrimetime ad decisioningの広 `PlacementType.MID_ROLL` 告オポチュニテ `PlacementType.PRE_ROLL` ィ `PlacementMode.FREEREPLACE`

* 追加され `CustomRangeResolver`た：

   * `doCanResolve()` 削除範 `true` 囲に対してを返します。

   * 配置用 `createDeleteRangeOperation()` に作成す `DeleteRange` るために追加

* 追加され `CustomRangeHelper`た：

   * マーク/削除/置換を抽出して処理する共通のユーテ `timeRanges` ィリティクラス。
   * 追加済み `extractCustomRangesMetadata()`
   * 追加済み `extractCustomRanges()`
   * 追加され `mergeRanges()` た — 競合とサブセット/結合を解決します。

* `MediaPlayerTimeline`:

   * &quot;>で、操作 `executeOperation()`がある場合は、操 `DeleteRange`作内のメソッドを削除する呼び出しを追加

   * で、操 `executeOperation()`作が(サーバーから `NOPTimelineOperation` の空の) `AdBreaks` 場合、クリアする呼び出しを追加しました。

   * 追加済み `onDeleteRangeComplete()`
   * 追加済み `removeRange()`
   * モード `adjustPlacement()`の場合、 `PlacementMode.FREEREPLACE` 長さをゼロにします。 この時間は、リクエスト時に `AdBreaks`はより早く必要です。この時点で純粋な挿入を行うには、ゼロにする必要があります。

* `VideoEngineTimeline` 追加さ `removeC3Ad()` れた — 削除範 `removeByLocalTime()` 囲の呼び出し

* `AdSignalingModeGenerator`

   * `doConfigure()`  — オポチュニティが生成されない場合は解決しない
   * `createInitialOpportunity()`  — の初期オポチュニティを生成しませ `AdSignalingMode.CUSTOM_RANGE`ん。 もうこ `CustomRangeOpportunityGenerator` れを隠してる。

* `DeleteRange`

   * 拡張 `TimelineOperation`。
   * 削除および置 `CustomRangeResolver` 換（置換の削除部分）のために作成

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5`  — 梱包を許可
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` 異なる `accepts()` 配置タイプ（プリロール、ミッドロール、ポストロール）のパッキングを許可するようにメソッドを変更しました。

* `AuditudeRequestHelper` 広告パラメーターのサーバー上書きを許可するバグを修正しました。

* `AuditudeResolver` 梱包を許 `canBePacked()` 可する方法が変更されました

* `CustomAdResolver` 抽出関 `timeRange` 数は削除されました。 一度に1つの配置を得て、それを1つに変えます `AdBreakPlacement timelineOperation`。

