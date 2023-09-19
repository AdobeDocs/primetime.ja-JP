---
description: TVSDK には、有効な率、現在の率、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を決定するメソッド、プロパティ、イベントが含まれています。
title: レート変更 API 要素
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%

---

# レート変更 API 要素{#rate-change-api-elements}

TVSDK には、有効な率、現在の率、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を決定するメソッド、プロパティ、イベントが含まれています。

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

再生率を変更するには、次の API 要素を使用します。

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates`  — 有効なレートを指定します。

| レート値 | 再生時の効果 |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | 指定した乗数が通常よりも速い早送りモードに切り替えます（たとえば、4 は通常より 4 倍も速い）。 |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | 早戻しモードに切り替えます。 |
| 1.0 | 通常の再生モードに切り替えます ( `play` は、 rate プロパティを 1.0 に設定するのと同じです )。 |
| 0.0 | 一時停止（呼び出し） `pause` は、 rate プロパティを 0.0 に設定する場合と同じです )。 |
