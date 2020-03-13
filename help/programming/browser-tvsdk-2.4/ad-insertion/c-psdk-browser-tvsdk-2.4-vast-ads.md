---
description: ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーはセカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定し、広告が要求されたときにセカンダリ広告サーバーから送信される応答です。
seo-description: ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーはセカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定し、広告が要求されたときにセカンダリ広告サーバーから送信される応答です。
seo-title: VAST広告
title: VAST広告
uuid: 052dae0c-2425-456c-aebe-531f68bb5aa8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VAST広告 {#vast-ads}

ブラウザーTVSDKが、プライマリ広告サーバー上にない広告をリクエストする場合、プレイヤーはセカンダリサーバーから広告をリクエストする必要があります。 ビデオ広告配信テンプレート(VAST)は、広告サーバーとビデオプレーヤー間の通信の標準を設定し、広告が要求されたときにセカンダリ広告サーバーから送信される応答です。

VASTについて詳しくは、デジタルビデ [オ広告配信テンプレート(VAST)3.0を参照してください](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)。

ブラウザーTVSDKは、次のVAST広告要素をサポートしています。

## ラッパー広告とインライン広告 {#section_11B8A1A8F52F4F77981C6AAC02185087}

次の要素がサポートされています。

* **`wrapper`** プレイヤーが広告をリクエストするためにセカンダリ広告サーバーに接続する必要がある場合、ラッパー要素はリダイレクト情報を提供します。 1つのラッパー要素が、最終的にVAST広告を指す複数のラッパーを指し示す場合があります。

* **`inline`** 次の必須要素がサポートされています。

* `AdSystem`
* `AdTitle`
* `Impression`

   次のオプションの要素がサポートされています。

* `Description`
* `Survey`
* `Error`

## クリエイティブ {#section_0121F948CB074E49A8132D202786CAA4}

この要素は、VAST広告の一部で、リニア広告、非リニア広告、またはコンパニオン広告をサポートする `creative` 要素を含むファイルです。 要素では、 `creative` 、、およびの `id`要素が `sequence`サポートさ `adId` れています。

広告タイプについて詳しくは、以下を参照してください。

* **リニア広告** ：次の要素がサポートされます。

   * `TrackingEvent`に含まれてい `Tracking` ます。
      * `Duration`
      * `AdParameters`
      * `VideoClicks`に含まれます。

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`
         [!TIP]
この要素では，,,,,,,, `id``bitrate``delivery``width``height``scalable``maintainAspectRatio``apiFramework``type` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

* **非リニア広告** ：次の要素がサポートされます。

   * `Non-linear`
      [!TIP]
この要素では，,,,,,,, `id``width``height``apiFramework``expandedWidth``expandedHeight``scalable``maintainAspectRatio``minSuggestedDuration` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **コンパニオン広告** ：次の要素がサポートされています。

   * `Companion`
      [!TIP]
この要素では、、、、、、、 `id`および `width`の属 `height`性がサ `apiFramework`ポー `expandedWidth`トさ `expandedHeight` れています。

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## 拡張子 {#section_17401C75F419453BAE83637EEB6E1E60}

[!TIP]
Auditude固有の拡張のみがサポートされます。

* `Extension`