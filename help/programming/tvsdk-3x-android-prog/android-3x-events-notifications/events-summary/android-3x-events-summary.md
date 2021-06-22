---
description: TVSDKがディスパッチするイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化をアプリケーションで監視できます。
title: Primetimeプレーヤーイベントの概要
exl-id: 3912f140-1600-41fb-9dc4-306646b7cd85
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Primetimeプレーヤーイベントの概要{#primetime-player-events-summary}

TVSDKがディスパッチするイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーのステータスの変化をアプリケーションで監視できます。

## イベント {#events}

TVSDKは、アプリケーションが応答する必要があるイベントが発生したときに通知します。 各イベントは、実装する必要があるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは`MediaPlayerEvent`列挙の定数です。

`AdBreakCompletedEventListener`

* **** つまり、広告ブレークの再生が完了します。

* **を実装するコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** 意味：再生中に広告の時間がスキップされました。

* **を実装するコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** つまり、広告ブレークの再生が開始されました。

* **を実装するコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

`AdClickedEventListener`

* **** 意味：再生中に広告がクリックされた。

* **を実装するコールバック** `onAdClicked(AdClickEvent event)`
* **イベントコード** `AD_CLICK`

`AdCompletedEventListener`

* **** つまり、広告の再生が完了します。

* **を実装するコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

`AdProgressEventListener`

* **** 再生中の進行状況の報告

* **を実装するコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** つまり、Primetime ad decisioningad resolutionが完了します。このイベントは、VODコンテンツにのみ適用できます。

* **を実装するコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** つまり、広告の再生が開始されました。

* **を実装するコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

`AudioUpdatedEventListener`

* **** 意味：新しいオーディオトラックが検出されました。

* **を実装するコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** 意味：プレーヤーがバッファリングを開始しました。

* **を実装するコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** 意味：プレーヤーがバッファリングを停止しました。

* **を実装するコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

`BufferPreparedEventListener`

* **** 意味バッファが準備されています。

* **を実装するコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** 意味：新しいキャプショントラックが検出されました。

* **を実装するコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** 意味：新しいDRMメタデータがメディアストリームで検出されました。

* **を実装するコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

`ItemCreatedEventListener`

* **** 意味：新しいメディアプレーヤーアイテムが作成されました。

* **を実装するコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** 意味現在の項目に対して新しい読み込み情報が作成されました。

* **を実装するコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** 意味：新しいセグメントが読み込まれました。

* **を実装するコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** 意味：メインのマニフェストまたはプレイリストが更新されました。

* **を実装するコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** 意味：操作が失敗しました。

* **を実装するコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** つまり、再生範囲が更新されました。

* **を実装するコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** つまり、新しい再生レートは画面に表示されます。

* **を実装するコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** つまり、MediaPlayerのレート属性が設定されています。

* **を実装するコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

`PlayStartEventListener`

* **** つまり、再生が開始されました。

* **を実装するコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

`ProfileChangeEventListener`

* **** つまり、MediaPlayerの現在のプロファイルが変更されました。

* **を実装するコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** MeaningPlaybackがタイムラインの予約に達しました。

* **を実装するコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **** MeaningSeek操作が開始されました。

* **を実装するコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

`SeekEndEventListener`

* **** 意味：シーク操作が終了しました。

* **を実装するコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** 意味：シーク位置は、内部再生ルールまたは外部のビジネスルールが原因で調整されました。

* **を実装するコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** 意味：メディアのサイズを使用できます。

* **を実装するコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** つまり、MediaPlayerの状態が変更されました。

* **を実装するコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** 意味：再生ヘッドが変更されました。

* **を実装するコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

`TimedEventEventListener`

* **** 意味操作は、操作に要した時間で完了します。

* **を実装するコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** 意味：新しい時間指定メタデータがバックグラウンドでアイテムに追加されました。

* **を実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** 意味：新しい時間指定メタデータがメディアストリームで検出されました。

* **を実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** 意味タイムラインが変更されました。広告がタイムラインに追加または削除された可能性があります。

* **を実装するコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`
