---
description: Android TVSDK APIに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-description: Android TVSDK APIに加えられた以下の変更は、広告の削除と置換をサポートします。
seo-title: 広告削除および置換APIの変更
title: 広告削除および置換APIの変更
uuid: 2bb8a331-6851-4442-99de-b01500a0e1e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告削除および置換APIの変更{#ad-deletion-and-replacement-api-changes}

Android TVSDK APIに加えられた以下の変更は、広告の削除と置換をサポートします。

* `AdSignalingMode` 新しいカスタム時間範囲広告シグナリングモード

* `AdvertisingMetadata` 新規 `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`:メタデータを処理する際に、マーク、削除または置換する時間範囲を設定します

* `ContentResolver`

   * 新規 `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * 新規 `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* 新しいク `ContentRemoval` ラス

   `TimelineOperation` タイムラインから削除する時間範囲を定義するクラス。

* `AuditudeResolver`

   * 新規 `private LinkedList<AuditudeRequest> _requestQueue`
   * 新規 `void startConsumer()`:Primetime ad decisioningリクエストキューの処理を開始し、各リクエストが一定の間隔で発行されるように `MIN_INIT_REQUEST_INTERVAL` します

   * 新規 `processReplacementRange()`:広告メタデータから時間範囲を抽出し、そ `PlacementInformations`れを含むPrimetime ad decisioningリクエストを生成しま `PlacementInformations`す。

   * 新規 `canDoResolver()`:配置オポチュニティにPrimetime ad decisioningメタデータが含まれているかどうかを確認します

* 広告メタ `CustomRangeHelper` データから時間範囲メタデータを抽出し、サブセット/重複/無効な時間範囲を削除する新しいヘルパークラス。

* 次の配置 `DeleteContentResolver` オポチュニティを解決する新しいコンテンツリゾルバー `PlacementInformation.Mode.DELETE`

* 広告の時 `NopTimelineOperation` 間の配置や置換を行う必要がない場合の新しいタイムライン操作。 このクラスは、これを区別する目的と、解決プロセス中にエラーが発生した場合に使用されます。

* `TimelineOperationQueue` タイムライン操作が処理の前の操作かどうかを `NopTimelineOperation` 確認します。

* `CustomAdMarkersContentResolver` 新規 `canDoResolve()`:配置オポチュニティのタイプが `Mode.MARK`

* `MetadataResolver` 新規 `canDoResolve()`:配置オポチュニティのタイプが `Mode.INSERT`

* `DefaultMetadataKeys` 新規 `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * 新しいモード `enum (INSERT, DELETE, REPLACE, MARK)`
   * 新しいタイプ `CUSTOM_TIME_RANGES`

* `TimeRange` 新規 `compareTo(TimeRange timeRange)`:したがって、開始時間に基づいてTimeRangesを並べ替えることができます。

* [新規] `ReplacementTimeRange` は、置 `TimeRange` 換時間範囲を表すクラスを、、、およびのパ `begin`ラメー `end`タで拡張 `replacement-duration` します。

* `TimeRangeCollection`

   * 新規 `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * 名前を `CUSTOM_AD_MARKERS` 次に `MARK_RANGES`

   * 削除/マ `toMetadata(Metadata options)` ーク/置換の範囲を広告メタデータに追加するように変更されました。

* `MediaPlayerNotification`

   * 新規 `UNDEFINED_TIME_RANGES`:広告シグナリングモードがサーバーマップまたはマニフェストキューで、置換範囲も広告メタデータに含まれている場合、置換範囲は無視されます。
   * 新規 `REPLACE_RANGES_NOT_AVAILABLE`:広告シグナリングモードがカスタム時間範囲で、置換範囲が使用できない場合、警告がディスパッチされます。

* `AdvertisingFactory` 新規 `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` 新規 `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` 新規 `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * 対象 `prepareToPlay()`:範囲が削除されると、メディアプレイヤーは自動的に再 `[0,n]` 生されないので、初期シークを0にします。

   * 対象 `prepareToPlay()`:解決するための初期配置情報のリストをルー `mediaplayerclient` プします。

   * 対象 `extractAdSignalingMode()`:新しいカスタム時間範囲モードに対応。
   * 新規 `private static List<PlacementInformation> createInitalPlacementInformations()`:広告シグナリングモードとコンテンツリゾルバー（広告メタデータから派生）に関する初期配置情報を生成します。
   * 対象 `ContentPlacementCompletedListener`:が呼び出す前に存在するかどうかを `mediaPlayerClient` 確認 `doneInitialResolving` しま `endAdResolving`す。

* `MediaPlayerClient`

   * 新規 `List<ContentResolver> _contentResolvers`
   * 新規 `int _reservations`
   * 新規 `lookupContentResolver(PlacementOpportunity placementOpportunity)`:どのリゾルバーがを解決できるかを調べま `PlacementOpportunity`す。

   * 複数のコンテンツリゾルバーを作成するようにコードを変更。
   * 新規 `public boolean doneInitialResolving()`:解決するオポチュニティが残っているかどうかを確認します。

* `VideoEngineTimeline`

   * 新規 `removeContent(TimelineOperation timelineOperation)`:指定した範囲のコンテンツをタイムラインから削除します。
   * 新規 `removeContentByLocalTime(long begin, long end)`:とを指定して、ローカル時間でコンテンツを `begin` 削除しま `end`す。

* `DefaultOpportunityDetectorFactory` 変更 `createOpportunityDetector`日：VODストリームの場合、MARK範囲またはREPLACE範囲がな `SpliceOutOpportunityDetector` い場合（これらの範囲はシグナリングモードより優先されるので）、新しい範囲のみが返されます。

