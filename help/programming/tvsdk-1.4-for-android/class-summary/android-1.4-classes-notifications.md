---
description: エラー、警告および TVSDK がログおよびデバッグ目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。
title: Notification クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Notification クラス{#notification-classes}

エラー、警告および TVSDK がログおよびデバッグ目的で発行する一部のアクティビティに関するメッセージを記述するクラスです。

パッケージ： [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)  パッケージ： [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| クラス名 | 説明 |
|---|---|
| MediaPlayerNotification. [エラー](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | プレーヤーが再生を停止する原因となるエラーの通知を記述するクラス。 これは、 [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) 通知タイプ ERROR の。 |
| MediaPlayerNotification. [情報](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | 情報通知を表すクラス。 これは、 [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) 通知タイプ INFO の。 |
| MediaPlayerNotification. [警告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | 警告通知を表すクラス。 これは、 [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) 通知タイプ WARNING の |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | 情報メッセージ、警告およびエラーを提供するクラス。 単一の通知イベントのオブジェクト表現を [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | 指定された通知コードに関連付けられた説明を返します。 |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | 通知オブジェクトのログを保存するクラス。 次の循環リスト： [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) 通知イベント履歴リストへのアクセスを提供するオブジェクト。 つまり、要素のリストを維持し、各要素には [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) クラス。 ( 内 [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) パッケージ )。 |
| NotificationHistory。 [項目](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | の循環リストのエントリを定義するクラス [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) およびは、通知とそのタイムスタンプを保持します。 |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | サポートされる通知タイプを含むクラス。 |
