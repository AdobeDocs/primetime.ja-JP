---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
title: Timeline advertising クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Timeline advertising クラス {#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

パッケージ： [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/package-detail.html)
パッケージ： [com.adobe.mediacore.timeline.advertising.policy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/package-detail.html)

| 名前 | 説明 |
|---|---|
| [広告](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | 広告の抽象化を定義し、すべての広告情報を保持するクラス。 一意の ID、期間、および `MediaResource`. The `MediaResource` には、実際の広告コンテンツが存在する URL が含まれます。 |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | 表示するアセットを表すクラス。 広告アセットを表すクラス。 |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | 再生中にある時点で再生される、複数の広告に対して統合ビューを提供するクラス。 |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakPolicy.html) | シーク中に広告をバイパスするユーザーに関連する広告再生ポリシーを定義する列挙。 |
| [AdBreakTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdBreakTimelineItem.html) | 特定の広告ブレークに関連付けられたタイムライン項目。 |
| [AdBreakWatchedPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdBreakWatchedPolicy.html) | 広告の時間を視聴済みとしてマークするタイミングに関して使用可能なポリシーの列挙クラス。 |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルー URL に関する情報と、ユーザーに追加情報を提供するために使用できるタイトルが含まれています。 |
| [AdPolicy](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicy.html) | シークまたはトリック再生モード後に広告ブレークの再生を再開する場所に関して指定可能なポリシーの列挙クラスです。 |
| [AdPolicyMode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicyMode.html) | シーク再生や通常再生など、プレーヤーの再生方法をリストする列挙クラス。 |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | のプロパティを定義するインターフェイス `AdPolicySelector` API 呼び出し。 これらのプロパティは、各広告の動作を強制するコンテキストを提供します。 |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/policy/AdPolicySelector.html) | 広告の動作を強制する広告ポリシーセレクターインターフェイス。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトのポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このインターフェイスに準拠できます。 |
| [AdTimelineItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdTimelineItem.html) | 特定の広告に関連付けられたタイムライン項目。 |
| [AuditudeAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AuditudeAdResolver.html) | TVSDK プロセスでプリタイム広告の解決を処理するクラス。 |
| [AdType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/AdType.html) | TVSDK でサポートされているすべての広告タイプの列挙。 |
| [MetadataAdResolver](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/MetadataAdResolver.html) | クラス。 |
