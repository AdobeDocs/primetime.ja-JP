---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-title: カスタム時間範囲操作
title: カスタム時間範囲操作
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 概要 {#custom-time-range-operations-overview}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除および置き換えることもできます。

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

広告削除および置換は、VODストリームの様々なタイプの時間範囲を識別するカスタムマーカーを使用して実装されます。マーク、削除、置換を行います。 各カスタム時間範囲に対して、広告コンテンツの削除や置換など、関連する操作を実行できます。

広告の削除および置換の場合、TVSDKには次のカスタム時間範囲 *操作モードが含まれ* ます。

* MARK — マークされた領 `AdBreak` 域のイベントをディスパッチします。 (以前のバージョンのTVSDK `customAdMarker` で呼び出されていました)。このモードでは、広告の挿入は許可されません。

* DELETE — このモードでは、アプリはクラスを使用し `TimeRangeCollection` て、C3広告削除の時間領域を定義します。 このモードでは、広告の挿入が許可されます。
* 置換 — このモードでは、アプリはAdobe Primetime Ad Decisioning `timeRange` に置き換えられます `AdBreak`。 置換操作は、C3広告削除が発生した時点で開始され、指定された時間（元の時間範囲より短いまたは長い）に終了します。

TVSDKは、MARK範囲とDELETE `CustomRangesOpportunityGenerator` 範囲の配置オポチュニティを生成するクラスを提供します。 REPLACEモードの場合、TVSDKは、時間範囲ごとに2つの配置オポチュニティを生成します。

* DELETEの配 `CustomRangeResolver` 置オポチュニティを生成します
* は、INSERTの `AuditudeAdResolver` 配置オポチュニティを生成します。