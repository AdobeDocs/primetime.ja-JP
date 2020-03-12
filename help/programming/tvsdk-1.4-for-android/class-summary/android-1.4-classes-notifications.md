---
description: TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。
seo-description: TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。
seo-title: Notificationクラス
title: Notificationクラス
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Notificationクラス{#notification-classes}

TVSDKがログおよびデバッグの目的で発行するエラー、警告および一部のアクティビティに関するメッセージを記述するクラスです。

パッケージ： [com.adobe.mediacoreパッケージ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) : [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| クラス名 | 説明 |
|---|---|
| MediaPlayerNotification。 [エラー](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | プレーヤーが再生を停止する原因となったエラーの通知を記述するクラス。 これは、通知タ [イプ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) ERRORのMediaPlayerNotificationです。 |
| MediaPlayerNotification。 [情報](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | 情報通知を記述するクラス。 これは、通知タ [イプ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) INFOのMediaPlayerNotificationです。 |
| MediaPlayerNotification。 [警告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | 警告通知を記述するクラス。 これは、通知タ [イプ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) WARNINGのMediaPlayerNotificationです。 |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現をNotificationHistoryにカプセル化 [します](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html)。 |
| MediaPlayerNotification。 [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | 指定された通知コードに関連付けられた説明を返します。 |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | 通知オブジェクトのログを格納するクラス。 通知イベント履歴リ [ストへのアクセスを提供する](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) 、NotificationHistory.Itemオブジェクトの循環リストです。 つまり、MediaPlayerNotificationクラスの個別のインスタンスを含むエレメントのリストを保持 [します](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) 。 ( [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) package)。 |
| NotificationHistory。 [項目](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | NotificationHistoryの循環リストのエントリを定義し、通知とそのタ [イムスタンプ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) を保持するクラス。 |
| MediaPlayerNotification。 [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | サポートされる通知タイプを含むクラス。 |