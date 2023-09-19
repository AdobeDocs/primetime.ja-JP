---
title: MVPD および選択したプログラマの指標を書き出す
description: MVPD および選択したプログラマの指標を書き出す
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# MVPD および選択したプログラマの指標を書き出す {#export-metric}

アカウント IQ のダッシュボードに、選択したセグメント内の購読者アカウントの資格情報共有の統計の表とグラフが表示されます。 共有パターンとスコアの表示に加えて、選択したセグメントの MVPD およびチャネルの購読者のアカウント使用状況指標と共有スコアを、これらのテーブルから書き出すこともできます。

MVPD および選択したプログラマーの指標を書き出すには、許可された MVPD ユーザーとしてログインした後に、次の手順を実行します。

1. 次の手順に従って、目的のセグメントを定義します。 [セグメントを定義して期間を選択する方法](/help/AccountIQ/howto-select-segment-timeframe.md) 評価のために [セグメントと期間](/help/AccountIQ/segments-timeframe.md) パネル。

1. 次のパネルの 1 つに移動します。

   * セグメント内のプログラマー
     ![](assets/prog-segment-export-option.png)

   * 共有の確率レベル別のアカウント数と使用状況

     ![](assets/progr-usage-panel-export.png)

1. 選択 **書き出し** オプションは、パネルの右上隅にあります。

データは CSV 形式で書き出され、ファイルがデバイス上にローカルにダウンロードされます。 目的の CSV ビューアおよびエディターを使用して、書き出されたレポートを開くことができます。

* セグメント内のプログラマー

  ![](assets/export-progr-in-seg.png)


* 共有の確率レベル別のアカウント数と使用状況

  ![](assets/export-acc-usage.png)
