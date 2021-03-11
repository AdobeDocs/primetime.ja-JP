---
description: TVSDKは、広告イベントの再生時など、広告関連の操作に応じて広告再生開始をディスパッチします。
title: 広告再生イベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# 広告再生イベント{#ad-playback-events}

TVSDKは、広告イベントの再生時など、広告関連の操作に応じて広告再生開始をディスパッチします。

すべての広告再生関連イベントに関して通知を受けるには、以下のイベントの`MediaPlayer`オブジェクトにリスナーを登録します。

>[!TIP]
>
>広告がメディアに挿入されたりメディアから削除されたりすると、TVSDKは再生イベントTimelineEventをディスパッチします。[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| イベント | 意味 |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | 広告の時間が完全に再生されました。 |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | 再生中に広告の時間がスキップされました。 |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | 広告の時間が開始されました。 |
| AdClickEvent.[AD _CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | ユーザーが広告をクリックしました。 アプリケーションが`MediaPlayerView`で`notifyClick`を呼び出すのに応じて、ユーザーがクリックした広告に関する情報をアプリケーションに提供します。 |
| AdPlaybackEvent.[AD _COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | 広告が完全に再生されました。 |
| AdPlaybackEvent.[AD _PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | 再生の進行中です。 広告の再生中に複数回ディスパッチされます。 |
| AdPlaybackEvent.[AD _SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告の境界を越えて、または広告内でシークが発生しました。 |
| AdPlaybackEvent.[AD _STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告が開始されました。 |