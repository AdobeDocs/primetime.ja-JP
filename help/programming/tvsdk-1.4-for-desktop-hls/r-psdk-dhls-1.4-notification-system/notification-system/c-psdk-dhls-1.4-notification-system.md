---
description: MediaPlayerNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーのステータスが変化する原因にもなります。
title: プレイヤーのステータス、アクティビティ、エラーおよびログに関する通知
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# 概要{#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーのステータスが変化する原因にもなります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

イベントリスナーを実装して、イベントを取得し、応答します。 多くのイベントは`MediaPlayerNotification`ステータス通知を提供します。