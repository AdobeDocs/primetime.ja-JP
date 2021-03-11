---
description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
title: ビデオ分析
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# ビデオ分析の統合{#video-analytics-integration}

TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDKのビデオトラッキングでは、**Adobe AnalyticsVideo Essentials**&#x200B;サービスを使用して、ビデオ表示、ビデオ完了、広告インプレッション、ビデオ滞在時間などのビデオエンゲージメント指標を提供します。 このサービスの詳細については、Adobeの担当者にお問い合わせください。

以下の手順は、プレイヤーでビデオトラッキングをアクティブにする手順をまとめたものです。

1. 以下のビデオトラッキングコンポーネントを初期化または設定します。

   iOSでは、以下のコンポーネントがTVSDKに含まれています。

   * JSON設定ファイル
   * ビデオ分析メタデータオブジェクト
   * グローバルメタデータオブジェクト
   * ビデオ分析トラッカーオブジェクト

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。