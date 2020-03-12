---
description: TVSDKには、有効なレート、現在のレート、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を判断するためのメソッド、プロパティ、イベントが含まれています。
seo-description: TVSDKには、有効なレート、現在のレート、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を判断するためのメソッド、プロパティ、イベントが含まれています。
seo-title: レート変更API要素
title: レート変更API要素
uuid: 0040d35c-f9cb-4066-9bee-828ed5541194
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# レート変更API要素{#rate-change-api-elements}

TVSDKには、有効なレート、現在のレート、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を判断するためのメソッド、プロパティ、イベントが含まれています。

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

次のAPIエレメントを使用して、再生率を変更します。

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates`  — 有効なレートを指定します。

| レート値 | 再生への影響 |
|---|---|
| 2.0, 4.0, 8.0, 16.0, 32.0, 64.0, 128.0 | 指定した乗数が通常よりも速い早送りモードに切り替えます（例えば、4は通常よりも4倍速い）。 |
| -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 , -128.0 | 早戻しモードに切り替えます。 |
| 1.0 | 通常再生モードに切り替えます( `play` 呼び出しは、rateプロパティを1.0に設定するのと同じです)。 |
| 0.0 | 一時停止(呼び出 `pause` しは、rateプロパティを0.0に設定するのと同じ) |

