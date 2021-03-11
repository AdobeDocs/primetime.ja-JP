---
description: Android TVSDK APIの以下の変更は、広告の削除と置換をサポートします。
title: 広告削除および置換APIの変更
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# 広告削除および置換APIの変更{#ad-deletion-and-replacement-api-changes}

Android TVSDK APIの以下の変更は、広告の削除と置換をサポートします。

* `AdSignalingMode` 新しいカスタム時間範囲広告シグナリングモード

* `AdvertisingMetadata` 新規 `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`:メタデータの処理時にマーク、削除または置換する時間範囲を設定します

* `ContentResolver`

   * 新しい`public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * 新しい`protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* 新しい`ContentRemoval`クラス

   `TimelineOperation` タイムラインから削除する時間範囲を定義するクラス

* `AuditudeResolver`

   * 新しい`private LinkedList<AuditudeRequest> _requestQueue`
   * 新しい`void startConsumer()`:Primetime ad decisioningリクエストキューを処理する開始。各リクエストが`MIN_INIT_REQUEST_INTERVAL`間隔で発行されるようにします。

   * 新しい`processReplacementRange()`:広告メタデータから時間範囲を抽出し、`PlacementInformations`を生成し、`PlacementInformations`を含むPrimetime ad decisioningリクエストを作成します。

   * 新しい`canDoResolver()`:配置オポチュニティにPrimetime ad decisioningメタデータがあるかどうかを確認します

* 広告メタデータから時間範囲メタデータを抽出し、サブセット/オーバーラップ/無効な時間範囲を削除する新しい`CustomRangeHelper`ヘルパークラス。

* 新しい`DeleteContentResolver``PlacementInformation.Mode.DELETE`の配置オポチュニティを解決するコンテンツリゾルバー

* 新しい`NopTimelineOperation`広告の時間の配置や置き換えを行う必要がない場合の新しいタイムライン操作。 このクラスは、これを区別する目的と、解決プロセス中にエラーが発生した場合に使用されます。

* `TimelineOperationQueue` タイムライン操作が処理 `NopTimelineOperation` 前の操作かどうかを確認します。

* `CustomAdMarkersContentResolver` 新規 `canDoResolve()`:配置オポチュニティのタイプが  `Mode.MARK`

* `MetadataResolver` 新規 `canDoResolve()`:配置オポチュニティのタイプが  `Mode.INSERT`

* `DefaultMetadataKeys` 新規  `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * 新しいモード`enum (INSERT, DELETE, REPLACE, MARK)`
   * 新しいタイプ`CUSTOM_TIME_RANGES`

* `TimeRange` 新規 `compareTo(TimeRange timeRange)`:したがって、開始時間に基づいてTimeRangesを並べ替えることができます。

* 新しい`ReplacementTimeRange`は、置き換え時間範囲を表す`TimeRange`クラスを拡張し、`begin`、`end`、`replacement-duration`パラメーターを使用します。

* `TimeRangeCollection`

   * 新しい`MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * `CUSTOM_AD_MARKERS`の名前を`MARK_RANGES`に変更

   * `toMetadata(Metadata options)`が変更され、広告メタデータに削除/マーク/置換範囲が追加されました。

* `MediaPlayerNotification`

   * 新しい`UNDEFINED_TIME_RANGES`:広告シグナリングモードがサーバーマップまたはマニフェストキューで、広告メタデータにも置換範囲が含まれる場合、置換範囲は無視されます。
   * 新しい`REPLACE_RANGES_NOT_AVAILABLE`:広告シグナリングモードがカスタム時間範囲の場合に、置換範囲が使用できないと、警告がディスパッチされます。

* `AdvertisingFactory` 新規  `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` 新規  `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` 新規  `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * `prepareToPlay()`内：範囲`[0,n]`が削除された場合、メディアプレイヤーは自動的に再生を行わないので、初期シークを0にします。

   * `prepareToPlay()`内：解決する`mediaplayerclient`の初期配置情報のリストをループ処理します。

   * `extractAdSignalingMode()`内：新しいカスタム時間範囲モードに対応。
   * 新しい`private static List<PlacementInformation> createInitalPlacementInformations()`:広告シグナリングモードとコンテンツリゾルバー（広告メタデータから派生）に関する初期配置情報を生成します。
   * `ContentPlacementCompletedListener`内：`endAdResolving`を呼び出す前に、`mediaPlayerClient`が`doneInitialResolving`かどうかを確認します。

* `MediaPlayerClient`

   * 新しい`List<ContentResolver> _contentResolvers`
   * 新しい`int _reservations`
   * 新しい`lookupContentResolver(PlacementOpportunity placementOpportunity)`:`PlacementOpportunity`を解決できるリゾルバーを検索します。

   * 複数のコンテンツリゾルバーを作成するように変更されました。
   * 新しい`public boolean doneInitialResolving()`:解決するオポチュニティが残っているかどうかを確認します。

* `VideoEngineTimeline`

   * 新しい`removeContent(TimelineOperation timelineOperation)`:指定された範囲のコンテンツをタイムラインから削除します。
   * 新しい`removeContentByLocalTime(long begin, long end)`:`begin`と`end`を指定して、ローカル時間でコンテンツを削除します。

* `DefaultOpportunityDetectorFactory` 変更 `createOpportunityDetector`日：VODストリームの場合、MARK範囲またはREPLACE範囲がない `SpliceOutOpportunityDetector` 場合（これらの範囲はシグナリングモードよりも優先されるので）、新しい範囲のみが返されます。

