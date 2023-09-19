---
description: TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。
title: カスタム時間範囲操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 概要 {#custom-time-range-operations-overview}

TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除して置き換えることもできます。

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

広告の削除と置換は、VOD ストリーム内の様々なタイプの時間範囲（マーク、削除および置換）を識別するカスタムマーカーを使用して実装されます。 カスタム時間範囲ごとに、広告コンテンツの削除や置き換えなど、関連する操作を実行できます。

広告の削除と置き換えの場合、 TVSDK には次の機能が含まれます。 *カスタム時間範囲操作* モード：

* MARK — ディスパッチ `AdBreak` イベントを設定します。 ( これは、 `customAdMarker` （以前のバージョンの TVSDK）。 このモードでは広告の挿入は許可されていません。

* DELETE — このモードでは、アプリは `TimeRangeCollection` C3 広告削除の時間領域を定義するクラス。 このモードでは、広告の挿入が許可されます。
* REPLACE — このモードでは、アプリは `timeRange` Adobe Primetime ad decisioning を使用 `AdBreak`. 置換操作は、C3 広告削除の発生時に開始し、指定された時間（元の時間範囲より短い、または長い）に終了します。

TVSDK は、 `CustomRangesOpportunityGenerator` クラスを使用して、MARK およびDELETE範囲の配置オポチュニティを生成します。 REPLACE モードの場合、 TVSDK は、各時間範囲に対して 2 つの配置オポチュニティを生成します。

* The `CustomRangeResolver` DELETEの配置機会を生成します
* The `AuditudeAdResolver` は、INSERT 用の配置オポチュニティを生成します。
