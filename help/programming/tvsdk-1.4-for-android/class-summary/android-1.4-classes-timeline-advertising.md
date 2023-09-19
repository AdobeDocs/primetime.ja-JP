---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
title: Timeline advertising クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Timeline advertising クラス{#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

パッケージ： [com.adobe.mediacore.timeline.advertising](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

パッケージ： [com.adobe.mediacore.timeline.advertising.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| 名前 | 説明 |
|--- |--- |
| [広告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | 広告の抽象化を定義し、すべての広告情報を保持するクラス。 一意の ID、期間、および `MediaResource`. The `MediaResource` には、実際の広告コンテンツが存在する URL が含まれます。 |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | 表示するアセットを表すクラス。 広告アセットを表すクラス。 |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | 再生中にある時点で再生される、複数の広告に対して統合ビューを提供するクラス。 |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | 広告ブレークの配置操作クラス。 |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | シーク中に広告をバイパスするユーザーに関連する広告再生ポリシーを定義する列挙。 |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルー URL に関する情報と、ユーザーに追加情報を提供するために使用できるタイトルが含まれています。 |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | AdPolicySelector API 呼び出しのプロパティを定義するインターフェイス。 これらのプロパティは、各広告の動作を強制するコンテキストを提供します。 |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | 広告の動作を強制する広告ポリシーセレクターインターフェイス。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトのポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このインターフェイスに準拠できます。 |
| `auditude.AuditudeAdProvider` | 廃止されました。 AuditudeResolver を使用します。 |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Phrase プロセスで primetime と解決を処理するクラス。 |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | ContentTracker インターフェイスを実装し、Primetime 広告トラッキングイベントを定義するクラス。 |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Phrase プロセスの広告解決部分を処理するクラス。 |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | ライブラリまたはカスタム広告トラッカーと統合するように設計された広告トラッキングモジュールを作成する場合に実装する必要があるプロトコルを定義するインターフェイス。 このインターフェイスでは、リモート広告トラッキングシステムに広告進行状況イベントを報告する方法を定義する必要があります。 |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | 配置情報リクエストを抽象化するクラス。 解決された各広告には、1 つの配置情報が添付されている必要があります。 配置情報は、広告がタイムライン上のどこに配置されるかを示します。 次のような情報が含まれます。 <ul><li>配置の位置（ミリ秒） </li><li>配置のタイプ（プリロール、ミッドロールまたはポストロール） </li><li>置き換えられるメインコンテンツチャンクの期間</li></ul> |
