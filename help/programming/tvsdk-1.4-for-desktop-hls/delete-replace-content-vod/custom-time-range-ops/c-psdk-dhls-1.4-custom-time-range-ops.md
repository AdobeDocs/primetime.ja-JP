---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。
seo-description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。
seo-title: カスタム時間範囲操作
title: カスタム時間範囲操作
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 概要{#custom-time-range-operations-overview}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張するものです。 カスタム広告マーカーは、メインコンテンツの一部を広告関連コンテンツ期間としてマークします。 これらの時間範囲をマークするだけでなく、時間範囲を削除したり置き換えたりすることもできます。

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

広告削除および置換は、VODストリームの様々なタイプの時間範囲を識別するカスタムマーカーを使用して実装されます。マーク、削除、置換を行います。 カスタム時間範囲ごとに、広告コンテンツの削除や置換など、関連する操作を実行できます。

広告削除および置換の場合、TVSDKには、次の&#x200B;*カスタム時間範囲操作*&#x200B;モードが含まれます。

* MARK — マークされた領域に対して`AdBreak`イベントをディスパッチします。 （以前のバージョンのTVSDKでは`customAdMarker`と呼ばれていました）。 このモードでは広告挿入は許可されません。

* DELETE — このモードでは、アプリは`TimeRangeCollection`クラスを使用してC3広告削除の時間範囲を定義します。 このモードでは広告挿入が許可されます。
* REPLACE — このモードでは、アプリは`timeRange`をAdobe Primetimead decisioning `AdBreak`で置き換えます。 C3広告削除が発生し、指定された時間（元の時間範囲より短いまたは長い）に終了する置換操作開始。

TVSDKは、MARKとDELETE範囲の配置オポチュニティを生成するための`CustomRangesOpportunityGenerator`クラスを提供します。 REPLACEモードの場合、TVSDKは、時間範囲ごとに2つの配置オポチュニティを生成します。

* `CustomRangeResolver`は、DELETEのための配置オポチュニティを生成します
* `AuditudeAdResolver`は、INSERT用の配置オポチュニティを生成します。