---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-title: Timeline advertisingクラス
title: Timeline advertisingクラス
uuid: f424fa13-778b-458d-bc82-389441a8a56a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Timeline advertising classes {#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

パッケージ：[com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)
パッケージ：[com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| 名前 | 説明 |
|---|---|
| [広告](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Ad抽象を定義し、すべての広告情報を保持するクラス。 一意のID、期間、`MediaResource`で定義されます。 `MediaResource`には、実際の広告コンテンツが存在するURLが含まれます。 |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | 表示するアセットを表すクラス。 広告アセットを表すクラス。 |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | 再生中の特定の時点で再生される複数の広告に対して統合表示を提供するクラス。 |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | シーク中に広告をバイパスするユーザーに関連する広告再生ポリシーを定義する定義済みリスト。 |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | 特定の広告の時間に関連付けられたタイムラインアイテム。 |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | 広告の時間をいつ視聴済みとしてマークするかに関して指定できるポリシーの定義済みリストクラス。 |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルーURLと、ユーザーに追加情報を提供する際に使用できるタイトルに関する情報が含まれています。 |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | シークまたはトリック再生モード後に広告の時間の再生をどこで再開するかに関して指定できるポリシーの定義済みリストクラスです。 |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | シークや通常再生など、プレイヤーの再生方法をリストする定義済みリストクラス。 |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | `AdPolicySelector` API呼び出しのプロパティを定義するインターフェイス。 これらのプロパティは、各広告の動作を適用するコンテキストを提供します。 |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | 広告の動作を適用する広告ポリシーセレクターインターフェイス。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このインターフェイスに適合できます。 |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | 特定の広告に関連付けられたタイムラインアイテム。 |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | TVSDKプロセスのプライムタイム広告解決を処理するクラス。 |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | TVSDKがサポートするすべての広告タイプの定義済みリスト。 |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | クラス。 |

