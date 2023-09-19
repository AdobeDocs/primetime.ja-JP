---
description: TVSDK は、広告の再生が開始したときなど、広告関連の操作に応じて広告再生イベントをディスパッチします。
title: 広告再生イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 広告再生イベント {#ad-playback-events}

TVSDK は、広告の再生が開始したときなど、広告関連の操作に応じて広告再生イベントをディスパッチします。

すべての広告再生関連イベントに関して通知を受け取るには、 `MediaPlayer` オブジェクトを次のイベントに設定します。

>[!TIP]
>
>広告がメディアに挿入またはメディアから削除されると、 TVSDK は再生イベント TimelineEvent をディスパッチします。[TIMELINE_UPDATED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED).

| イベント | 意味 |
|---|---|
| AdBreakPlaybackEvent.[AD_BREAK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_COMPLETED) | 広告ブレークが完全に再生されました。 |
| AdBreakPlaybackEvent.[AD_BREAK_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_SKIPPED) | 再生中に広告の時間がスキップされました。 |
| AdBreakPlaybackEvent.[AD_BREAK_STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html#AD_BREAK_STARTED) | 広告ブレークが開始しました。 |
| AdClickEvent.[AD _CLICK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html#AD_CLICK) | ユーザーが広告をクリックした。 アプリケーションが呼び出す応答でユーザーがクリックした広告に関する情報をアプリケーションに提供します `notifyClick` の `MediaPlayerView`. |
| AdPlaybackEvent.[AD _COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_COMPLETED) | 広告が完全に再生されました。 |
| AdPlaybackEvent.[AD _PROGRESS](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_PROGRESS) | 広告の再生が進行しました。 広告の再生中に複数回ディスパッチされます。 |
| AdPlaybackEvent.[AD _SEEK](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告の境界をまたいで、または広告内で、シークが発生しました。 |
| AdPlaybackEvent.[AD _STARTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html#AD_STARTED) | 広告が開始されました。 |
