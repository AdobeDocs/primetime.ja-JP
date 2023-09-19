---
description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
title: 通知システムの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# 通知システムの設定{#set-up-your-notification-system}

通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。

Primetime Player 通知システムの中心となるのは、スタンドアロン通知を表す Notification クラスです。

NotificationHistory クラスは、通知を蓄積するメカニズムを提供します。 通知のログを保存します ( `NotificationHistoryItem`) 通知のコレクションを表すオブジェクト。

通知を受け取るには：

* 通知をリッスンする
* 通知履歴に通知を追加する

1. 状態の変更をリッスンします。
1. の実装 `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` イベントリスナー。
1. TVSDK が `MediaPlayer.StatusChangeEvent` 次の 2 つのパラメーターを含むイベントリスナーのインスタンス。

   * 新しい状態 ( `MediaPlayer.Status`)
   * A `MediaPlayerNotification` object
