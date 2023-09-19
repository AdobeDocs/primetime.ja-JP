---
description: TVSDK は、広告の再生が開始したときなど、広告関連の操作に応じて広告再生イベントをディスパッチします。
title: 広告再生イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 広告再生イベント{#ad-playback-events}

TVSDK は、広告の再生が開始したときなど、広告関連の操作に応じて広告再生イベントをディスパッチします。

すべての広告再生関連イベントに関する通知を受け取るには、 `MediaPlayer.AdPlaybackEventListener` 次のコールバックを含めます。

>[!TIP]
>
>広告がメディアに挿入またはメディアから削除されると、 TVSDK は再生イベントをディスパッチします [onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated()).

| イベント | 意味 |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告ブレークが完全に再生されました。 |
| onAdBreakSkipped | 再生中に広告の時間がスキップされました。 |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告ブレークが開始しました。 |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Ad ad, AdClick adClick) | ユーザーが広告をクリックした。 アプリケーションが呼び出す応答でユーザーがクリックした広告に関する情報をアプリケーションに提供します `notifyClick` の `MediaPlayerView`. |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, Ad ad ad) | 広告が完全に再生されました。 |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad ad, int percentage) | 広告の再生が進行しました。 広告の再生中に複数回ディスパッチされます。 |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, Ad ad ad) | 広告が開始されました。 |
