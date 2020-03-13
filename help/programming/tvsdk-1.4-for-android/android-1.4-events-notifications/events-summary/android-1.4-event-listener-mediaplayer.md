---
description: TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。
seo-description: TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。
seo-title: 広告再生イベント
title: 広告再生イベント
uuid: dd6991ae-3e33-4d92-92e9-26b1086a555a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告再生イベント{#ad-playback-events}

TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。

すべての広告再生関連イベントに関する通知を受け取るには、以下のコールバックを含む `MediaPlayer.AdPlaybackEventListener` 実装を登録します。

>[!TIP]
>
>広告がメディアに挿入されたり、メディアから削除されたりすると、TVSDKは再生イベントをonTimelineUpdated [にディスパッチします](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated())。

| イベント | 意味 |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告の時間が完全に再生されました。 |
| onAdBreakSkipped | 再生中に広告の時間がスキップされました。 |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告の時間が開始されました。 |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Ad ad ad, AdClick adClick) | ユーザーが広告をクリックしました。 アプリケーションからの呼び出しに応じて、ユーザーがクリックした広告に関する情報をアプリケーション `notifyClick` に提供しま `MediaPlayerView`す。 |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, Ad ad ad) | 広告が完全に再生されました。 |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad ad, int percentage) | 広告の再生が進行しました。 広告の再生中に複数回ディスパッチされます。 |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, Ad ad ad) | 広告が開始されました。 |