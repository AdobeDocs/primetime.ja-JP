---
description: エラー、警告、およびログおよびデバッグの目的で発生する一部のアクティビティに関するメッセージを記述するクラスです。
seo-description: エラー、警告、およびログおよびデバッグの目的で発生する一部のアクティビティに関するメッセージを記述するクラスです。
seo-title: Notificationクラス
title: Notificationクラス
uuid: 3befc64b-4abd-47df-9c45-215b49029757
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Notificationクラス{#notification-classes}

エラー、警告、およびログおよびデバッグの目的で発生する一部のアクティビティに関するメッセージを記述するクラスです。

パッケージ：[com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| クラス名 | 説明 |
|---|---|
| [通知](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を[NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html)にカプセル化します。 |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | 指定された通知コードに関連付けられた説明を返し、通知オブジェクトに数値定数を提供します。 |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | 通知オブジェクトのログを格納するクラス。 通知イベント履歴リストへのアクセスを提供する[NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html)オブジェクトの循環リスト。 つまり、エレメントのリストを維持します。各エレメントには[Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html)クラスの個別のインスタンスが含まれます。 |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html)の循環リストのエントリを定義し、通知とそのタイムスタンプを保持するクラス。 |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | サポートされる通知タイプを含むクラス。 |

