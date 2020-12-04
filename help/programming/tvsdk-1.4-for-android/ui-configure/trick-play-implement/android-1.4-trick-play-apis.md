---
description: TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関するその他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。
seo-description: TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関するその他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。
seo-title: レート変更APIエレメント
title: レート変更APIエレメント
uuid: 0040d35c-f9cb-4066-9bee-828ed5541194
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 2%

---


# レート変更APIエレメント{#rate-change-api-elements}

TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関するその他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。

<!--<a id="section_36576E92DE6343AEBD0BBD662502365D"></a>-->

再生率を変更するには、次のAPIエレメントを使用します。

* `PlaybackRateEvent.getRate`
* `MediaPlayer.getLocalTime`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerEvent.AD_BREAK_SKIPPED`
* `MediaPlayerItem.getAvailablePlaybackRates`  — 有効な料金を指定します。

| レート値 | 再生への影響 |
|---|---|
| 2.0、4.0、8.0、16.0、32.0、64.0、128.0 | 指定した倍速の早送りモードに切り替えます（例えば、4は4倍速です）。 |
| -2.0、-4.0、-8.0、-16.0、-32.0、-64.0、-128.0 | 早戻しモードに切り替えます。 |
| 1.0 | 通常再生モードに切り替えます（`play`を呼び出すのと、rateプロパティを1.0に設定するのは同じことです）。 |
| 0.0 | 一時停止します（`pause`を呼び出すのと、レートプロパティを0.0に設定するのは同じことです）。 |

