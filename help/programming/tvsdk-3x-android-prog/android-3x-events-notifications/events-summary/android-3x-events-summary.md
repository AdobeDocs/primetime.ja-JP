---
description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-title: Primetimeプレーヤーイベントの概要
title: Primetimeプレーヤーイベントの概要
uuid: b2ff74f2-c373-42da-a717-2f0550cbcb7f
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Primetimeプレーヤーイベントの概要 {#primetime-player-events-summary}

アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。

## イベント {#events}

TVSDKは、アプリケーションが応答する必要のあるイベントが発生したことを通知します。 各イベントは、実装する必要があるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは、列挙型の定数 `MediaPlayerEvent` です。

`AdBreakCompletedEventListener`

* **つまり** 、広告の時間の再生が完了したとします。

* **実装のコールバック**`onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード**`AD_BREAK_COMPLETE`

`AdBreakSkippedEventListener`

* **つまり** 、広告の時間が再生中にスキップされました。

* **実装のコールバック**`onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード**`AD_BREAK_SKIPPED`

`AdBreakStartedEventListener`

* **つまり** 、広告の時間の再生が開始されました。

* **実装のコールバック**`onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード**`AD_BREAK_START`

`AdClickedEventListener`

* **つまり** 、再生中に広告がクリックされたことを意味します。

* **実装のコールバック**`onAdClicked(AdClickEvent event)`
* **イベントコード**`AD_CLICK`

`AdCompletedEventListener`

* **つまり** 、広告の再生が完了したということです。

* **実装のコールバック**`onAdCompleted(AdPlaybackEvent event)`

* **イベントコード**`AD_COMPLETE`

`AdProgressEventListener`

* **つまり** 、再生中の進行状況のレポート。

* **実装のコールバック**`onAdProgress(AdPlaybackEvent event)`

* **イベントコード**`AD_PROGRESS`

`AdResolutionCompleteEventListener`

* **つまり** 、Primetime ad decisioningad resolutionが完了したということです。 このイベントはVODコンテンツにのみ適用されます。

* **実装のコールバック**`onAdResolutionComplete()`

* **イベントコード**`AD_RESOLUTION_COMPLETE`

`AdStartedEventListener`{#section_A4339C48F82640A8AF4AF09CB3B33188}

* **つまり** 、広告の再生が開始されたことです。

* **実装のコールバック**`onAdStarted(AdPlaybackEvent event)`

* **イベントコード**`AD_START`

`AudioUpdatedEventListener`

* **つまり** 、新しいオーディオトラックが検出されました。

* **実装のコールバック**`onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード**`AUDIO_TRACK_UPDATED`

`BufferingBeginEventListener`

* **つまり** 、プレイヤーがバッファリングを開始したということです。

* **実装のコールバック**`onBufferingBegin(BufferEvent event)`

* **イベントコード**`BUFFERING_BEGIN`

`BufferingEndEventListener`

* **つまり** 、プレーヤーがバッファリングを停止したとします。

* **実装のコールバック**`onBufferingEnd(BufferEvent event)`

* **イベントコード**`BUFFERING_END`

`BufferPreparedEventListener&quot;

* **つまり** 、バッファが準備されている。

* **実装のコールバック**`onBufferPrepared()`

* **イベントコード**`BUFFER_PREPARED`

`CaptionsUpdatedEventListener`

* **つまり** 、新しいキャプショントラックが検出されました。

* **実装のコールバック**`onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード**`CAPTIONS_UPDATED`

`DRMMetadataInfoEventListener`

* **つまり** 、新しいDRMメタデータがメディアストリームで検出されました。

* **実装のコールバック**`onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード**`DRM_METADATA`

`ItemCreatedEventListener`

* **つまり** 、新しいメディアプレイヤー項目が作成されたということです。

* **実装のコールバック**`onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード**`ITEM_CREATED`

`ItemLoadCompleteEventListener`

* **意味** ：現在の品目に対して新しい読み込み情報が作成されました。

* **実装のコールバック**`onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード**`ITEM_UPDATED`

`LoadInformationEventListener`

* **意味** ：新しいセグメントが読み込まれた。

* **実装のコールバック**`onLoadInformation(LoadInformationEvent event)`

* **イベントコード**`LOAD_INFORMATION_AVAILABLE`

`MainManifestUpdatedEventListener`

* **つまり** 、メインのマニフェストまたはプレイリストが更新されました。

* **実装のコールバック**`onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード**`MANIFEST_UPDATED`

`NotificationEventListener`

* **つまり** 、操作が失敗した。

* **実装のコールバック**`onNotification(NotificationEvent event)`

* **イベントコード**`OPERATION_FAILED`

`PlaybackRangeUpdatedEventListener`

* **つまり** 、再生範囲が更新されました。

* **実装のコールバック**`onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード**`PLAYBACK_RANGE_UPDATED`

`PlaybackRatePlayingEventListener`

* **つまり** 、新しい再生速度が画面に表示されます。

* **実装のコールバック**`onRatePlaying(PlaybackRateEvent event)`

* **イベントコード**`RATE_PLAYING`

`PlaybackRateSelectedEventListener`

* **つまり** 、MediaPlayerのレート属性が設定されていることを意味します。

* **実装のコールバック**`onRateSelected(PlaybackRateEvent event)`

* **イベントコード**`RATE_SELECTED`

`PlayStartEventListener`

* **つまり** 、再生が開始されたことです。

* **実装のコールバック**`onPlayStart()`

* **イベントコード**`PLAY_START`

`ProfileChangeEventListener`

* **つまり** 、MediaPlayerの現在のプロファイルが変更されたということです。

* **実装のコールバック**`onProfileChanged(ProfileEvent event)`

* **イベントコード**`PROFILE_CHANGED`

`ReservationReachedEventListener`

* **つまり** 、再生がタイムラインの予約に到達したということです。

* **実装のコールバック**`onReservationReached(ReservationEvent event)`

* **イベントコード**`RESERVATION_REACHED`

`SeekBeginEventListener`

* **意味シーク** 操作が開始されました。

* **実装のコールバック**`onSeekBegin(SeekEvent event)`

* **イベントコード**`SEEK_BEGIN`

`SeekEndEventListener`

* **つまり** 、シーク操作が完了したということです。

* **実装のコールバック**`onSeekEnd(SeekEvent event)`

* **イベントコード**`SEEK_END`

`SeekPositionAdjustedEventListener`

* **意味** ：シーク位置は、内部再生ルールまたは外部ビジネスルールが原因で調整されました。

* **実装のコールバック**`onPositionAdjusted(SeekEvent event)`

* **イベントコード**`SEEK_POSITION_ADJUSTED`

`SizeAvailableEventListener`

* **つまり** 、メディアのサイズが使用可能です。

* **実装のコールバック**`onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード**`SIZE_AVAILABLE`

`StatusChangeEventListener`

* **つまり** 、MediaPlayerの状態が変更されたということです。

* **実装のコールバック**`onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード**`STATUS_CHANGED`

`TimeChangeEventListener`

* **つまり** 、再生ヘッドが変更されました。

* **実装のコールバック**`onTimeChanged(TimeChangeEvent event)`

* **イベントコード**`TIME_CHANGED`

`TimedEventEventListener`

* **つまり** 、操作は、操作に要した時間で完了します。

* **実装のコールバック**`onTimedEvent(TimedEventEvent event)`

* **イベントコード**`TIMED_EVENT`

`TimelineMetadataAddedInBackgroundEventListener`

* **つまり** 、新しい時間指定メタデータがバックグラウンドのアイテムに追加されました。

* **実装のコールバック**`onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード**`TIMED_METADATA_ADDED_IN_BACKGROUND`

`TimedMetadataEventListener`

* **つまり** 、新しい時間指定メタデータがメディアストリームで検出されました。

* **実装のコールバック**`onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード**`TIMED_METADATA_AVAILABLE`

`TimelineUpdatedEventListener`

* **つまり** 、タイムラインが変更されたということです。 広告がタイムラインに追加されたり、タイムラインから削除されたりした可能性があります。

* **実装のコールバック**`onTimelineUpdated(TimelineEvent event)`

* **イベントコード**`TIMELINE_UPDATED`