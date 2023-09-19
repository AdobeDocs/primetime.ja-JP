---
description: ブラウザー TVSDK は、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準のタグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。
title: オポチュニティジェネレーターとコンテンツリゾルバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# オポチュニティジェネレーターとコンテンツリゾルバー{#opportunity-generators-and-content-resolvers}

ブラウザー TVSDK は、広告をタイムラインに配置するデフォルトのオポチュニティジェネレーターとコンテンツリゾルバーを提供します。これらのジェネレーターとリゾルバーは、マニフェスト内の非標準のタグに基づいています。 アプリケーションは、マニフェストで識別されるオポチュニティに基づいてタイムラインを変更する必要がある場合があります。

An *`opportunity`* 通常、広告配置オポチュニティを示す、タイムライン上の目標地点を表します。 また、このオポチュニティは、タイムラインに影響を与える可能性のあるカスタム操作を示すこともできます。 An *`opportunity generator`* は、タイムライン内の特定のオポチュニティ（タグ）を識別し、これらのオポチュニティがタグ付けされたことを TVSDK に通知します。

商談は、 `TimedMetata`. The `ManifestCuesOpportunityGenerator` 次に基づいて商談を作成 `TimedMetadata` 各スプライスアウト広告タグ ( `MediaPlayerItemConfig.adTags`) がマニフェストで検出されました。 The `AdSignalingModeOpportunityGenerator` は、 `MediaPlayerItem` タイプおよびそれに関連する広告シグナリングモード。

>[!TIP]
>
>次の場合、 `AdvertisingMetadata.livePreroll` または `AdvertisingMetadata.preroll` プロパティが設定されている場合、 `AdSignalingModeOpportunityGenerator` は、ライブストリームのプリロールオポチュニティを生成します。

オポチュニティ（タグ）に関する通知がアプリケーションに届くと、一連の広告を挿入するなどして、アプリケーションがタイムラインを変更する場合があります。 デフォルトでは、Browser TVSDK は適切な *`content resolver`* 必要なタイムラインの変更またはアクションを実装する場合。 アプリケーションは、デフォルトのブラウザー TVSDK 広告コンテンツリゾルバーを使用するか、独自のコンテンツリゾルバーを登録することができます。

また、 `MediaPlayerItemConfig.adTags` デフォルト用の広告マーカータグ/キューをさらに追加するには `ManifestCuesOpportunityGenerator` クラスと使用 `MediaPlayerItemConfig.subscribedTags` 広告ワークフロー情報を持つ可能性のある追加のタグについて TVSDK がアプリケーションに通知できるようにするためです。

>[!TIP]
>
>のデフォルト値 `MediaPlayerItemConfig.adTags` および `MediaPlayerItemConfig.subscribeTags` 次に該当 `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.
