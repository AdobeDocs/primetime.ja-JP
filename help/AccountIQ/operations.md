---
title: アカウント IQ の操作
description: アカウント IQ の操作には、購読者アカウントに対して自動化と一括操作を実行し、その効果を追跡するアクションを実行する必要があります。
source-git-commit: e61cca77bad4f01de871e300dc99d7368c283f2a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# 運用 {#operations-tab-next-steps}

選択したセグメント（アカウント IQ の Reports &amp; Analytics を使用）の購読者の使用パターンとパスワードの共有を把握したら、目標に向けてターゲット設定したアクションを実行し、パスワードの共有を軽減できます。

アカウント IQ の Operations 機能は、操作と呼ばれる重点的な手順を通じて、資格情報の共有に効果的に取り組み、管理するのに役立ちます。 このツールでは、目的を設計し、特定の購読者アカウントのグループに合わせて（目標に基づいて）ターゲットアクションを調整し、将来の期間にわたって自動化するオプションを提供します。 操作機能を使用すると、操作の作成と実行だけでなく、その影響を測定することができます。 そのため、影響を調整することで、借り手の変換や資格情報の共有の軽減など、効果を最適化するための戦略を調整できます。

表示する **運用** ページ選択 **運用** のオプション **アクション** をクリックします。 [ 操作 ] ページには、アカウント IQ システム上に既に存在するすべての操作とその詳細が表示されます。

![](assets/operations-page.png)

*図：アカウント IQ の既存の操作のリストと詳細*

「操作」ページでは、次の操作を実行できます。

* アカウント IQ に既に存在する操作のリストを表示します

* 次のような操作の詳細を表示します。

   * ステータス（スケジュール済み、実行中、終了、エラーまたは停止）

   * 進行状況（完了率）

   * ターゲットオーディエンス（操作を実行するセグメント）

   * スケジュール（操作の開始日と終了日）

   * 操作の作成日と終了日

* [新しい操作を作成](/help/AccountIQ/operation-affecting-user-segment.md)

* [操作レポートを表示](#operation-reports)

<!--* Search from the list of operations using Search field

* Stop an operation.

* Create a duplicate operation.

* [Configure columns of Operations details page](#configure-columns)-->

## 操作レポートを表示 {#operation-reports}

操作のレポートを表示して、操作の影響を分析できます。 工程のレポートを表示する手順は、次のとおりです。

1. メインの操作ページで操作名を選択します。

   レポートは積み重ね棒グラフの形式で表示されます。

   ![](assets/operation-impact-report.png)

   *図：運用レポートを開いて、運用の影響を確認*

   x 軸には評価期間がプロットされ、y 軸には操作の影響を測定する変数がプロットされます。

   例えば、上の画像では、y 軸の変数はアカウント数です。 グラフを見ると、特定の時間（操作評価期間の第 2 週など）に、操作セグメントに含まれるアカウント数と、その時間に含まれる操作セグメントの外部に含まれるアカウント数を比較できます。 したがって、評価期間中に操作セグメント内およびセグメント外でアカウント数がどのように変化するかを分析できます。

   したがって、疑うアカウントに警告 E メールを送信し、操作セグメントのアカウントが確率 90 を超え、コンテンツのストリーミングに 5 台以上のデバイスを使用する場合、セグメントの評価期間の最初のアカウントは 700 万を超えます。 この数は、グラフに示すように、評価期間中に変化し、操作の影響を示します。 評価に基づいて、アカウントの疑問に対する是正措置を講じたり、操作を続行したり、より良い結果を得るために戦略を調整して、資格情報の共有を抑えたりできます。

2. レポートを閉じて、メインの操作ページに戻るには、「 **運用** のオプション **アクション** をクリックします。

<!--

![](assets/operations-details.png)

*Figure: Operation details*
## Configure columns {#configure-columns}

You can select the icon to **Configure columns** on the top of the operations table.

![](assets/config-columns.png)

*Figure: Configure columns of Operations details page*-->