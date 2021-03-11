---
description: オポチュニティディテクターは、ストリーム内のカスタムタグを検出し、配置オポチュニティを識別するTVADKコンポーネントです。 これらのオポチュニティはコンテンツリゾルバーに送信され、コンテンツリゾルバーは、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。
title: オポチュニティディテクターとコンテンツリゾルバーのカスタマイズ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 概要{#customize-opportunity-detectors-and-content-resolvers-overiew}

オポチュニティディテクターは、ストリーム内のカスタムタグを検出し、配置オポチュニティを識別するTVADKコンポーネントです。 これらのオポチュニティはコンテンツリゾルバーに送信され、コンテンツリゾルバーは、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。

TVSDKには、次のデフォルトのオポチュニティディテクターが含まれています。

* `SpliceOutOpportunityDetector`は、デフォルトの広告キューを認識します。
* `AdSignalingModeOpportunityGenerator`は、広告シグナリングモードに基づいて、初期広告配置オポチュニティを作成します。
* `SpliceOutOpportunityGenerator`は、任意の#EXT-X-CUEタグから広告配置オポチュニティを作成します。

TVSDKには、プレイヤーアイテムのメタデータキーに基づいて挿入されるコンテンツを提供する、次のデフォルトのコンテンツリゾルバーも含まれています。

* `AuditudeResolver`に含まれ、Adobe Primetimead decisioning（旧称Auditude）サーバーと通信し、配置する広告の時間を返すことができます。

デフォルトのオポチュニティディテクターとコンテンツリゾルバーを上書きして、次の方法で広告ワークフローをカスタマイズできます。

* カスタムタグ追加検出のサポート
* 広告挿入用のカスタムタグを認識する
* カスタマイズした広告プロバイダーの作成
* コンテンツの墨消し

