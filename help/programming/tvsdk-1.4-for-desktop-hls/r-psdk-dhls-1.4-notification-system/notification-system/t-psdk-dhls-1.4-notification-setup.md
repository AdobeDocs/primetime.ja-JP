---
description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
seo-description: 通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。
seo-title: 通知システムのセットアップ
title: 通知システムのセットアップ
uuid: 2d1876c7-4ce6-491c-880b-dd94697d4feb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '139'
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

