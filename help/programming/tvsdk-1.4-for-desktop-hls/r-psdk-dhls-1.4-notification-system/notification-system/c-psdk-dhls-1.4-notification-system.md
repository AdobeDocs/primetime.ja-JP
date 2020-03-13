---
description: MediaPlayerNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。
seo-description: MediaPlayerNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。
seo-title: プレイヤーのステータス、アクティビティ、エラーおよびログに関する通知
title: プレイヤーのステータス、アクティビティ、エラーおよびログに関する通知
uuid: 7ce5bed0-f312-437e-a82f-b1d4a8e1926c
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 概要 {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

イベントリスナーを実装して、イベントを取得し、イベントに応答します。 多くのイベントは、ステータス `MediaPlayerNotification` 通知を提供します。