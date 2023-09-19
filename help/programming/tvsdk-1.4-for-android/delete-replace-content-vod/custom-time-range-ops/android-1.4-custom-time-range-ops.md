---
description: TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。
title: カスタム時間範囲操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# カスタム時間範囲操作 {#custom-time-range-operations}

TVSDK では、VOD ストリーム内の広告コンテンツのプログラムによる削除と置き換えをサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張したものです。 カスタム広告マーカーは、メインコンテンツのセクションを広告関連のコンテンツ期間としてマークします。 これらの時間範囲をマークする以外に、時間範囲を削除して置き換えることもできます。

広告の削除と置換は、 `TimeRange` VOD ストリーム内の様々なタイプの時間範囲を識別する要素（マーク、削除および置換）。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置き換えなど、対応する操作を実行できます。

広告の削除と置き換えに、 TVSDK は以下を使用します。 *カスタム時間範囲操作* モード：

* **トンボ**
（以前のバージョンの TVSDK では、カスタム広告マーカーと呼ばれていました）。 既に VOD ストリームに配置されている広告の開始時間と終了時間をマークします。 ストリーム内に MARK 型の時間範囲マーカーがある場合、 `Mode.MARK` が `CustomAdMarkersContentResolver`. 広告は挿入されません。

* **DELETE**
DELETE時間範囲の場合、 `placementInformation` のタイプ `Mode.DELETE` が作成され、対応する `DeleteContentResolver`. `ContentRemoval` は新しい `timelineOperation` これは、タイムラインから削除する範囲を定義します。 TVSDK が使用する `removeByLocalTime` をAdobeビデオエンジン (AVE)API から削除して、その操作を容易にします。 DELETE範囲とAdobe Primetime Ad Decisioning( 旧称：Auditude) メタデータがある場合、その範囲が最初に削除され、 `AuditudeResolver` 通常のAdobe Primetime ad decisioning ワークフローを使用して広告を解決します。

* **置換**
REPLACE 時間範囲の場合、2 つの初期値 `placementInformations` 作成済み、1 つ `Mode.DELETE` 一つ `Mode.REPLACE`. The `DeleteContentResolver` 最初に時間範囲を削除し、次に `AuditudeResolver` 指定した `replaceDuration` をタイムラインに追加します。 いいえの場合 `replaceDuration` を指定した場合、サーバーは何を挿入するかを決定します。

これらのカスタム時間範囲操作をサポートするために、 TVSDK は以下を提供します。

* 複数のコンテンツリゾルバー

  ストリームは、広告シグナリングモードおよび広告メタデータに基づいて、複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変わります。
* 複数の初期値 `PlacementInformations` The `DefaultMediaPlayer` 初期の `PlacementInformations` で解決される広告シグナリングモードおよび広告メタデータに基づく `MediaPlayerClient`.

* 新しい広告シグナリングモード：カスタム時間範囲

  広告は、外部ソース（JSON ファイルなど）の時間範囲データに基づいて配置されます。
