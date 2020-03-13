---
description: MediaPlayerNotificationは、プレイヤーのステータスに関連する情報を提供します。
seo-description: MediaPlayerNotificationは、プレイヤーのステータスに関連する情報を提供します。
seo-title: 通知内容
title: 通知内容
uuid: c2321a49-1b60-4e44-b8e2-a023b764d779
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 通知内容{#notification-content}

MediaPlayerNotificationは、プレイヤーのステータスに関連する情報を提供します。

TVSDKは、通知の時系列のリストを提供 `MediaPlayerNotification` します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * 情報の入力、警告またはエラー
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキーと値のペア。 例えば、という名前のキ `URL` ーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与え `MediaPlayerNotification` る別のオブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログやグラフィカル表示のためにリモートサーバーに送信したりできます。
