---
description: TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。
seo-description: TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。
seo-title: Notificationクラス
title: Notificationクラス
uuid: 08c29efe-245d-4a6d-80c6-cd561cbf3b5f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Notificationクラス{#notification-classes}

TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。

| クラス名 | 説明 |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | プレーヤーが再生を停止する原因となったエラーの通知を記述するクラス。 これは、通知タ [イプ](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) ERRORのPTNotificationです。 |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Primetime Playerフレームワークによってディスパッチされるすべての通知を一覧表示します。 |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現をPTNotificationHistoryにカプセル化 [します](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html)。 |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | 通知イベント履歴リストへのアクセスを提供する [通知オブジェクト](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) PTNotificationHistoryItemオブジェクトのログを格納するクラス。 つまり、PTNotificationの個別のインスタンスを含む各要素のリストを保持し [ます](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | PTNotificationHistoryの循環リストのエントリを定義し、通知と [そのタイムスタンプを保持する](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) クラス。 |

