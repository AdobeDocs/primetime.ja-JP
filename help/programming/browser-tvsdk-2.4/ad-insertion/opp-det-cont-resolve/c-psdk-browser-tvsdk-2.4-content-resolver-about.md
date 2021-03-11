---
description: ブラウザーTVSDKは、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準タグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。
title: オポチュニティジェネレーターとコンテンツリゾルバー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# オポチュニティジェネレーターとコンテンツリゾルバー{#opportunity-generators-and-content-resolvers}

ブラウザーTVSDKは、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準タグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。

*`opportunity`*&#x200B;は、通常、広告配置オポチュニティを示す、タイムライン上の目標地点を表します。 また、このオポチュニティは、タイムラインに影響を与える可能性のあるカスタム操作を示すこともできます。 *`opportunity generator`*&#x200B;は、タイムライン内の特定のオポチュニティ（タグ）を識別し、これらのオポチュニティがタグ付けされたことをTVSDKに通知します。

オポチュニティは、タイムライン内の`TimedMetata`で識別されます。 `ManifestCuesOpportunityGenerator`は、マニフェストで検出された（`MediaPlayerItemConfig.adTags`内の）各スプライスアウト広告タグに対して作成された`TimedMetadata`オブジェクトに基づいてオポチュニティを作成します。 `AdSignalingModeOpportunityGenerator`は、`MediaPlayerItem`タイプと関連する広告シグナリングモードに基づく初期オポチュニティを作成します。

>[!TIP]
>
>`AdvertisingMetadata.livePreroll`または`AdvertisingMetadata.preroll`プロパティが設定されている場合、`AdSignalingModeOpportunityGenerator`はライブストリームのプリロールオポチュニティを生成します。

オポチュニティ（タグ）に関する通知がアプリケーションに送信されると、一連の広告を挿入するなどして、アプリケーションがタイムラインを変更する場合があります。 デフォルトでは、Browser TVSDKは適切な&#x200B;*`content resolver`*&#x200B;を呼び出して、必要なタイムラインの変更またはアクションを実装します。 アプリケーションは、デフォルトのブラウザーTVSDK広告コンテンツリゾルバーを使用するか、独自のコンテンツリゾルバーを登録できます。

また、`MediaPlayerItemConfig.adTags`を使用して、デフォルトの`ManifestCuesOpportunityGenerator`クラスに広告マーカータグ/キューを追加し、`MediaPlayerItemConfig.subscribedTags`を使用して、TVSDKが広告ワークフロー情報を持つ追加タグに関してアプリケーションに通知できます。

>[!TIP]
>
>`MediaPlayerItemConfig.adTags`と`MediaPlayerItemConfig.subscribeTags`のデフォルト値は`[MediaPlayerItemConfig.DEFAULT_AD_TAG]`です。

