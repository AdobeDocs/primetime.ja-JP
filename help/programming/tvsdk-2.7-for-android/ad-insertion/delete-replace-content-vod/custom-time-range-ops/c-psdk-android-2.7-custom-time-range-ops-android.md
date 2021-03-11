---
description: CustomRangeMetadataクラスは、VODストリームマーク、削除および置換の様々なタイプの時間範囲を識別します。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。
title: カスタム時間範囲操作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# 概要{#custom-time-range-operations}

CustomRangeMetadataクラスは、VODストリームの様々なタイプの時間範囲を識別します。マーク、削除、置換を行います。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

広告削除および置換の場合、TVSDKは次の&#x200B;*カスタム時間範囲操作*&#x200B;モードを使用します。

* **MARKTこの** モードは、以前のバージョンのTVSDKではカスタム広告マーカーと呼ばれていました。このモードは、既にVODストリームに配置されている広告の開始時間と終了時間をマークします。 ストリーム内にタイプ`MARK`の時間範囲マーカーがある場合、`CustomMarkerOpportunityGenerator`によって`Mode.MARK`の初期配置が生成され、`CustomRangeResolver`によって解決されます。 広告は挿入されません。

* **** DELETEFまたは `DELETE` 時間範囲の場合、タイプ `placementInformation` の初期値 `Mode.DELETE` が作成され、によって解決され `CustomRangeResolver`ます。`DeleteRangeTimelineOperation` は、タイムラインから削除する範囲を定義します。TVSDKは、Adobeビデオエンジン(AVE)API `removeByLocalTime` からこの操作を実行します。DELETE範囲とAdobe Primetimead decisioningメタデータがある場合、その範囲が最初に削除され、次に`AuditudeResolver`が一般的なAdobe Primetimead decisioningワークフローを使用して広告を解決します。

* **** REPLACEFまたは `REPLACE` 時間範囲を指定すると、2つの初期値(1 `placementInformations` つと1つ) `Mode.DELETE` が作成され `Mode.REPLACE`ます。`CustomRangeResolver` 最初に時間範囲を削除し、次に指定した広告をタイムライン `AuditudeResolver` に `replaceDuration` 挿入します。`replaceDuration`を指定しない場合は、何を挿入するかがサーバーによって決定されます。

これらのカスタム時間範囲操作をサポートするために、TVSDKは以下を提供します。

* 複数のコンテンツリゾルバー

   ストリームは、広告シグナリングモードと広告メタデータに基づいて、複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変わります。
* `CustomMarkerOpportunityGenerator`を使用して複数の初期オポチュニティを作成します。
* 新しい広告シグナリングモード`CUSTOM_RANGES`。

   広告は、JSONファイルなどの外部ソースの時間範囲データに基づいて配置されます。

