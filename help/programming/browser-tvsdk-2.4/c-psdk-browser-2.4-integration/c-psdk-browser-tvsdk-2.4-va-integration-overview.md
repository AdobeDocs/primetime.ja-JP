---
description: Browser TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-description: Browser TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-title: ビデオ分析
title: ビデオ分析
uuid: 6351933b-c0f3-4e3e-ad27-bedc8eecc312
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# ビデオ分析{#video-analytics}

Browser TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

ブラウザーTVSDKのビデオトラッキングでは、**Adobe AnalyticsVideo Essentials**&#x200B;サービスを使用して、ビデオ表示、ビデオ完了、広告インプレッション、ビデオ滞在時間などのビデオエンゲージメント指標を提供します。 このサービスの詳細については、Adobeの担当者にお問い合わせください。

以下の手順は、プレイヤーでビデオトラッキングをアクティブにする手順をまとめたものです。

1. 以下のビデオトラッキングコンポーネントを初期化または設定します。

   * **AppMeasurementライブラリ**  — 低レベルのデータ収集のコアロジックが含まれています。ビデオハートビートデータが累積され、ネットワーク経由で送信される場所です。
   * **ビデオハートビートライブラリ**  — ビデオハートビートデータ収集のコアロジックを含みます。ビデオハートビートライブラリは、AppMeasurementライブラリAPIのサブセットにアクセスします。

      >[!TIP]
      >
      >アプリは、ビデオハートビートコードと直接やり取りすることはありません。 代わりに、アプリはブラウザーTVSDK APIを使用して、プレイヤーのビデオトラッキング機能を設定します。

   * **VisitorIDライブラリ**  — ビデオプレーヤーをホストするWebページへの訪問者を一意に識別します。
   >[!IMPORTANT]
   >
   >ブラウザーTVSDKに組み込まれているビデオトラッキング機能は、適切に設定されたAppMeasurementインスタンスに依存します。 トラッキング要素は、ビデオトラッキングを設定およびアクティブ化する前に、AppMeasurementライブラリが既にインスタンス化および設定済みであることを前提としています。 ブラウザーTVSDKのビデオトラッキング機能は、AppMeasurementライブラリの完全に機能し、適切に設定されたインスタンスが存在するかどうかに依存します。

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。