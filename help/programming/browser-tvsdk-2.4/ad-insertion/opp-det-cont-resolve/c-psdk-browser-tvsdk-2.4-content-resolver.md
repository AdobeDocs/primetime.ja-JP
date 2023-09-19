---
description: オポチュニティディテクターは、ストリーム内のカスタムタグを検出し、配置オポチュニティを識別する Browser TVSDK コンポーネントです。 これらのオポチュニティは、コンテンツリゾルバーに送信され、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。
title: オポチュニティディテクターとコンテンツリゾルバーのカスタマイズ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 概要 {#customize-opportunity-detectors-and-content-resolvers-overview}

オポチュニティディテクターは、ストリーム内のカスタムタグを検出し、配置オポチュニティを識別する Browser TVSDK コンポーネントです。 これらのオポチュニティは、コンテンツリゾルバーに送信され、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。

ブラウザー TVSDK には、以下のデフォルトのオポチュニティディテクターが含まれています。

* `AdSignalingModeOpportunityGenerator`：広告シグナリングモードに基づいて、初期広告配置オポチュニティを作成します。
* `ManifestCuesOpportunityGenerator`：任意のスプライスアウトタグから広告配置オポチュニティを作成します。

また、Browser TVSDK には、次のようなデフォルトのコンテンツリゾルバーも含まれています。 `AuditudeResolver`：プレーヤーアイテムのメタデータキーに基づいて挿入されるコンテンツを提供します。 `AuditudeResolver` は、Adobe Primetime ad decisioning サーバーと通信し、配置する広告の時間を返すことができます。

デフォルトのオポチュニティディテクターとコンテンツリゾルバーを上書きして、次の方法で広告ワークフローをカスタマイズできます。

* カスタムタグ検出のサポートを追加
* 広告挿入用のカスタムタグを認識する
* カスタマイズされた広告プロバイダーの作成
