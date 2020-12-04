---
description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-title: ビデオ分析
title: ビデオ分析
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# ビデオ分析{#video-analytics}

TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDKのビデオトラッキングでは、**Adobe AnalyticsVideo Essentials**&#x200B;サービスを使用して、ビデオ表示、ビデオ完了、広告インプレッション、ビデオ滞在時間などのビデオエンゲージメント指標を提供します。 このサービスの詳細については、Adobeの担当者にお問い合わせください。

以下の手順は、プレイヤーでビデオトラッキングをアクティブにする手順をまとめたものです。

1. 以下のビデオトラッキングコンポーネントを初期化または設定します。

   * **AppMeasurementライブラリ**  — 低レベルのデータ収集のコアロジックが含まれています。ビデオハートビートデータが累積され、ネットワーク経由で送信される場所です。
   * **ビデオハートビートライブラリ**  — ビデオハートビートデータ収集のコアロジックを含みます。ビデオハートビートライブラリは、`AppMeasurement`ライブラリAPIのサブセットにアクセスします。

      >[!TIP]
      >
      >アプリは、ビデオハートビートコードと直接やり取りすることはありません。 代わりに、アプリはTVSDK APIを使用して、プレイヤーのビデオトラッキング機能を設定します。

   * **VisitorIDライブラリ**  — ビデオプレーヤーをホストするWebページへの訪問者を一意に識別します。
   >[!IMPORTANT]
   >
   >TVSDKに組み込まれているビデオトラッキング機能は、適切に設定された`AppMeasurement`インスタンスに依存します。 トラッキング要素は、ビデオトラッキングを設定およびアクティブ化する前に、`AppMeasurement`ライブラリが既にインスタンス化され、設定済みであることを前提としています。 TVSDKのビデオトラッキング機能は、`AppMeasurement`ライブラリの完全に機能し、適切に設定されたインスタンスが存在するかどうかに依存します。

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。

