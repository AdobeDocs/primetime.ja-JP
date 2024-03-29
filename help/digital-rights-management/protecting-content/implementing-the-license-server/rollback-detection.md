---
title: ロールバックの検出
description: ロールバックの検出
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# ロールバックの検出{#rollback-detection}

ロールバック検出の場合、一部の使用ルールでは、権限を適用するためにクライアントが状態情報を維持する必要があります。 例えば、再生ウィンドウの使用ルールを適用するために、クライアントは、ユーザーがコンテンツの最初の表示を開始した日時を保存します。 このイベントは、再生ウィンドウの開始をトリガーします。 再生ウィンドウを安全に強制するには、クライアントに保存されている再生ウィンドウの開始時間を削除するために、ユーザーがクライアント状態のバックアップおよび復元を行わないようにする必要があります。 サーバーは、クライアントのロールバックカウンターの値を追跡することでこれを行います。

リクエストごとに、サーバーは`RequestMessageBase.getClientState()`を呼び出して`ClientState`オブジェクトを取得し、`ClientState.getCounter()`を呼び出してクライアント状態カウンターの現在の値を取得することで、カウンターの値を取得します。 サーバーは、各クライアントにこの値を格納する必要があります（`MachineId.getUniqueId()`を使用してロールバックカウンタ値に関連付けられたクライアントを識別します）。次に`ClientState.incrementCounter()`を呼び出してカウンタ値を1ずつ増やします。 カウンター値がサーバーで最後に表示された値より小さいことがサーバーで検出された場合は、クライアント状態がロールバックされた可能性があります。

クライアント状態の改ざん検出について詳しくは、`ClientState` APIリファレンスドキュメントを参照してください。
