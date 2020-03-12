---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。
seo-title: カスタム時間範囲操作
title: カスタム時間範囲操作
uuid: e04af786-8dac-41a6-8406-f2ca04f612a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタム時間範囲操作 {#custom-time-range-operations}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除と置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除および置き換えることもできます。

広告削除および置換は、VODストリー `TimeRange` ムの様々なタイプの時間範囲を識別する要素を使用して実装されます。マーク、削除、置換を行います。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。

広告の削除および置換の場合、TVSDKは次のカスタム時間範囲 *操作モードを使用しま* す。

* **MARK**（以前のバージョンのTVSDKでは、これらはカスタム広告マーカーと呼ばれていました）。 既にVODストリームに配置されている広告の開始時間と終了時間をマークします。 ストリーム内にタイプMARKの時間範囲マーカーが存在する場合、の初期配置が生 `Mode.MARK``CustomAdMarkersContentResolver`成され、 広告は挿入されません。

* **DELETE** DELETE時間範囲の場合、タイプのイニ `placementInformation` シャルが作成 `Mode.DELETE``DeleteContentResolver`され、対応する `ContentRemoval` は、タイムライン `timelineOperation` から削除する範囲を定義する新しいです。 TVSDKは、Adobe Video Engine(AVE)API `removeByLocalTime` からこの操作を容易に行うために使用します。 DELETE範囲とAdobe Primetime ad decisioning（旧称Auditude）メタデータがある場合、その範囲が最初に削除され、次に通常のAdobe Primetime ad decisioningワークフローを使用して `AuditudeResolver` 広告が解決されます。

* **REPLACE** REPLACE時間範囲の場合、1つと1つの `placementInformations` 2つの初期値が作成 `Mode.DELETE` されます `Mode.REPLACE`。 が最初 `DeleteContentResolver` に時間範囲を削除し、次に指定し `AuditudeResolver` た広告をタイムラインに `replaceDuration` 挿入します。 何も指定しな `replaceDuration` い場合、何を挿入するかはサーバーが決定します。

これらのカスタム時間範囲操作をサポートするため、TVSDKは次の機能を提供します。

* 複数のコンテンツリゾルバー

   ストリームは、広告シグナリングモードと広告メタデータに基づいて複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変化します。
* 複数のイニシ `PlacementInformations` ャ `DefaultMediaPlayer` ル広告シグナリングモードと、によ `PlacementInformations` って解決される広告メタデータに基づいて、イニシャルのリストを作成しま `MediaPlayerClient`す。

* 新しい広告シグナリングモード：カスタム時間範囲

   広告は、外部ソース（JSONファイルなど）の時間範囲データに基づいて配置されます。