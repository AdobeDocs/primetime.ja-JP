---
description: エラー、警告およびログおよびデバッグ目的の問題に関する一部のアクティビティに関するメッセージを記述するクラスです。
title: Notification クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Notification クラス {#notification-classes}

エラー、警告およびログおよびデバッグ目的の問題に関する一部のアクティビティに関するメッセージを記述するクラスです。

パッケージ： [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| クラス名 | 説明 |
|---|---|
| [通知](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | 指定された通知コードに関連付けられた説明を返し、通知オブジェクトの数値定数を提供します。 |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | 通知オブジェクトのログを保存するクラス。 次の循環リスト： [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) 通知イベント履歴リストへのアクセスを提供するオブジェクト。 つまり、要素のリストを維持し、各要素には [通知](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) クラス。 |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | の循環リストのエントリを定義するクラス [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) およびは、通知とそのタイムスタンプを保持します。 |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | サポートされる通知タイプを含むクラス。 |
