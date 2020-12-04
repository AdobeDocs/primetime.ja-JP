---
description: TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-description: TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-title: 広告削除および置換APIの変更
title: 広告削除および置換APIの変更
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# 広告削除および置換APIの変更{#ad-deletion-and-replacement-api-changes}

TVSDKに加えられた以下の変更は、広告の削除と置換をサポートします。

* `AdSignalingMode` シグナリング `CUSTOM_RANGES` モードが追加されました。

* `OpportunityGenerator`  `extractAdSignalingMode()`  — 置換範囲がメタデータ内にある `AdSignalingMode.CUSTOM_RANGES` 場合に設定します。

* `PlacementType` タイプを追加 `CUSTOM_RANGE` しました。

* `PlacementMode`

   * `DELETE`モードを追加しました。
   * `MARK`モードを追加しました
   * `FreeReplace`モードが追加されました — このモードは継続時間を持ちますが、純粋な挿入です

* `TimeRange` クラスの廃止 `final` 

* `ReplaceTimeRange()`メソッドの追加

   `TimeRange`を拡張して`replacementDuration`プロパティを持つようにします。 MARKとDELETEの場合、`replacementDuration`は0です。

* `TimeRangeCollection`

   * `timeRanges`を抽出する`toReplaceMetadata()`ユーティリティ関数が追加されました。

   * `DELETE`と`REPLACE`で動作するように変更

   * `METADATA_KEY_CUSTOM_MARK_RANGES`,  `METADATA_KEY_CUSTOM_DELETE_RANGES`  `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * `createCustomTimeRangesFrom()`の追加 — JSONファイルからMARK/DELETE/REPLACE使用例のメタデータを作成します。
   * 削除`createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * `CUSTOM_DELETE_RANGES_METADATA_KEY`を追加
   * `CUSTOM_REPLACE_RANGES_METADATA_KEY`を追加
   * `CUSTOM_AD_MARKERS_METADATA_KEY` （変更なし）

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * メタデータにカスタム範囲が含まれる場合に`CustomRangesOpportunityGenerator`を追加
   * `doRetrieveResolvers()`

      * &lt;a0/追加>DELETEとREPLACEカスタム範囲がメタデータに存在する場合`CustomRangeResolver`
      * `CustomAdMarkerResolver`を`AuditudeResolver`の前に移動


* `CustomRangeOpportunityGenerator`を追加

   * `doUpdate()` 空のまま — 更新なし、VOD
   * `doProcess()` 新しいタイプの新しい配置を作成します  `Placement.Delete_Range`

   * `DefaultContentFactory`のgeneratorsリストの先頭に`CustomRangeOppotunityGenerator`が追加されたので、広告挿入の前に削除範囲が処理されます。

   * すべてのオポチュニティを作成するために`createCustomRangeOpportunities`を追加しました

      MARK - `PlacementType.CUSTOM_RANGE`と`PlacementMode.MARK`の有効なマーク範囲ごとに1つのオポチュニティ

      DELETE- `PlacementType.CUSTOM_RANGE`と`PlacementMode.DELETE`の有効な削除範囲ごとに1つのオポチュニティ

      REPLACE — 有効な置換範囲ごとに2つのオポチュニティ：

      1. `PlacementType.CUSTOM_RANGE`と`PlacementMode.DELETE`の削除範囲オポチュニティ。

      1. `PlacementType.MID_ROLL`または`PlacementType.PRE_ROLL`と`PlacementMode.FREEREPLACE`のPrimetime ad decisioningの広告オポチュニティ

* `CustomRangeResolver`を追加：

   * `doCanResolve()` 削除範囲 `true` に対してを返します。

   * 配置の`DeleteRange`を作成する`createDeleteRangeOperation()`を追加しました

* `CustomRangeHelper`を追加：

   * `timeRanges`のマーク/削除/置換を抽出して処理する共通ユーティリティクラス。
   * `extractCustomRangesMetadata()`を追加
   * `extractCustomRanges()`を追加
   * `mergeRanges()`の追加 — 競合やサブセット/結合を解決します。

* `MediaPlayerTimeline`:

   * &quot;>`executeOperation()`内で、操作が`DeleteRange`の場合、操作内のメソッドを削除する呼び出しを追加

   * `executeOperation()`で、操作が`NOPTimelineOperation` （空の`AdBreaks`がサーバーから戻ってくる）の場合、クリアする呼び出しを追加します。

   * `onDeleteRangeComplete()`を追加
   * `removeRange()`を追加
   * `adjustPlacement()`では、`PlacementMode.FREEREPLACE`モードの場合、長さをゼロにします。 `AdBreaks`をリクエストする場合は、この時間が早く必要になります。純粋な挿入にするには、この時点で0にする必要があります。

* `VideoEngineTimeline` 追加 `removeC3Ad()`  — 削除範囲 `removeByLocalTime()` の呼び出し

* `AdSignalingModeGenerator`

   * `doConfigure()`  — オポチュニティが生成されない場合は解決しない
   * `createInitialOpportunity()`  — の初期オポチュニティを生成し `AdSignalingMode.CUSTOM_RANGE`ません。`CustomRangeOpportunityGenerator`は既にこれを覆っています。

* `DeleteRange`

   * `TimelineOperation`を拡張します。
   * `CustomRangeResolver`が削除と置換（置換の削除部分）のために作成しました

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5`  — 梱包を許可
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` 異なる配置タイプ（プリロール、ミッドロール、ポストロール）のパッキングが可能になるように `accepts()` メソッドが変更されました。

* `AuditudeRequestHelper` サーバーが広告パラメーターを上書きできるようにバグを修正しました。

* `AuditudeResolver` 梱包を許可する `canBePacked()` 方法が変更されました

* `CustomAdResolver`  `timeRange` 抽出関数は削除されました。一度に1つの場所を取得し、`AdBreakPlacement timelineOperation`にします。

