---
description: ブラウザーTVSDKは、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準タグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。
seo-description: ブラウザーTVSDKは、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準タグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。
seo-title: オポチュニティジェネレーターとコンテンツリゾルバー
title: オポチュニティジェネレーターとコンテンツリゾルバー
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# オポチュニティジェネレーターとコンテンツリゾルバー{#opportunity-generators-and-content-resolvers}

ブラウザーTVSDKは、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準タグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。

は、通 *`opportunity`* 常、広告配置オポチュニティを示す、タイムライン上の目標地点を表します。 また、このオポチュニティは、タイムラインに影響を与える可能性のあるカスタム操作を示すこともできます。 タイムラ *`opportunity generator`* イン内の特定のオポチュニティ（タグ）を識別し、TVSDKに対して、これらのオポチュニティがタグ付けされたことを通知します。

オポチュニティは、のタイムラインで識別されま `TimedMetata`す。 では、 `ManifestCuesOpportunityGenerator` マニフェスト内で検出さ `TimedMetadata` れた各スプライスアウト広告タグ（内）に対して作成されたオ `MediaPlayerItemConfig.adTags`ブジェクトに基づいてオポチュニティが作成されます。 は、タ `AdSignalingModeOpportunityGenerator` イプと関連する広告シグナリングモードに基づ `MediaPlayerItem` く初期オポチュニティを作成します。

>[!TIP]
>
>またはプロパ `AdvertisingMetadata.livePreroll` ティが設 `AdvertisingMetadata.preroll` 定されている場合、ラ `AdSignalingModeOpportunityGenerator` イブストリームのプリロールオポチュニティが生成されます。

アプリにオポチュニティ（タグ）が通知されると、例えば、一連の広告を挿入するなどして、アプリケーションがタイムラインを変更する場合があります。 デフォルトでは、ブラウザーTVSDKは、必要なタイムラインの変 *`content resolver`* 更またはアクションを実装するために適切なを呼び出します。 アプリケーションは、デフォルトのブラウザーTVSDK広告コンテンツリゾルバーを使用するか、独自のコンテンツリゾルバーを登録できます。

また、を使用して、デ `MediaPlayerItemConfig.adTags` フォルトクラスに広告マーカータグ/キューを追加し、を使用して、広告ワークフロー情報を持つ可能性のある追加のタグについてTVSDKがアプリケー `ManifestCuesOpportunityGenerator``MediaPlayerItemConfig.subscribedTags` ションに通知できるようにすることもできます。

>[!TIP]
>
>とのデフォルト値 `MediaPlayerItemConfig.adTags` は `MediaPlayerItemConfig.subscribeTags` です `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`。

