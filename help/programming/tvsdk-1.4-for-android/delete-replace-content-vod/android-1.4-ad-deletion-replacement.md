---
description: Android TVSDK API の以下の変更は、広告の削除と置換をサポートします。
title: 広告の削除と置き換え API の変更
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# 広告の削除と置き換え API の変更{#ad-deletion-and-replacement-api-changes}

Android TVSDK API の以下の変更は、広告の削除と置換をサポートします。

* `AdSignalingMode` 新しいカスタム時間範囲広告シグナリングモード

* `AdvertisingMetadata` 新規 `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`：メタデータの処理時にマーク、削除または置換する時間範囲を設定します

* `ContentResolver`

   * 新規 `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * 新規 `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* 新規 `ContentRemoval` クラス

  `TimelineOperation` タイムラインから削除する時間範囲を定義するクラス

* `AuditudeResolver`

   * 新規 `private LinkedList<AuditudeRequest> _requestQueue`
   * 新規 `void startConsumer()`: Primetime ad decisioning リクエストキューの処理を開始し、各リクエストが次の時点で発行されるようにします。 `MIN_INIT_REQUEST_INTERVAL` 間隔

   * 新規 `processReplacementRange()`：広告メタデータから時間範囲を抽出し、を生成します。 `PlacementInformations`を作成し、 `PlacementInformations`.

   * 新規 `canDoResolver()`：配置オポチュニティに Primetime ad decisioning メタデータがあるかどうかを確認します

* 新規 `CustomRangeHelper` 広告メタデータから時間範囲メタデータを抽出し、サブセット/重複/無効な時間範囲を削除するヘルパークラス。

* 新規 `DeleteContentResolver` 次の場所に配置する機会を解決するコンテンツリゾルバー `PlacementInformation.Mode.DELETE`

* 新規 `NopTimelineOperation` 広告ブレークの配置や置き換えをおこなう必要がない場合に使用する、新しいタイムライン操作。 このクラスは、これを区別するために使用され、解決プロセス中にエラーが発生した場合に使用されます。

* `TimelineOperationQueue` タイムライン操作が `NopTimelineOperation` 処理の前に

* `CustomAdMarkersContentResolver` 新規 `canDoResolve()`：配置オポチュニティのタイプがであるかどうかをチェックします `Mode.MARK`

* `MetadataResolver` 新規 `canDoResolve()`：配置オポチュニティのタイプがであるかどうかをチェックします `Mode.INSERT`

* `DefaultMetadataKeys` 新規 `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * 新しいモード `enum (INSERT, DELETE, REPLACE, MARK)`
   * 新しいタイプ `CUSTOM_TIME_RANGES`

* `TimeRange` 新規 `compareTo(TimeRange timeRange)`：開始時間に基づいて TimeRanges を並べ替えることができます。

* 新規 `ReplacementTimeRange` を `TimeRange` 置き換え時間範囲を表すクラスで、 `begin`, `end`、および `replacement-duration` パラメーター。

* `TimeRangeCollection`

   * 新規 `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * 名前を変更 `CUSTOM_AD_MARKERS` から `MARK_RANGES`

   * 変更済み `toMetadata(Metadata options)` を使用して、広告メタデータに削除/マーク/置換範囲を追加します。

* `MediaPlayerNotification`

   * 新規 `UNDEFINED_TIME_RANGES`：広告シグナリングモードがサーバーマップまたはマニフェストキューで、置き換え範囲が広告メタデータにも含まれている場合、置き換え範囲は無視されます。
   * 新規 `REPLACE_RANGES_NOT_AVAILABLE`：広告シグナリングモードがカスタム時間範囲で、置換範囲が使用できない場合は、警告がディスパッチされます。

* `AdvertisingFactory` 新規 `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` 新規 `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` 新規 `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`：範囲がの場合、最初のシークを 0 にします。 `[0,n]` を削除すると、メディアプレーヤーは自動的には再生されません。

   * In `prepareToPlay()`：の初期配置情報のリストをループ処理します。 `mediaplayerclient` 解決するには

   * In `extractAdSignalingMode()`：新しいカスタム時間範囲モードに対応します。
   * 新規 `private static List<PlacementInformation> createInitalPlacementInformations()`：広告シグナリングモードとコンテンツリゾルバーに関する初期配置情報を生成します（広告メタデータから派生）。
   * In `ContentPlacementCompletedListener`：をチェックして、 `mediaPlayerClient` 次に該当 `doneInitialResolving` 呼び出し前 `endAdResolving`.

* `MediaPlayerClient`

   * 新規 `List<ContentResolver> _contentResolvers`
   * 新規 `int _reservations`
   * 新規 `lookupContentResolver(PlacementOpportunity placementOpportunity)`: `PlacementOpportunity`.

   * 複数のコンテンツリゾルバーを作成するようにコードを変更しました。
   * 新規 `public boolean doneInitialResolving()`：解決するオポチュニティが残っているかどうかを確認します。

* `VideoEngineTimeline`

   * 新規 `removeContent(TimelineOperation timelineOperation)`：特定の範囲のコンテンツをタイムラインから削除します。
   * 新規 `removeContentByLocalTime(long begin, long end)`：指定されたローカル時間でコンテンツを削除します `begin` および `end`.

* `DefaultOpportunityDetectorFactory` 変更済み `createOpportunityDetector`:VOD ストリームの場合、新しい `SpliceOutOpportunityDetector` MARK または REPLACE 範囲がない場合（これらの範囲はシグナリングモードよりも優先されるため）。
