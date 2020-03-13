---
description: 通知をリッスンし、独自の通知を通知履歴に追加できます。
seo-description: 通知をリッスンし、独自の通知を通知履歴に追加できます。
seo-title: 通知システムの設定
title: 通知システムの設定
uuid: 2d1876c7-4ce6-491c-880b-dd94697d4feb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 通知システムの設定{#set-up-your-notification-system}

通知をリッスンし、独自の通知を通知履歴に追加できます。

Primetime Player通知システムの中核は、スタンドアロン通知を表すNotificationクラスです。

NotificationHistoryクラスは、通知を蓄積するメカニズムを提供します。 通知のコレクションを表す通知( `NotificationHistoryItem`)オブジェクトのログを保存します。

通知を受信するには：

* 通知のリッスン
* 通知履歴への通知の追加

1. 状態の変更をリッスンします。
1. イベントリスナー `MediaPlayer.StatusChangeEvent.STATUS_CHANGED` を実装します。
1. TVSDKは、2つのパラメー `MediaPlayer.StatusChangeEvent` ターを含む1つのインスタンスをイベントリスナーに渡します。

   * 新しい状態( `MediaPlayer.Status`)
   * オブジェクト `MediaPlayerNotification` です。

