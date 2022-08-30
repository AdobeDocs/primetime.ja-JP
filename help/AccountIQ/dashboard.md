---
title: アカウント IQ ダッシュボード
description: ダッシュボードを使用すると、幅広いサブスクライバーデータを分析することで、パスワード共有のインスタンスを特定できます。
exl-id: 616da2a5-c9fe-40ea-90cf-f565bc13e764
source-git-commit: 5b34fbe26078ae761d61179975366505c5628c9c
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# ダッシュボード {#dashboard}

ダッシュボードは、アカウント共有の範囲と影響を大まかに把握できるように設計されたグラフとレポートの集まりにデータをまとめて集計します。 アカウント IQ の主要なレポートと指標を含む単一のページが提供されます。

![アカウント IQ のダッシュボード](assets/dashboard-capture.png)


*図：ダッシュボード*

## 平均共有スコア — 現在のセグメントの集計 {#aggregated-sharing}

集計共有スコアパネルには、アカウントとストリーミングのボリュームに関する共有の量と影響を要約した上部の行が表示されます。

値は、購読者による秘密鍵証明書の共有の規模を把握するのに役立ち、それに基づいて行動する必要性の尺度を提供します。

![](assets/aggregate-sharing-score.png)


*図：平均共有スコアパネル — 現在のセグメントの集計*

次の 3 つの指標は、平均共有スコアの構成要素です。

### 共有レベル {#sharing-level}

共有レベルゲージは、選択した期間に、（定義されたセグメント内で）共有されたすべての購読者アカウントの割合を示します。

選択した期間に選択したプログラマチャネルの 1 つからストリーミングされた、選択した MVPD のセット内の各アカウントに対して計算された共有確率の平均に基づいて計算された値。

![](assets/sharing-level.png)


*図：共有レベル*

トレンドインジケーターは、の前の期間からの指標の値の変化の割合を示します。

### 共有アカウントからの使用 {#usage-from-shared-accounts}

このゲージは、定義されたセグメントおよび期間における、共有アカウントのすべての購読者アカウントの使用率を示します。 このゲージは、0～100%のスケールで（共有アカウントから）使用の範囲を示します。 これらの範囲（「低」、「中」、「高」、「異常」）は、業界平均に基づいています。

また、トレンドインジケーターも表示できます。これは、前の期間と比較した、共有アカウントからの使用の増加または減少を示しています。

![](assets/usage-4mshared-accounts.png)


*図：共有アカウントからの使用*

### 全体的な共有スコア {#overall-sharing-score}

全体的な共有スコアは、「共有レベル」や「共有アカウントの z 使用量」などの共有スコアの複合です。

業界と比較した場合の共有の相対的な影響を反映した値が提供されます。 目的はクレジットスコアと似ており、状況を 1 つの数字でまとめます。 しかし、この場合、数が多いほど、潜在的な害が大きくなります。

![](assets/overall-sharing-score.png)


*図：全体的な共有スコア*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)-->

### MVPDs の業界全体の共有スコア {#top-mvpds}

次の表は、セグメント内の MVPD の異なる集計共有スコアの比較ビューを示しています。

>[!NOTE]
>
>この表は、セグメント内の MVPD で表されるデータではなく、比較の目的で業界全体のデータを使用します。

![](assets/top-mvpds.png)


*図：全体スコア別のセグメントで上位の MVPD*

### チャネルおよび MVPD によるスコアの共有 {#sharin-score-by-channels-and-mvpds}

次の表は、現在のセグメント内の MVPDs に対して選択したチャネルの共有スコアの比較ビューを示しています。

![](assets/sharing-scores-by-channels-mvpds.png)


*図：チャネルおよび MVPD によるスコアの共有*

### アカウント共有の確率 {#accounts-sharing-probability}

このグラフは、共有確率 5 分割の範囲を非常に低い (0 ～ 20 %) から非常に高い (80 = 100 %) に分割します。

>[!NOTE]
>
>棒グラフは対数スケールを使用します。


![](assets/dashboard-ac-sharing-prob.png)


*図：異なる共有確率範囲の購読者アカウントの数と割合*

### 共有の確率レベル別のアカウント数と使用状況 {#number-of-accounts-usage-sharing-probability}

このパネルは、共有アカウントからの各キンタイルの関連使用量を使用して、共有確率の極めて低い (0 ～ 20 %) から非常に高い (80 ～ 100 %) までの範囲に分割されたアカウントの表形式の表示を提供します。

![](assets/no-acc-usage-prob-level.png)


*図：様々な確率範囲に該当するアカウント、トレンドおよび使用の数*



<!--
+++Dashboard for programmers

![dashboard of account IQ](assets/dashboard-capture.png)


*Figure: The dashboard*

## Average sharing score - aggregated for the current segment {#aggregated-sharing}

The Aggregated Sharing Score panel provides a top line readout summarizing the quantity and impact of sharing in terms of accounts and streaming volume.

The values help you understand the magnitude of credential sharing by your subscribers, hence providing a measure of the need to act upon it.

![](assets/aggregate-sharing-score.png)


*Figure: Average sharing score panel - aggregated for the current segment*

The following three metrics are components of the Average Sharing Score.

### Sharing level {#sharing-level}

The sharing level gauge shows the percentage of all your subscriber accounts (in the defined segment) that are shared, during the selected time frame.  

A value calculated based on an average of the sharing probability computed for every account in the set of selected MVPDs that has streamed from a one of the selected programmer channels during the selected time frame.

![](assets/sharing-level.png)


*Figure: Sharing level*

The Trend indicator shows the percentage change in the value of the metric in from the previous time frame.

### Usage from shared accounts {#usage-from-shared-accounts}

This gauge indicates what percent of the usage of all the subscriber accounts is from the shared accounts for the defined segment and time period. The gauge marks the ranges of usage (from shared accounts) on the scale of 0 to 100%. These ranges—named Low, Medium, High, and Abnormal—are based on the industry average.

You can also see the Trend indicator, which depicts a rise or fall in the usage from shared accounts as compared to the previous time frame.

![](assets/usage-4mshared-accounts.png)


*Figure: Usage from shared accounts*

### Overall sharing score {#overall-sharing-score}

Overall sharing score is composite of sharing scores including “Sharing level” and “z Usage from shared accounts”.

It provides a value meant to reflect the relative impact of sharing when compared to the industry. It’s purpose is similar to that of a credit score, summarizing the situation with a single number. But in this case, the higher the number the greater the potential harm.

![](assets/overall-sharing-score.png)


*Figure: Overall sharing score*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)

### Industrywide overall sharing scores for MVPDs {#top-mvpds}

This table provides a comparative view of the different Aggregated Sharing Scores for the MVPDs in the segment.

>[!NOTE]
>
>This table uses overall industry data for comparative purposes, not the data represented by those MVPDs in the segment.

![](assets/top-mvpds.png)


*Figure: Top MVPDs in segment by overall score*

### Sharing score by channels and MVPDs {#sharin-score-by-channels-and-mvpds}

This table provides a comparative view of sharing scores of the selected channels for the MVPDs in the current segment.

![](assets/sharing-scores-by-channels-mvpds.png)


*Figure: Sharing scores by channels and MVPDs*

### Accounts sharing probability {#accounts-sharing-probability}

This chart partitions accounts into ranges of sharing probability quintiles from very low (0-20%) to very high (80=100%).

>[!NOTE]
>
>The bar graph uses a logarithmic scale.


![](assets/dashboard-ac-sharing-prob.png)


*Figure: Numbers and percentages of subscriber accounts in different sharing probability ranges*

### Number of accounts and usage by sharing probability level {#number-of-accounts-usage-sharing-probability}

This panel provides tabular view of  accounts partitioned into ranges of sharing probability quintiles from very low (0-20%) to very high (80-100%) with each quintile’s associated usage from shared accounts.

![](assets/no-acc-usage-prob-level.png)


*Figure: Number of accounts, trends, and usages falling in various probability ranges*

+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}

![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}


![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++
-->