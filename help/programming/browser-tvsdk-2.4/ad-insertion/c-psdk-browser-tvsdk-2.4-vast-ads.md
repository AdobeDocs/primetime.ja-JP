---
description: ブラウザー TVSDK が、プライマリ広告サーバー上にない広告をリクエストする場合、プレーヤーはセカンダリサーバーから広告をリクエストする必要があります。 Video Ad Serving Template(VAST) は、広告サーバーとビデオプレーヤー間の通信の標準を設定します。これは、広告が要求されたときにセカンダリ広告サーバーから送信される応答です。
title: VAST 広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# VAST 広告 {#vast-ads}

ブラウザー TVSDK が、プライマリ広告サーバー上にない広告をリクエストする場合、プレーヤーはセカンダリサーバーから広告をリクエストする必要があります。 Video Ad Serving Template(VAST) は、広告サーバーとビデオプレーヤー間の通信の標準を設定します。これは、広告が要求されたときにセカンダリ広告サーバーから送信される応答です。

VAST について詳しくは、 [デジタルビデオ広告サービングテンプレート (VAST)3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

ブラウザー TVSDK は、次の VAST 広告要素をサポートしています。

## ラッパーおよびインライン広告 {#section_11B8A1A8F52F4F77981C6AAC02185087}

次の要素がサポートされています。

* **`wrapper`** プレーヤーがセカンダリ広告サーバーと通信して広告をリクエストする必要がある場合、ラッパー要素はリダイレクト情報を提供します。 1 つのラッパー要素は、最終的に VAST 広告を指す複数のラッパーを指すことができます。

* **`inline`** 次の必須要素がサポートされています。

* `AdSystem`
* `AdTitle`
* `Impression`

  次のオプション要素がサポートされています。

* `Description`
* `Survey`
* `Error`

## クリエイティブ {#section_0121F948CB074E49A8132D202786CAA4}

この要素は、VAST 広告の一部であり、 `creative` リニア広告、非リニア広告またはコンパニオン広告をサポートできる要素です。 Adobe Analytics の `creative` 要素、 `id`, `sequence`、および `adId` 要素がサポートされています。

広告タイプの詳細を以下に示します。

* **リニア広告** 次の要素がサポートされています。

   * `TrackingEvent`（を含む） `Tracking` 要素を選択します。
      * `Duration`
      * `AdParameters`
      * `VideoClicks`（以下を含む）

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`

        >[!TIP]
        >
        >この要素では、 `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework`、および `type` 属性がサポートされています。

* **非リニア広告** 次の要素がサポートされています。

   * `Non-linear`

     >[!TIP]
     >
     >この要素では、 `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio`、および `minSuggestedDuration` 属性がサポートされています。

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **コンパニオン広告** 次の要素がサポートされています。

   * `Companion`

     >[!TIP]
     >
     >この要素では、 `id`, `width`, `height`, `apiFramework`, `expandedWidth`、および `expandedHeight` 属性がサポートされています。

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## 拡張機能 {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Auditude固有の拡張機能のみがサポートされます。

* `Extension`
