---
description: TVSDKは、広告イベントの再生時など、広告関連の操作に応じて広告再生開始をディスパッチします。
title: 広告再生イベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---


# 広告再生イベント{#ad-playback-events}

TVSDKは、広告イベントの再生時など、広告関連の操作に応じて広告再生開始をディスパッチします。

すべての広告再生関連イベントに関して通知を受けるには、以下のコールバックを含む`MediaPlayer.AdPlaybackEventListener`の実装を登録します。

>[!TIP]
>
>広告がメディアに挿入またはメディアから削除されると、TVSDKは再生イベント[onTimelineUpdated](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated())をディスパッチします。

| イベント | 意味 |
|---|---|
| [onAdBreakComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告の時間が完全に再生されました。 |
| onAdBreakSkipped | 再生中に広告の時間がスキップされました。 |
| [onAdBreakStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdBreakStart(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak) | 広告の時間が開始されました。 |
| [onAdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdClick(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad,%20com.adobe.mediacore.timeline.advertising.AdClick)) (AdBreak adBreak, Ad ad, AdClick adClick) | ユーザーが広告をクリックしました。 アプリケーションが`MediaPlayerView`で`notifyClick`を呼び出すのに応じて、ユーザーがクリックした広告に関する情報をアプリケーションに提供します。 |
| [onAdComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdComplete(com.adobe.mediacore.timeline.advertising.AdBreak)) (AdBreak adBreak, Ad ad) | 広告が完全に再生されました。 |
| [onAdProgress](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdProgress(com.adobe.mediacore.timeline.advertising.AdBreak,com.adobe.mediacore.timeline.advertising.Ad,%20int)) (AdBreak adBreak, Ad ad, int percentage) | 再生の進行中です。 広告の再生中に複数回ディスパッチされます。 |
| [onAdStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html#onAdStart(com.adobe.mediacore.timeline.advertising.AdBreak,%20com.adobe.mediacore.timeline.advertising.Ad)) (AdBreak adBreak, Ad ad) | 広告が開始されました。 |