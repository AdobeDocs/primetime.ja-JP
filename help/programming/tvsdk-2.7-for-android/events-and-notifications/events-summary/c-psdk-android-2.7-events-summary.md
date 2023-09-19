---
description: アプリケーションは、TVSDK によってディスパッチされるイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化を監視できます。
title: Primetime プレーヤーイベントの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# Primetime プレーヤーイベントの概要 {#primetime-player-events-summary-overview}

アプリケーションは、TVSDK によってディスパッチされるイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化を監視できます。

## イベント {#events}

TVSDK は、アプリケーションが応答する必要のあるイベントが発生したときに通知します。 各イベントは、実装する必要のあるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは、 `MediaPlayerEvent` enum.

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* **つまり**広告ブレークの再生が完了します。

* **実装するコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* **つまり**再生中に広告の時間がスキップされました。

* **実装するコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* **つまり**広告ブレークの再生が開始しました。

* **実装するコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* **つまり**再生中に広告がクリックされました。

* **実装するコールバック** `onAdClicked(AdClickEvent event)`

* **イベントコード** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* **つまり**広告の再生が完了しました。

* **実装するコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* **つまり、**再生中の進行状況のレポート。

* **実装するコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* **つまり、** Primetime ad decisioningad の解決が完了しました。 このイベントは、VOD コンテンツにのみ適用できます。

* **実装するコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* **つまり**広告の再生が開始されました。

* **実装するコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* **意味**新しいオーディオトラックが検出されました。

* **実装するコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* **つまり**プレーヤーがバッファリングを開始しました。

* **実装するコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* **つまり**プレーヤーがバッファリングを停止しました。

* **実装するコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* **意味**バッファが準備されました。

* **実装するコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* **意味**新しいキャプショントラックが検出されました。

* **実装するコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* **意味**メディアストリームで新しい DRM メタデータが検出されました。

* **実装するコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* **つまり**新しいメディアプレーヤーアイテムが作成されました。

* **実装するコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* **意味**現在の項目に対して新しい読み込み情報が作成されました。

* **実装するコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* **意味**新しいセグメントが読み込まれました。

* **実装するコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* **意味**メインのマニフェストまたはプレイリストが更新されました。

* **実装するコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* **意味**操作が失敗しました。

* **実装するコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* **つまり**再生範囲が更新されました。

* **実装するコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* **つまり**新しい再生レートが画面に表示されます。

* **実装するコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* **つまり** MediaPlayer のレート属性が設定されています。

* **実装するコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* **つまり**再生が開始されました。

* **実装するコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* **つまり** MediaPlayer の現在のプロファイルが変更されました。

* **実装するコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* **つまり、**再生がタイムラインの予約に到達しました。

* **実装するコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* **つまり**シーク操作が開始されました。

* **実装するコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* **意味**シーク操作が完了しました。

* **実装するコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* **意味**内部再生ルールまたは外部ビジネスルールが原因で、シーク位置が調整されました。

* **実装するコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* **つまり**メディアのサイズが使用可能です。

* **実装するコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* **つまり** MediaPlayer の状態が変更されました。

* **実装するコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* **つまり**再生ヘッドが変更されました。

* **実装するコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* **意味**操作は、操作に要した時間で完了します。

* **実装するコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* **つまり**バックグラウンドの項目に新しい時間指定メタデータが追加されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* **意味**メディアストリームで新しい時間指定メタデータが検出されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* **意味**タイムラインが変更されました。 広告がタイムラインに追加または削除された可能性があります。

* **実装するコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`
