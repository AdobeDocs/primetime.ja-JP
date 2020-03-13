---
description: TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。
seo-description: TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。
seo-title: 広告再生イベント
title: 広告再生イベント
uuid: 63138237-2315-45ff-914d-369da18fdff7
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 広告再生イベント {#ad-playback-events}

TVSDKは、広告の再生開始時など、広告関連の操作に応じて、広告再生イベントをディスパッチします。

すべての広告再生関連イベントに関する通知を受け取るには、以下のイベントのリスナーをオ `MediaPlayer` ブジェクトに登録します。

>[!TIP]
>
>広告がメディアに挿入されたり、メディアから削除されたりすると、TVSDKは再生イベントTimelineEventをディスパッチします。[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED)。

| イベント | 意味 |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | 広告の時間が完全に再生されました。 |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | 再生中に広告の時間がスキップされました。 |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | 広告の時間が開始されました。 |
| AdClickEvent.[AD _CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | ユーザーが広告をクリックしました。 アプリケーションからの呼び出しに応じて、ユーザーがクリックした広告に関する情報をアプリケーション `notifyClick` に提供しま `MediaPlayerView`す。 |
| AdPlaybackEvent.[AD _COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | 広告が完全に再生されました。 |
| AdPlaybackEvent.[AD _PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | 広告の再生が進行しました。 広告の再生中に複数回ディスパッチされます。 |
| AdPlaybackEvent.[AD _SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告の境界を越えて、または広告内でシークが発生しました。 |
| AdPlaybackEvent.[広告開始(_S)](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告が開始されました。 |