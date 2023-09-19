---
description: エラー、警告および TVSDK がログおよびデバッグ目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。
title: Notification クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Notification クラス{#notification-classes}

エラー、警告および TVSDK がログおよびデバッグ目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。

| クラス名 | 説明 |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | プレーヤーが再生を停止する原因となるエラーの通知を記述するクラス。 これは、 [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) 通知タイプ ERROR の。 |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Primetime Player フレームワークによってディスパッチされるすべての通知のリストを表示します。 |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | 通知オブジェクトのログを保存するクラス [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) 通知イベント履歴リストへのアクセスを提供するオブジェクト。 つまり、要素のリストを維持し、各要素には [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | の循環リストのエントリを定義するクラス [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) およびは、通知とそのタイムスタンプを保持します。 |
