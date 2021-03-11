---
description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
title: 通知システムのセットアップ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# 通知システムのセットアップ{#set-up-your-notification-system}

通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。

Primetime Player通知システムの中核は、スタンドアロン通知を表すNotificationクラスです。

NotificationHistoryクラスは、通知を蓄積するメカニズムを提供します。 通知のコレクションを表す通知(`NotificationHistoryItem`)オブジェクトのログを保存します。

通知を受信するには：

* 通知をリッスンする
* 追加通知履歴への通知

1. 状態の変更をリッスンします。
1. `MediaPlayer.StatusChangeEvent.STATUS_CHANGED`イベントリスナーを実装します。
1. TVSDKは、`MediaPlayer.StatusChangeEvent`インスタンスをイベントリスナーに渡します。このリスナーには、次の2つのパラメーターが含まれています。

   * 新しい状態(`MediaPlayer.Status`)
   * `MediaPlayerNotification`オブジェクト

