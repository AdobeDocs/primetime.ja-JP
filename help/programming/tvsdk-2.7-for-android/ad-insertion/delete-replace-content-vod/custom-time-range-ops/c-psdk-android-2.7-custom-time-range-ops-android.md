---
description: CustomRangeMetadata クラスは、VOD ストリームマーク、削除および置換内の様々なタイプの時間範囲を識別します。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置き換えなど、対応する操作を実行できます。
title: カスタム時間範囲操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 概要 {#custom-time-range-operations}

CustomRangeMetadata クラスは、VOD ストリーム内の様々なタイプの時間範囲 (mark、delete、replace) を識別します。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置き換えなど、対応する操作を実行できます。

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

広告の削除と置き換えに、 TVSDK は以下を使用します。 *カスタム時間範囲操作* モード：

* **トンボ** このモードは、以前のバージョンの TVSDK ではカスタム広告マーカーと呼ばれていました。 このモードは、既に VOD ストリームに配置されている広告の開始時間と終了時間をマークします。 タイプの時間範囲マーカーがある場合 `MARK` ストリーム内で、 `Mode.MARK` が次で生成された： `CustomMarkerOpportunityGenerator` およびによって解決された `CustomRangeResolver`. 広告は挿入されません。

* **DELETE** の場合 `DELETE` 時間範囲、初期 `placementInformation` のタイプ `Mode.DELETE` が次の方法で作成および解決された `CustomRangeResolver`. `DeleteRangeTimelineOperation` は、タイムラインから削除する範囲を定義します。 TVSDK は `removeByLocalTime` Adobeビデオエンジン (AVE)API からこの操作を完了します。 DELETE範囲とAdobe Primetime Ad Decisioning メタデータがある場合、その範囲が最初に削除され、 `AuditudeResolver` 一般的なAdobe Primetime ad decisioning ワークフローを使用して広告を解決します。

* **置換** の場合 `REPLACE` 時間範囲、2 つの初期値 `placementInformations` 作成済み、1 つ `Mode.DELETE` 一つ `Mode.REPLACE`. `CustomRangeResolver` 最初に時間範囲を削除し、次に `AuditudeResolver` 指定した `replaceDuration` をタイムラインに追加します。 いいえの場合 `replaceDuration` を指定した場合、サーバーは何を挿入するかを決定します。

これらのカスタム時間範囲操作をサポートするために、 TVSDK は以下を提供します。

* 複数のコンテンツリゾルバー

  ストリームは、広告シグナリングモードおよび広告メタデータに基づいて、複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変わります。
* 次を使用して複数の初期商談 `CustomMarkerOpportunityGenerator`.
* 新しい広告シグナリングモード `CUSTOM_RANGES`.

  広告は、JSON ファイルなどの外部ソースの時間範囲データに基づいて配置されます。
