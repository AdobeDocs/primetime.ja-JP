---
description: エラー、警告、およびTVSDKがログおよびデバッグの目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。
title: Notificationクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Notificationクラス{#notification-classes}

エラー、警告、およびTVSDKがログおよびデバッグの目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。

| クラス名 | 説明 |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | プレイヤーが再生を停止する原因となったエラーの通知を記述するクラス。 これは、通知タイプERRORの[PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html)です。 |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Primetime Playerフレームワークがディスパッチするすべての通知をリストします。 |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を[PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html)にカプセル化します。 |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | 通知イベント履歴リストへのアクセスを提供する通知オブジェクト[PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html)オブジェクトのログを格納するクラス。 つまり、[PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html)の個別のインスタンスを含むエレメントのリストを維持します |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html)の循環リストのエントリを定義し、通知とそのタイムスタンプを保持するクラス。 |

