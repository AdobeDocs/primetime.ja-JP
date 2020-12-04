---
description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンして、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンして、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。
seo-title: Primetimeプレイヤーイベントの概要
title: Primetimeプレイヤーイベントの概要
uuid: ed3be4c2-8df3-4d96-a30b-74c196262798
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Primetimeプレイヤーイベントの概要{#primetime-player-events-summary-overview}

アプリケーションは、TVSDKがディスパッチするイベントをリッスンして、プレイヤーのアクティビティおよびプレイヤーのステータスの変化を監視できます。

## イベント{#events}

TVSDKは、イベントが発生した場合に、その応答を求めるアプリケーションを通知します。 各イベントは、実装する必要があるコールバックメソッドを持つリスナークラスに対応します。

>[!TIP]
>
>イベントコードは`MediaPlayerEvent`列挙の定数です。

## AdBreakCompletedEventListener {#section_D7A74A4EACA44E54806D040491B7D879}

* ** **広告の時間の再生が完了したことを意味します。

* **実装のコールバック** `onAdBreakCompleted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_COMPLETE`

## AdBreakSkippedEventListener {#section_7AE5442442484F45B521D3309691C59C}

* ** **再生中に広告の時間がスキップされたことを意味します。

* **実装のコールバック** `onAdBreakSkipped(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_SKIPPED`

## AdBreakStartedEventListener {#section_0D50327621164E3A9C8F3337AA20BDE7}

* **意味**広告の時間の再生が開始されました。

* **実装のコールバック** `onAdBreakStarted(AdBreakPlaybackEvent event)`

* **イベントコード** `AD_BREAK_START`

## AdClickedEventListener {#section_9A6FD39EEDE0460B94FD074B5C2FB9BE}

* **意味**再生中に広告がクリックされた。

* **実装のコールバック** `onAdClicked(AdClickEvent event)`

* **イベントコード** `AD_CLICK`

## AdCompletedEventListener {#section_D45EA0B1825145259EAC50A3E6B24BFC}

* ** **広告の再生が完了したことを意味します。

* **実装のコールバック** `onAdCompleted(AdPlaybackEvent event)`

* **イベントコード** `AD_COMPLETE`

## AdProgressEventListener {#section_C26ACC4B941942B0A24DB06585EF52AB}

* **再生中の**レポートの進行状況を意味します。

* **実装のコールバック** `onAdProgress(AdPlaybackEvent event)`

* **イベントコード** `AD_PROGRESS`

## AdResolutionCompleteEventListener {#section_E9D545408CBA448EA2A8606DA629FB0B}

* ** ** Primetime ad decisioningad resolution is complete. このイベントは、VODコンテンツにのみ適用されます。

* **実装のコールバック** `onAdResolutionComplete()`

* **イベントコード** `AD_RESOLUTION_COMPLETE`

## AdStartedEventListener {#section_A4339C48F82640A8AF4AF09CB3B33188}

* ** **広告の再生が開始されたことを意味します。

* **実装のコールバック** `onAdStarted(AdPlaybackEvent event)`

* **イベントコード** `AD_START`

## AudioUpdatedEventListener {#section_06E1A9F683E1411081CFC6BD30C3B669}

* **意味**新しいオーディオトラックが検出されました。

* **実装のコールバック** `onAudioUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `AUDIO_TRACK_UPDATED`

## BufferingBeginEventListener {#section_F8378841149A4801867ADDC7C0A98C57}

* **意味**プレイヤーがバッファリングを開始しました。

* **実装のコールバック** `onBufferingBegin(BufferEvent event)`

* **イベントコード** `BUFFERING_BEGIN`

## BufferingEndEventListener {#section_9107E0ED59474F11A04E243C6B117E21}

* **意味**プレイヤーがバッファリングを停止しました。

* **実装のコールバック** `onBufferingEnd(BufferEvent event)`

* **イベントコード** `BUFFERING_END`

## BufferPreparedEventListener {#section_F6BFDF525D8B41B7B6E0EFCCE3065811}

* ** **バッファが準備されていることを意味します。

* **実装のコールバック** `onBufferPrepared()`

* **イベントコード** `BUFFER_PREPARED`

## CaptionsUpdatedEventListener {#section_048BB128ADB747519F02DEDDD1C88B86}

* **意味**新しいキャプショントラックが検出されました。

* **実装のコールバック** `onCaptionsUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `CAPTIONS_UPDATED`

## DRMMetadataInfoEventListener {#section_CB55064D305A40D5BBAD09A53D63DB95}

* **意味**新しいDRMメタデータがメディアストリームで検出されました。

* **実装のコールバック** `onDRMMetadataInfo(DRMMetadataInfoEvent event)`

* **イベントコード** `DRM_METADATA`

## ItemCreatedEventListener {#section_32A3178664C841008370E8447C978AB2}

* **意味**新しいメディアプレイヤー項目が作成されました。

* **実装のコールバック** `onItemCreated(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_CREATED`

## ItemLoadCompleteEventListener {#section_E29A3D7D2666461599909BD8E8BA46A7}

* **意味**現在のアイテムに対して新しい読み込み情報が作成されています。

* **実装のコールバック** `onLoadComplete(MediaPlayerItemEvent event)`

* **イベントコード** `ITEM_UPDATED`

## LoadInformationEventListener {#section_A986AD83F68446B99EAC888F98B39148}

* **意味**新しいセグメントが読み込まれました。

* **実装のコールバック** `onLoadInformation(LoadInformationEvent event)`

* **イベントコード** `LOAD_INFORMATION_AVAILABLE`

## MainManifestUpdatedEventListener {#section_73709D121CED48C1B38550135DA55548}

* **意味**メインのマニフェストまたはプレイリストが更新されました。

* **実装のコールバック** `onMainManifestUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `MANIFEST_UPDATED`

## NotificationEventListener {#section_E8F27B979D374B5D8EA184E23BC17E43}

* **意味**操作が失敗しました。

* **実装のコールバック** `onNotification(NotificationEvent event)`

* **イベントコード** `OPERATION_FAILED`

## PlaybackRangeUpdatedEventListener {#section_9072862D7EB842AEA3094DAF911CDF7F}

* ** **再生範囲が更新されたことを意味します。

* **実装のコールバック** `onPlaybackRangeUpdated(MediaPlayerItemEvent event)`

* **イベントコード** `PLAYBACK_RANGE_UPDATED`

## PlaybackRatePlayingEventListener {#section_548A489ABED44F89BDF29DB9EDD348C5}

* **意味**新しい再生速度が画面に表示されます。

* **実装のコールバック** `onRatePlaying(PlaybackRateEvent event)`

* **イベントコード** `RATE_PLAYING`

## PlaybackRateSelectedEventListener {#section_B303BAAFA6D14C1599AD3D7D79D722DD}

* **意味** MediaPlayerのレート属性が設定されています。

* **実装のコールバック** `onRateSelected(PlaybackRateEvent event)`

* **イベントコード** `RATE_SELECTED`

## PlayStartEventListener {#section_1D54CAE387B243679348A26E65B6A3FD}

* **意味**再生が開始された。

* **実装のコールバック** `onPlayStart()`

* **イベントコード** `PLAY_START`

## ProfileChangeEventListener {#section_EEDF08916D1D40509E64EC180F143C9A}

* **意味** MediaPlayerの現在のプロファイルが変更されました。

* **実装のコールバック** `onProfileChanged(ProfileEvent event)`

* **イベントコード** `PROFILE_CHANGED`

## ReservationReachedEventListener {#section_31677E931F154E7E86D725B2B046065C}

* ** **再生がタイムラインの予約に到達したことを意味します。

* **実装のコールバック** `onReservationReached(ReservationEvent event)`

* **イベントコード** `RESERVATION_REACHED`

## SeekBeginEventListener {#section_749E02ED2B1647438F50224C85260A1D}

* ** **シーク操作が開始されたことを意味します。

* **実装のコールバック** `onSeekBegin(SeekEvent event)`

* **イベントコード** `SEEK_BEGIN`

## SeekEndEventListener {#section_4F70BAD695AF4717B2254D9DBA1071E4}

* ** **シーク操作が終了したことを意味します。

* **実装のコールバック** `onSeekEnd(SeekEvent event)`

* **イベントコード** `SEEK_END`

## SeekPositionAdjustedEventListener {#section_01F89B73DBB84BEBBA60D820BF5FAC9A}

* **意味**内部再生ルールまたは外部ビジネスルールが原因で、シーク位置が調整されました。

* **実装のコールバック** `onPositionAdjusted(SeekEvent event)`

* **イベントコード** `SEEK_POSITION_ADJUSTED`

## SizeAvailableEventListener {#section_90DF6565E59B44B19338A7B89D53BBBF}

* **意味**メディアのサイズが使用可能です。

* **実装のコールバック** `onSizeAvailable(SizeAvailableEvent event)`

* **イベントコード** `SIZE_AVAILABLE`

## StatusChangeEventListener {#section_310D2327089D46358F9CE03EA76F3287}

* **意味** MediaPlayerの状態が変更されました。

* **実装のコールバック** `onStatusChanged(MediaPlayerStatusChangeEvent event)`

* **イベントコード** `STATUS_CHANGED`

## TimeChangeEventListener {#section_ED3855BD90124D97836B2D0957AD9E0C}

* **意味**再生ヘッドが変更されました。

* **実装のコールバック** `onTimeChanged(TimeChangeEvent event)`

* **イベントコード** `TIME_CHANGED`

## TimedEventEventListener {#section_5E62C2C81C3B4F93B46E7518578456EA}

* ** **操作は、操作に要した時間と共に完了します。

* **実装のコールバック** `onTimedEvent(TimedEventEvent event)`

* **イベントコード** `TIMED_EVENT`

## TimelineMetadataAddedInBackgroundEventListener {#section_7B923C7116154CCFBAE1FCA92C928EB2}

* **意味**新しい時間指定メタデータがバックグラウンドでアイテムに追加されました。

* **実装のコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_ADDED_IN_BACKGROUND`

## TimedMetadataEventListener {#section_9741EA321ACF403FB8E9AB311BAACDD7}

* **意味**新しい時間指定メタデータがメディアストリームで検出されました。

* **実装のコールバック** `onTimedMetadata(TimedMetadataEvent event)`

* **イベントコード** `TIMED_METADATA_AVAILABLE`

## TimelineUpdatedEventListener {#section_D0755BD2AF3347C7861395706E31B861}

* **意味**タイムラインが変更されています。 広告がタイムラインに追加されたか、タイムラインから削除された可能性があります。

* **実装のコールバック** `onTimelineUpdated(TimelineEvent event)`

* **イベントコード** `TIMELINE_UPDATED`