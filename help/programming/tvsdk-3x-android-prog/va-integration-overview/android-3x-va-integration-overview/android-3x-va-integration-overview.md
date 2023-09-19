---
description: TVSDK とAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
title: TVSDK とAdobe Analyticsの統合
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# TVSDK とAdobe Analyticsの統合 {#integrating-tvsdk-with-adobe-analytics}

TVSDK とAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDK のビデオトラッキングでは、 **Adobe Analytics Video Essentials** サービス：ビデオ視聴、ビデオ完了、広告インプレッション、ビデオ滞在時間など、ビデオエンゲージメント指標を提供します。 このサービスの詳細については、Adobe担当者にお問い合わせください。

以下の手順は、プレーヤーでビデオトラッキングを有効にする手順の概要を示しています。

1. 次のビデオトラッキングコンポーネントを初期化または設定します。

   >[!TIP]
   >
   >Android では、これらのコンポーネントは TVSDK に含まれています。

   * JSON 設定ファイル
   * ビデオ分析メタデータオブジェクト
   * グローバルメタデータオブジェクト

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。
