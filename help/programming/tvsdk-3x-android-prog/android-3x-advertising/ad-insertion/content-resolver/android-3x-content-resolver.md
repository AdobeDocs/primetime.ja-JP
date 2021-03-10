---
description: オポチュニティジェネレーターは、ストリーム内のカスタムタグ、広告シグナリングモードのカスタムマーカーなどによって、配置オポチュニティを識別します。 オポチュニティジェネレーターは、これらの配置オポチュニティをコンテンツリゾルバーに送信します。コンテンツリゾルバーは、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。
title: オポチュニティジェネレーターとコンテンツリゾルバーのカスタマイズ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 概要{#customize-opportunity-generators-and-content-resolvers-overview}

オポチュニティジェネレーターは、ストリーム内のカスタムタグ、広告シグナリングモードのカスタムマーカーなどによって、配置オポチュニティを識別します。 オポチュニティジェネレーターは、これらの配置オポチュニティをコンテンツリゾルバーに送信します。コンテンツリゾルバーは、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。

TVSDKには、次のデフォルトのオポチュニティジェネレーターが含まれています。

* `ManifestCuesOpportunityGenerator` デフォルトの広告キュー(  `#EXT-X-CUE`)からオポチュニティを生成します。

* `AdSignalingModeOpportunityGenerator` 指定された広告シグナリングモードに対する初期オポチュニティを生成します。キューまたは時間指定メタデータ情報は無視されます。
* `CustomMarkerOpportunityGenerator` ベイクインC3広告を置き換えるオポチュニティを生成します。
* `AuditudeResolver`のオポチュニティジェネレーターは、遅延広告解決がオンの場合にオポチュニティを生成します。

TVSDKには、次のデフォルトコンテンツリゾルバーも含まれています。

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`を呼び出します。

デフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを上書きして、次のような方法で広告ワークフローをカスタマイズできます。

* 広告挿入用のカスタムタグを認識する。 詳しくは、[オポチュニティジェネレーターとコンテンツリゾルバーのカスタマイズ](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/content-resolver/android-3x-content-resolver.md)を参照してください。
* カスタマイズした広告プロバイダーを作成します。
* コンテンツをブラックアウトします。