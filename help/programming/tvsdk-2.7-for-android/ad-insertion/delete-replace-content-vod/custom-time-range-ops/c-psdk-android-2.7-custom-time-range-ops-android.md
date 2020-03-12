---
description: CustomRangeMetadataクラスは、VODストリームマーク、削除および置換の様々なタイプの時間範囲を識別します。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。
seo-description: CustomRangeMetadataクラスは、VODストリームマーク、削除および置換の様々なタイプの時間範囲を識別します。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。
seo-title: カスタム時間範囲操作
title: カスタム時間範囲操作
uuid: e9c6a135-124e-44d4-adf2-dc9d671e2483
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 概要 {#custom-time-range-operations}

CustomRangeMetadataクラスは、VODストリーム内の様々なタイプの時間範囲を識別します。マーク、削除、置換を行います。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

広告の削除および置換の場合、TVSDKは次のカスタム時間範囲 *操作モードを使用しま* す。

* **MARK** ：このモードは、以前のバージョンのTVSDKではカスタム広告マーカーと呼ばれていました。 モードは、既にVODストリームに配置されている広告の開始時間と終了時間を示します。 ストリーム内にタイプの時間範囲マーカ `MARK` ーがある場合、の初期配置がによって生 `Mode.MARK` 成され、によって解 `CustomMarkerOpportunityGenerator` 決されま `CustomRangeResolver`す。 広告は挿入されません。

* **DELETE** ：時 `DELETE` 間範囲の場合、タイプのイニシャ `placementInformation` ルが作成 `Mode.DELETE` され、によって解決されま `CustomRangeResolver`す。 `DeleteRangeTimelineOperation` タイムラインから削除する範囲を定義します。TVSDKは、Adobe Video Engine(AVE)API `removeByLocalTime` を使用してこの操作を完了します。 DELETE範囲とAdobe Primetime ad decisioningメタデータがある場合、最初に範囲が削除され、次に、一般的なAdobe Primetime ad decisioningワークフ `AuditudeResolver` ローを使用して広告が解決されます。

* **REPLACE** 時間範 `REPLACE` 囲に対して、1つと1つの `placementInformations` 最初の2つの名前が作成 `Mode.DELETE` されま `Mode.REPLACE`す。 `CustomRangeResolver` 最初に時間範囲を削除し、次に指定した `AuditudeResolver` 広告をタイムラインに `replaceDuration` 挿入します。 何も指定しな `replaceDuration` い場合、何を挿入するかはサーバーが決定します。

これらのカスタム時間範囲操作をサポートするため、TVSDKは次の機能を提供します。

* 複数のコンテンツリゾルバー

   ストリームは、広告シグナリングモードと広告メタデータに基づいて複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変化します。
* を使用して複数の初期オポチュニテ `CustomMarkerOpportunityGenerator`ィ。
* 新しい広告シグナリングモードで `CUSTOM_RANGES`す。

   広告は、JSONファイルなどの外部ソースの時間範囲データに基づいて配置されます。

