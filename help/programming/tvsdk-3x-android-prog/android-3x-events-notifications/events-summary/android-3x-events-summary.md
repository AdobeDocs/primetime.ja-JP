---
description: アプリケーションは、TVSDK によってディスパッチされるイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化を監視できます。
title: Primetime プレーヤーイベントの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Primetime プレーヤーイベントの概要 {#primetime-player-events-summary}

アプリケーションは、TVSDK によってディスパッチされるイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化を監視できます。

## イベント {#events}

TVSDK は、アプリケーションが応答する必要のあるイベントが発生したときに通知します。 各イベントは、実装する必要のあるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは、 `MediaPlayerEvent` enum.

`AdBreakCompletedEventListener`

* **意味** 広告ブレークの再生が完了します。

* **実装するコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **意味** 再生中に広告の時間がスキップされました。

* **実装するコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **意味** 広告ブレークの再生が開始しました。

* **実装するコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

`AdClickedEventListener`

* **意味** 再生中に広告がクリックされました。

* **実装するコールバック** `onAdClicked(AdClickEvent event)`
* **イベントコード** `AD_CLICK`

`AdCompletedEventListener`

* **意味** 広告の再生が完了しました。

* **実装するコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

`AdProgressEventListener`

* **意味** 再生中の進行状況のレポート。

* **実装するコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **意味** Primetime ad decisioning 広告の解決が完了しました。 このイベントは、VOD コンテンツにのみ適用できます。

* **実装するコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **意味** 広告の再生が開始しました。

* **実装するコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

`AudioUpdatedEventListener`

* **意味** 新しいオーディオトラックが検出されました。

* **実装するコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **意味** プレーヤーがバッファリングを開始しました。

* **実装するコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **意味** プレーヤーがバッファリングを停止しました。

* **実装するコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

`BufferPreparedEventListener`

* **意味** バッファが準備されます。

* **実装するコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **意味** 新しいキャプショントラックが検出されました。

* **実装するコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **意味** メディアストリームで新しい DRM メタデータが検出されました。

* **実装するコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

`ItemCreatedEventListener`

* **意味** 新しいメディアプレーヤーアイテムが作成されました。

* **実装するコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **意味** 現在の項目に対して新しい読み込み情報が作成されました。

* **実装するコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

`LoadInformationEventListener`

* **意味** 新しいセグメントが読み込まれました。

* **実装するコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **意味** メインのマニフェストまたはプレイリストが更新されました。

* **実装するコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

`NotificationEventListener`

* **意味** 操作に失敗しました。

* **実装するコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **意味** 再生範囲が更新されました。

* **実装するコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **意味** 新しい再生レートが画面に表示されます。

* **実装するコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **意味** MediaPlayer の rate 属性が設定されている。

* **実装するコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

`PlayStartEventListener`

* **意味** 再生が開始されました。

* **実装するコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

`ProfileChangeEventListener`

* **意味** MediaPlayer の現在のプロファイルが変更されました。

* **実装するコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **意味** 再生がタイムラインの予約に到達しました。

* **実装するコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **意味** シーク操作が開始されました。

* **実装するコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

`SeekEndEventListener`

* **意味** シーク操作が終了しました。

* **実装するコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **意味** 内部再生ルールまたは外部ビジネスルールが原因で、シーク位置が調整されました。

* **実装するコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **意味** メディアのサイズを使用できます。

* **実装するコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **意味** MediaPlayer の状態が変更されました。

* **実装するコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

`TimeChangeEventListener`

* **意味** 再生ヘッドが変更されました。

* **実装するコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

`TimedEventEventListener`

* **意味** 操作が完了し、操作に要した時間が表示されます。

* **実装するコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **意味** バックグラウンドの項目に新しい時間指定メタデータが追加されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **意味** メディアストリームで新しい時間指定メタデータが検出されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **意味** タイムラインが変更されました。 広告がタイムラインに追加または削除された可能性があります。

* **実装するコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`
