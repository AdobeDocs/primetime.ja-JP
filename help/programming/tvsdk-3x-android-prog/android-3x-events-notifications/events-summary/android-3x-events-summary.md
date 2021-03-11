---
description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンして、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
title: Primetimeプレイヤーイベントの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---


# Primetimeプレイヤーイベントの概要{#primetime-player-events-summary}

アプリケーションは、TVSDKがディスパッチするイベントをリッスンして、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。

## イベント{#events}

TVSDKは、イベントが発生した場合に、その応答を求めるアプリケーションを通知します。 各イベントは、実装する必要があるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは`MediaPlayerEvent`列挙の定数です。

`AdBreakCompletedEventListener`

* **** つまり、広告の時間の再生が完了したということです。

* **実装するコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **** つまり、再生中に広告の時間がスキップされました。

* **実装するコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **** つまり、広告の時間の再生が開始されました。

* **実装するコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

`AdClickedEventListener`

* **** 意味：再生中に広告がクリックされた。

* **実装するコールバック** `onAdClicked(AdClickEvent event)`
* **イベントコード** `AD_CLICK`

`AdCompletedEventListener`

* **** つまり、広告の再生が完了したということです。

* **実装するコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

`AdProgressEventListener`

* **** 意味再生中の進行状況のレポート。

* **実装するコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **** 意味Primetimeの広告判定の広告の解決が完了した。このイベントは、VODコンテンツにのみ適用されます。

* **実装するコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **** つまり、広告の再生が開始されたことです。

* **実装するコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

`AudioUpdatedEventListener`

* **** 意味新しいオーディオトラックが検出されました。

* **実装するコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **** 意味プレイヤーがバッファリングを開始しました。

* **実装するコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

`BufferingEndEventListener`

* **** 意味プレイヤーがバッファリングを停止しました。

* **実装するコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

`BufferPreparedEventListener&quot;

* **** 意味バッファが準備されている。

* **実装するコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **** 意味新しいキャプショントラックが検出されました。

* **実装するコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **** 意味新しいDRMメタデータがメディアストリームで検出されました。

* **実装するコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

`ItemCreatedEventListener`

* **** 意味新しいメディアプレイヤー項目が作成されました。

* **実装するコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **** 意味現在の項目に対して新しい読み込み情報が作成されました。

* **実装するコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

`LoadInformationEventListener`

* **** 意味新しいセグメントが読み込まれました。

* **実装するコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **** 意味メインのマニフェストまたはプレイリストが更新されました。

* **実装するコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

`NotificationEventListener`

* **** 意味：操作が失敗しました。

* **実装するコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **** つまり、再生範囲が更新されました。

* **実装するコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **** つまり、新しい再生速度が画面に表示されます。

* **実装するコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **** 意味MediaPlayerのレート属性が設定されている。

* **実装するコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

`PlayStartEventListener`

* **** つまり、再生が開始されたということです。

* **実装するコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

`ProfileChangeEventListener`

* **** つまり、MediaPlayerの現在のプロファイルが変更されました。

* **実装するコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

`ReservationReachedEventListener`

* **** MeaningPlaybackがタイムラインの予約に到達しました。

* **実装するコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

`SeekBeginEventListener`

* **** MeaningSeek操作が開始されました。

* **実装するコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

`SeekEndEventListener`

* **** 意味シーク操作が終了しました。

* **実装するコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

`SeekPositionAdjustedEventListener`

* **** 意味内部再生ルールまたは外部ビジネスルールが原因で、シーク位置が調整されました。

* **実装するコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **** つまり、メディアのサイズが使用可能です。

* **実装するコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

`StatusChangeEventListener`

* **** つまり、MediaPlayerの状態が変更されました。

* **実装するコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

`TimeChangeEventListener`

* **** 意味再生ヘッドが変更されました。

* **実装するコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

`TimedEventEventListener`

* **** 意味操作は、操作に要した時間で完了します。

* **実装するコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **** 意味新しい時間指定メタデータがバックグラウンドでアイテムに追加されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **** 意味新しい時間指定メタデータがメディアストリームで検出されました。

* **実装するコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **** 意味タイムラインが変更されています。広告がタイムラインに追加されたか、タイムラインから削除された可能性があります。

* **実装するコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`