---
description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-title: Primetimeプレーヤーイベントの概要
title: Primetimeプレーヤーイベントの概要
uuid: ed3be4c2-8df3-4d96-a30b-74c196262798
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Primetimeプレーヤーイベントの概要 {#primetime-player-events-summary-overview}

アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。

## イベント {#events}

TVSDKは、アプリケーションが応答する必要のあるイベントが発生したことを通知します。 各イベントは、実装する必要があるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは、列挙型の定数 `MediaPlayerEvent` です。

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** **広告の時間の再生が完了したことを意味します。

* **実装するためのコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** **再生中に広告の時間がスキップされたことを意味します。

* **実装するためのコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* ** **広告の時間の再生が開始されたことを意味します。

* **実装するためのコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* ** **再生中に広告がクリックされたことを意味します。

* **実装するためのコールバック** `onAdClicked(AdClickEvent event)`

* **イベントコード** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** **広告の再生が完了したことを意味します。

* **実装するためのコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* ** **再生中の進行状況のレポートを意味します。

* **実装するためのコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** ** Primetime ad decisioningad resolution is complete. このイベントはVODコンテンツにのみ適用されます。

* **実装するためのコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** **広告の再生が開始されたことを意味します。

* **実装するためのコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* ** **新しいオーディオトラックが検出されました。

* **実装するためのコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* ** **プレーヤーがバッファリングを開始したことを意味します。

* **実装するためのコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* ** **プレーヤーはバッファリングを停止しました。

* **実装するためのコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* *** **バッファが準備されていることを意味します。

* **実装するためのコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* **意味**新しいキャプショントラックが検出されました。

* **実装するためのコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* ** **メディアストリームで新しいDRMメタデータが検出されました。

* **実装するためのコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* ** **新しいメディアプレイヤー項目が作成されたことを意味します。

* **実装するためのコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* ** **現在の項目に対して新しい読み込み情報が作成されました。

* **実装するためのコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* ** **新しいセグメントが読み込まれました。

* **実装するためのコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* ** **メインのマニフェストまたはプレイリストが更新されました。

* **実装するためのコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* ** **操作が失敗したことを意味します。

* **実装するためのコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** **再生範囲が更新されたことを意味します。

* **実装するためのコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* ** **新しい再生レートが画面に表示されます。

* **実装するためのコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* ** ** MediaPlayerのレート属性が設定されていることを意味します。

* **実装するためのコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* ** **再生が開始されたことを意味します。

* **実装するためのコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* ** ** MediaPlayerの現在のプロファイルが変更されたことを意味します。

* **実装するためのコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** **再生がタイムラインの予約に達したことを意味します。

* **実装するためのコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** **シーク操作が開始されました。

* **実装するためのコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** **シーク操作が終了したことを意味します。

* **実装するためのコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* ** **内部再生ルールまたは外部ビジネスルールが原因で、シーク位置が調整されました。

* **実装するためのコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* ** **メディアのサイズが使用可能です。

* **実装するためのコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* ** ** MediaPlayerの状態が変更されたことを意味します。

* **実装するためのコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* ** **再生ヘッドが変更されたことを意味します。

* **実装するためのコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** **操作は、操作にかかった時間で完了します。

* **実装するためのコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* ** **新しい時間指定メタデータがバックグラウンドのアイテムに追加されました。

* **実装するためのコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* *** **新しい時間指定メタデータがメディアストリームで検出されました。

* **実装するためのコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* ** **タイムラインが変更されたことを意味します。 広告がタイムラインに追加されたり、タイムラインから削除されたりした可能性があります。

* **実装するためのコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`