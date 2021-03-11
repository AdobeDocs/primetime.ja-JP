---
description: 広告など、コンテンツを配置するためのタイムライン内のオポチュニティの検出を支援するクラスです。
title: Timeline generatorsクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Timeline generatorsクラス{#timeline-generators-classes}

広告など、コンテンツを配置するためのタイムライン内のオポチュニティの検出を支援するクラスです。

パッケージ：[com.adobe.mediacore.timeline.generators](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| 名前 | 説明 |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | 指定した広告シグナリングモードの初期オポチュニティを作成するクラス。 |
| [OpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | すべてのオポチュニティジェネレーターのベースクラス。 |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | オポチュニティジェネレーターがTVSDKコンポーネントと通信するために使用するインターフェイス。 |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | 再生タイムラインを監視し、SpliceOutコメントとしてマニフェストに挿入されている広告配置オポチュニティを検出するクラス。 |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | 時間指定メタデータ情報を使用して広告オポチュニティを検出し、生成するオポチュニティジェネレーターのデフォルト実装。 |