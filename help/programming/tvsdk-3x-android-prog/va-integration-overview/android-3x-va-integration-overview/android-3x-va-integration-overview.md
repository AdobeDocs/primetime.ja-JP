---
description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-description: TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
seo-title: TVSDKとAdobe Analyticsの統合
title: TVSDKとAdobe Analyticsの統合
uuid: 4d498d35-ec8e-40fc-8272-1637ef942bb0
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# TVSDKとAdobe Analyticsの統合 {#integrating-tvsdk-with-adobe-analytics}

TVSDKとAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDKのビデオトラッキングは、 **Adobe Analytics Video Essentials** サービスを使用します。このサービスは、ビデオビュー、ビデオ完了、広告インプレッション、ビデオ滞在時間などのビデオエンゲージメント指標を提供します。 このサービスについて詳しくは、アドビの担当者にお問い合わせください。

以下の手順は、プレーヤーでビデオトラッキングをアクティブにする手順の概要です。

1. 以下のビデオトラッキングコンポーネントを初期化または設定します。

   >[!TIP]
   >
   >Androidでは、これらのコンポーネントはTVSDKの一部です。

   * JSON設定ファイル
   * ビデオ分析メタデータオブジェクト
   * グローバルメタデータオブジェクト

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。