---
description: エラー、警告、およびTVSDKがログおよびデバッグの目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。
seo-description: エラー、警告、およびTVSDKがログおよびデバッグの目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。
seo-title: Notificationクラス
title: Notificationクラス
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# Notificationクラス{#notification-classes}

エラー、警告、およびTVSDKがログおよびデバッグの目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。

パッケージ：[com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)パッケージ：[com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| クラス名 | 説明 |
|---|---|
| MediaPlayerNotification. [エラー](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | プレイヤーが再生を停止する原因となったエラーの通知を記述するクラス。 これは、通知タイプERRORの[MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html)です。 |
| MediaPlayerNotification. [情報](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | 情報通知を記述するクラス。 これは、通知タイプINFOの[MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html)です。 |
| MediaPlayerNotification. [警告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | 警告通知を記述するクラス。 これは、通知タイプWARNINGの[MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html)です。 |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を[NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html)にカプセル化します。 |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | 指定した通知コードに関連付けられた説明を返します。 |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | 通知オブジェクトのログを格納するクラス。 通知イベント履歴リストへのアクセスを提供する[NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html)オブジェクトの循環リスト。 つまり、エレメントのリストを維持します。各エレメントには[MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html)クラスの個別のインスタンスが含まれます。 （[session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)パッケージ内）。 |
| NotificationHistory。 [項目](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html)の循環リストのエントリを定義し、通知とそのタイムスタンプを保持するクラス。 |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | サポートされる通知タイプを含むクラス。 |