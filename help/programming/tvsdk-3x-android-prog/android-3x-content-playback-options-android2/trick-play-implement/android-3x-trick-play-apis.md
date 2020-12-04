---
description: TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連する他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。
seo-description: TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連する他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。
seo-title: レート変更APIエレメント
title: レート変更APIエレメント
uuid: c2bcd20c-0641-4d75-802c-08098786d572
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 2%

---


# レート変更API要素{#rate-change-api-elements}

TVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連する他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。

<!--<a id="section_E5D37C71323947E2AED8B866D9835E31"></a>-->

再生率を変更するには、次のAPIエレメントを使用します。

* `PlaybackRateEvent.getRate`
* `MediaPlayerEvent.RATE_SELECTED`
* `MediaPlayerEvent.RATE_PLAYING`
* `MediaPlayerItem.isTrickPlaySupported`
* `MediaPlayerItem.getAvailablePlaybackRates`を指定します。

| **レート値** | **再生への影響** |
|---|---|
| 2.0、4.0、8.0、16.0、32.0、64.0、128.0 | 指定した倍速の早送りモードに切り替えます（例えば、4は4倍速です）。 |
| -2.0、-4.0、-8.0、-16.0、-32.0、-64.0、-128.0 | 早戻しモードに切り替えます。 |
| 1.0 | 通常再生モードに切り替えます（`play`を呼び出すのと、rateプロパティを1.0に設定するのは同じことです）。 |
| 0.0 | 一時停止します（`pause`を呼び出すのと、レートプロパティを0.0に設定するのは同じことです）。 |