---
description: オポチュニティジェネレーターは、ストリーム内のカスタムタグ、広告シグナリングモードのカスタムマーカーなどによって配置オポチュニティを識別します。 オポチュニティジェネレーターは、これらの配置オポチュニティをコンテンツリゾルバーに送信し、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。
title: オポチュニティジェネレーターとコンテンツリゾルバーのカスタマイズ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# 概要 {#customize-opportunity-generators-and-content-resolvers-overview}

オポチュニティジェネレーターは、ストリーム内のカスタムタグ、広告シグナリングモードのカスタムマーカーなどによって配置オポチュニティを識別します。 オポチュニティジェネレーターは、これらの配置オポチュニティをコンテンツリゾルバーに送信し、配置オポチュニティのプロパティとメタデータに基づいてコンテンツ/広告挿入ワークフローをカスタマイズします。

TVSDK には、次のデフォルトのオポチュニティジェネレーターが含まれています。

* `ManifestCuesOpportunityGenerator` は、デフォルトの広告キューからオポチュニティを生成します ( `#EXT-X-CUE`) をクリックします。

* `AdSignalingModeOpportunityGenerator` は、指定された広告シグナリングモードに対して初期オポチュニティを生成します。 キューまたは時間指定メタデータの情報は無視されます。
* `CustomMarkerOpportunityGenerator` は、ベイク処理された C3 広告を置き換えるオポチュニティを生成します。
* `AuditudeResolver`のオポチュニティジェネレーターは、遅延広告解決がオンの場合にオポチュニティを生成します。

TVSDK には、次のデフォルトのコンテンツリゾルバーも含まれています。

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`:Primetime ad decisioning と通信できます。

デフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを上書きして、次のような方法で広告ワークフローをカスタマイズできます。

* 広告挿入用のカスタムタグを認識する。 詳しくは、 [オポチュニティジェネレーターとコンテンツリゾルバーのカスタマイズ](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/content-resolver/android-3x-content-resolver.md).
* カスタマイズした広告プロバイダーを作成します。
* コンテンツをブラックアウトします。
