---
description: MediaPlayerNotification オブジェクトは、プレーヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスが変更される原因となります。
title: プレーヤーのステータス、アクティビティ、エラーおよびログに関する通知
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# 概要 {#notifications-for-player-status-activity-errors-and-logging-overview}

MediaPlayerNotification オブジェクトは、プレーヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスが変更される原因となります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断および検証用のログシステムを作成することもできます。

イベントリスナーを実装して、イベントをキャプチャし、それに応答します。 多くのイベントには `MediaPlayerNotification` ステータスの通知。
