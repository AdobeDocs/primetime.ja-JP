---
description: TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。
title: カスタム時間範囲操作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# カスタム時間範囲操作{#custom-time-range-operations}

TVSDKは、VODストリーム内の広告コンテンツのプログラムによる削除および置換をサポートしています。

削除および置換機能は、カスタム広告マーカー機能を拡張するものです。 カスタム広告マーカーは、メインコンテンツの一部を広告関連コンテンツ期間としてマークします。 これらの時間範囲をマークするだけでなく、時間範囲を削除したり置き換えたりすることもできます。

広告削除および置換は、VODストリームの様々なタイプの時間範囲を識別する`TimeRange`要素を使用して実装されます。マーク、削除、置換を行います。 これらのカスタム時間範囲タイプごとに、広告コンテンツの削除や置換など、対応する操作を実行できます。

広告削除および置換の場合、TVSDKは次の&#x200B;*カスタム時間範囲操作*&#x200B;モードを使用します。

* **MARK**
（以前のバージョンのTVSDKでは、これらはカスタム広告マーカーと呼ばれていました）。VODストリームに既に配置されている広告の開始時間と終了時間をマークします。 ストリーム内にタイプMARKの時間範囲マーカーがある場合、 
`Mode.MARK` が生成され、によって解決され `CustomAdMarkersContentResolver`ます。広告は挿入されません。

* **DELETEFor**
DELETE時間範囲、初期 
`placementInformation` のタイプ `Mode.DELETE`  `DeleteContentResolver`は、対応する`ContentRemoval` は、タイムラインから削除 `timelineOperation` する範囲を定義する新しいです。TVSDKは、Adobeビデオエンジン(AVE)APIの`removeByLocalTime`を使用して、その操作を容易にします。 DELETE範囲とAdobe Primetimead decisioning（旧称Auditude）メタデータがある場合は、その範囲が最初に削除され、次に`AuditudeResolver`が通常のAdobe Primetimead decisioningワークフローを使用して広告を解決します。

* **REPLACEFまたは**
REPLACE時間範囲。 
`placementInformations` が作成され、1つ `Mode.DELETE` と1つが作成され `Mode.REPLACE`ます。`DeleteContentResolver`が最初に時間範囲を削除し、次に`AuditudeResolver`が指定した`replaceDuration`の広告をタイムラインに挿入します。 `replaceDuration`を指定しない場合は、何を挿入するかがサーバーによって決定されます。

これらのカスタム時間範囲操作をサポートするために、TVSDKは以下を提供します。

* 複数のコンテンツリゾルバー

   ストリームは、広告シグナリングモードと広告メタデータに基づいて、複数のコンテンツリゾルバーを持つことができます。 広告シグナリングモードと広告メタデータの組み合わせが異なると、動作が変わります。
* 複数の初期`PlacementInformations``DefaultMediaPlayer`。広告シグナリングモードと広告メタデータに基づいて、初期`PlacementInformations`のリストを作成し、`MediaPlayerClient`で解決します。

* 新しい広告シグナリングモード：カスタム時間範囲

   広告は、外部ソース（JSONファイルなど）の時間範囲データに基づいて配置されます。