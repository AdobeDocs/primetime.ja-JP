---
description: 通知をリッスンし、独自の通知を通知履歴に追加できます。
seo-description: 通知をリッスンし、独自の通知を通知履歴に追加できます。
seo-title: 通知システムの設定
title: 通知システムの設定
uuid: caa6a306-dea9-45ee-b0b3-569b5f2527a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 通知システムの設定{#set-up-your-notification-system}

通知をリッスンし、独自の通知を通知履歴に追加できます。

Primetime Player通知システムの中核は、スタンドアロン `Notification` 通知を表すクラスです。

クラス `NotificationHistory` は、通知を蓄積するメカニズムを提供します。 通知のコレクションを表す通知(NotificationHistoryItem)オブジェクトのログを保存します。

通知を受信するには：

* 通知のリッスン
* 通知履歴への通知の追加

1. 状態の変更をリッスンします。
1. コールバックを実装 `MediaPlayer.PlaybackEventListener.onStateChanged` します。
1. TVSDKは、2つのパラメーターをコールバックに渡します。

   * 新しい状態( `MediaPlayer.PlayerState`)
   * オブジェクト `MediaPlayerNotification` です。

