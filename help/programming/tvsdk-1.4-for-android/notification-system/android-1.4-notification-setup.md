---
description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
seo-description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
seo-title: 通知システムのセットアップ
title: 通知システムのセットアップ
uuid: caa6a306-dea9-45ee-b0b3-569b5f2527a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# 通知システムのセットアップ{#set-up-your-notification-system}

通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。

Primetime Player通知システムの中核は`Notification`クラスで、スタンドアロン通知を表します。

`NotificationHistory`クラスは、通知を蓄積するメカニズムを提供します。 このクラスは、通知のコレクションを表す通知(NotificationHistoryItem)オブジェクトのログを保存します。

通知を受信するには：

* 通知をリッスンする
* 追加通知履歴への通知

1. 状態の変更をリッスンします。
1. `MediaPlayer.PlaybackEventListener.onStateChanged`コールバックを実装します。
1. TVSDKは、2つのパラメーターをこのコールバックに渡します。

   * 新しい状態(`MediaPlayer.PlayerState`)
   * `MediaPlayerNotification`オブジェクト

