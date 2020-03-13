---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-description: タイムライン内で発生する広告に関する情報を提供するクラスです。
seo-title: Timeline advertisingクラス
title: Timeline advertisingクラス
uuid: 4e6ca9fb-9e68-4625-a24b-386a50333862
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Timeline advertisingクラス{#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

パッケージ： [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

パッケージ： [com.adobe.mediacore.timeline.advertising.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| 名前 | 説明 |
|--- |--- |
| [広告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Ad抽象を定義し、すべての広告情報を保持するクラス。 一意のID、期間およびIDで定義されます `MediaResource`。 には、 `MediaResource` 実際の広告コンテンツが存在するURLが含まれます。 |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | 表示するアセットを表すクラス。 広告アセットを表すクラス。 |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | 再生中の特定の時点で再生される複数の広告に対して統合ビューを提供するクラス。 |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | 広告の時間の配置操作クラス。 |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | シーク中に広告をバイパスするユーザーに関連する広告再生ポリシーを定義する列挙。 |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルーURLと、ユーザーに追加情報を提供するために使用できるタイトルに関する情報が含まれます。 |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | AdPolicySelector API呼び出しのプロパティを定義するインターフェイス。 これらのプロパティは、各広告の動作を適用するコンテキストを提供します。 |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | 広告の動作を適用するための広告ポリシーセレクターインターフェイス。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトのポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このインターフェイスに準拠できます。 |
| `auditude.AuditudeAdProvider` | 廃止。 AuditudeResolverを使用します。 |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Phraseプロセスのプライムタイム広告解決を処理するクラス。 |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | ContentTrackerインターフェイスを実装し、Primetime広告追跡イベントを定義するクラス。 |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Phraseプロセスの広告解決部分を処理するクラス。 |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | ライブラリまたはカスタム広告トラッカーと統合するように設計された広告トラッキングモジュールを作成する場合に実装する必要があるプロトコルを定義するインターフェイス。 このインターフェイスでは、広告進行状況イベントをリモート広告トラッキングシステムにレポートする方法を定義する必要があります。 |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | 配置情報リクエストを抽象化するクラス。 解決される各広告には、配置情報が1つずつ添付されている必要があります。 配置情報は、広告が配置されるタイムライン上の場所を示します。 次のような情報が含まれます。 <ul><li>配置位置（ミリ秒） </li><li>配置のタイプ（プリロール、ミッドロールまたはポストロール） </li><li>置き換えられるメインコンテンツの長さ</li></ul> |
