---
description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-title: ビデオ分析の統合
title: ビデオ分析の統合
uuid: 275d2c88-a15c-4645-9234-f29d32fc4a63
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ビデオ分析の統合 {#video-analytics-integration}

TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDKのビデオトラッキングは、 **Adobe Analytics Video Essentials** サービスを使用します。このサービスは、ビデオビュー、ビデオ完了、広告インプレッション、ビデオ滞在時間などのビデオエンゲージメント指標を提供します。 このサービスについて詳しくは、アドビの担当者にお問い合わせください。

以下の手順は、プレーヤーでビデオトラッキングをアクティブにする手順の概要です。

1. 以下のビデオトラッキングコンポーネントを初期化または設定します。

   iOSでは、以下のコンポーネントがTVSDKの一部です。

   * JSON設定ファイル
   * ビデオ分析メタデータオブジェクト
   * グローバルメタデータオブジェクト
   * ビデオ分析トラッカーオブジェクト

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。