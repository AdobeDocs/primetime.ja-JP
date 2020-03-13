---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-title: Timeline advertisingクラス
title: Timeline advertisingクラス
uuid: f424fa13-778b-458d-bc82-389441a8a56a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Timeline advertisingクラス {#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

パッケージ： [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)Package: [com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| 名前 | 説明 |
|---|---|
| [広告](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Ad抽象を定義し、すべての広告情報を保持するクラス。 一意のID、期間およびIDで定義されます `MediaResource`。 には、 `MediaResource` 実際の広告コンテンツが存在するURLが含まれます。 |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | 表示するアセットを表すクラス。 広告アセットを表すクラス。 |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | 再生中の特定の時点で再生される複数の広告に対して統合ビューを提供するクラス。 |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | シーク中に広告をバイパスするユーザーに関連する広告再生ポリシーを定義する列挙。 |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | 特定の広告の時間に関連付けられたタイムライン項目。 |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | 広告の時間をいつ視聴済みとしてマークするかに関して可能なポリシーの列挙クラス。 |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルーURLと、ユーザーに追加情報を提供するために使用できるタイトルに関する情報が含まれます。 |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | シークまたはトリック再生モードの後で広告の時間の再生を再開する場所に関して可能なポリシーの列挙クラス。 |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | シークや通常の再生など、プレーヤーの再生方法をリストする列挙クラス。 |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | API呼び出しのプロパティを定義するイ `AdPolicySelector` ンターフェイス。 これらのプロパティは、各広告の動作を適用するコンテキストを提供します。 |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | 広告の動作を適用するための広告ポリシーセレクターインターフェイス。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトのポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このインターフェイスに準拠できます。 |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | 特定の広告に関連付けられたタイムライン項目。 |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | TVSDKプロセスでプライムタイム広告解決を処理するクラス。 |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | TVSDKがサポートするすべての広告タイプの列挙。 |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | クラス。 |

