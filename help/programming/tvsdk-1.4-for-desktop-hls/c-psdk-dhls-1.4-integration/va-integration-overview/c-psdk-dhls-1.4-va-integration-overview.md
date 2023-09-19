---
description: TVSDK とAdobe Analyticsを統合することで、ビデオの使用を追跡できます。
title: ビデオ分析
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# ビデオ分析{#video-analytics}

TVSDK とAdobe Analyticsを統合することで、ビデオの使用を追跡できます。

TVSDK のビデオトラッキングでは、 **Adobe Analytics Video Essentials** サービス：ビデオ視聴、ビデオ完了、広告インプレッション、ビデオ滞在時間など、ビデオエンゲージメント指標を提供します。 このサービスの詳細については、Adobe担当者にお問い合わせください。

以下の手順は、プレーヤーでビデオトラッキングを有効にする手順の概要を示しています。

1. 次のビデオトラッキングコンポーネントを初期化または設定します。

   * **AppMeasurementライブラリ**  — 低レベルのデータ収集コアロジックが含まれます。 ビデオハートビートデータが蓄積され、ネットワーク経由で送信される場所です。
   * **ビデオハートビートライブラリ**  — ビデオハートビートデータ収集のコアロジックが含まれます。 ビデオハートビートライブラリは、 `AppMeasurement` ライブラリ API

     >[!TIP]
     >
     >アプリがビデオハートビートコードを直接操作しない。 代わりに、アプリは TVSDK API を使用して、プレーヤーのビデオトラッキング機能を設定します。

   * **VisitorID ライブラリ**  — ビデオプレーヤーをホストする Web ページへの訪問者を一意に識別します。

   >[!IMPORTANT]
   >
   >TVSDK に組み込まれているビデオトラッキング機能は、適切に設定された `AppMeasurement` インスタンス。 トラッキング要素は、 `AppMeasurement` ライブラリは、ビデオトラッキングを設定してアクティブ化する前に、既にインスタンス化されて設定されています。 TVSDK のビデオトラッキング機能は、 `AppMeasurement` ライブラリ。

1. Adobe Analytics管理ツールを使用して、サーバー側でビデオ分析レポートを設定します。
