---
description: ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーは、セカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定します。これは、広告が要求されたときにセカンダリ広告サーバーによって送信される応答です。
seo-description: ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーは、セカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定します。これは、広告が要求されたときにセカンダリ広告サーバーによって送信される応答です。
seo-title: VAST広告
title: VAST広告
uuid: 052dae0c-2425-456c-aebe-531f68bb5aa8
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# VAST広告 {#vast-ads}

ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーは、セカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定します。これは、広告が要求されたときにセカンダリ広告サーバーによって送信される応答です。

VASTについて詳しくは、 [デジタルビデオ広告配信テンプレート(VAST) 3.0を参照してください](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)。

ブラウザーTVSDKは、以下のVAST広告エレメントをサポートしています。

## ラッパー広告とインライン広告 {#section_11B8A1A8F52F4F77981C6AAC02185087}

次の要素がサポートされています。

* **`wrapper`** プレイヤーが広告をリクエストするためにセカンダリ広告サーバーに接続する必要がある場合、ラッパー要素はリダイレクト情報を提供します。 1つのラッパー要素は、最終的にVAST広告を指す複数のラッパーを指し示すことができます。

* **`inline`** 次の必須要素がサポートされています。

* `AdSystem`
* `AdTitle`
* `Impression`

   次のオプションの要素がサポートされています。

* `Description`
* `Survey`
* `Error`

## クリエイティブ {#section_0121F948CB074E49A8132D202786CAA4}

この要素はVAST広告の一部であり、リニア広告、非リニア広告、またはコンパニオン広告をサポートする `creative` 要素を含むファイルです。 要素では、、、およ `creative` びの `id``sequence``adId` 要素がサポートされています。

広告タイプについて詳しくは、次を参照してください。

* **リニア広告** ：以下の要素がサポートされています。

   * `TrackingEvent`に含まれます。この中には `Tracking` 要素が含まれています。
      * `Duration`
      * `AdParameters`
      * `VideoClicks`に含まれる値は次のとおりです。

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`

         >[!TIP]
         >
         >この要素では、,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `id``bitrate``delivery``width``height``scalable``maintainAspectRatio``apiFramework``type`

* **非リニア広告** ：次の要素がサポートされます。

   * `Non-linear`

      >[!TIP]
      >
      >この要素では、,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `id``width``height``apiFramework``expandedWidth``expandedHeight``scalable``maintainAspectRatio``minSuggestedDuration`

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **コンパニオン広告** ：以下の要素がサポートされています。

   * `Companion`

      >[!TIP]
      >
      >この要素では、、、、、、、、およびの `id``width``height``apiFramework``expandedWidth``expandedHeight` 属性がサポートされています。

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## 拡張子 {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Auditude固有の拡張のみがサポートされます。

* `Extension`
