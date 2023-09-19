---
title: 購読者のセグメントと時間枠
description: コホートを定義するか、購読者セグメントを選択して、チャネル閲覧者が Account IQ のグラフィカルツールとレポートを使用できるように、アカウント共有の可能性とパターンを測定します。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# 購読者のセグメントと時間枠 {#cohorts-segments}

アカウント IQ にログインすると、上部にパネルが表示され、購読者を定義できます [セグメント](/help/AccountIQ/product-concepts.md#segment-segmet-def) を使用して結果をフィルタリングし、購読者共有の動作とパターンに関するレポートを表示します。

<!--![](assets/segment-timeframe-panel.png)-->

+++プログラマー向けのセグメント選択パネル

![](assets/segment-panel-programmer.png)

<!--![](assets/filter-panel.png)-->

次のドロップダウンオプションを使用して、セグメントを定義します。

**セグメント内の MVPD**

The **セグメント内の MVPD** セレクターを使用して、 [MVPDs](/help/AccountIQ/product-concepts.md#mvpd-def) （個人またはグループ）を選択します。このユーザーは、アカウント共有レポートを表示する購読者です。

このセレクターでは、個々の MVPD を選択する以外に、次のグループも選択できます。

* [スコアの共有による上位 10 件の MVPD](/help/AccountIQ/product-concepts.md#top-mvpds-def)

* [使用別上位 10 件の MVPD](/help/AccountIQ/product-concepts.md#top-mvpds-def)

* [アカウント別上位 10 件の MVPD](/help/AccountIQ/product-concepts.md#top-mvpds-def)

* [分離モード](/help/AccountIQ/isolation-mode.md)

**セグメント内のチャネル**

プログラマーユーザーとしてログインすると、チャネルを選択してアカウント共有分析を表示できます。 以下を使用します。 **セグメント内のチャネル** ドロップダウンオプションを使用して、組織内の個々のチャネルまたは複数のチャネルを選択します。

+++

+++MVPDs 用のセグメント選択パネル

![](assets/segment-panel-mvpd.png)

次のドロップダウンオプションを使用して、セグメントを定義します。

**セグメント内のチャネル**

The **セグメント内のチャネル** セレクターを使用すると、フィルターをさらに絞り込んで、選択した MVPD に対応するチャネルを選択できます。

* [スコアを共有した上位 10 人のプログラマー](/help/AccountIQ/product-concepts.md#top-mvpds-def)

* [使用状況別上位 10 位のプログラマー](/help/AccountIQ/product-concepts.md#top-mvpds-def)

* [アカウント別上位 10 件のプログラマー](/help/AccountIQ/product-concepts.md#top-mvpds-def)

**セグメント内の MVPD**

MVPD ユーザーとしてログインすると、名前が **セグメント内の MVPD**.

+++




<!--For example, you can define your segment as the "subscribers of the MVPD A that watched the channels X, Y, and Z".-->



## 精度と時間枠 {#granularity-timeframe}

The **精度と時間枠** セレクターを使用して、購読者の共有行動を表示する日付、期間、または時間を指定できます。

![精度と期間](assets/granularity-timeframe-weekwise.png)

これらの制御を使用して、問題文を「5 月にチャネル X、Y、Z を視聴した MVPD A の購読者」として定義できます。

