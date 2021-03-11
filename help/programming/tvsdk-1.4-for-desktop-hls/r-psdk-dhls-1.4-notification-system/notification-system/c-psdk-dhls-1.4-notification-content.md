---
description: MediaPlayerNotificationは、プレイヤーのステータスに関連する情報を提供します。
title: 通知内容
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# 通知内容{#notification-content}

MediaPlayerNotificationは、プレイヤーのステータスに関連する情報を提供します。

TVSDKは、`MediaPlayerNotification`通知の時系列リストを提供します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * INFO、WARN、またはERRORを入力します。
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキー/値のペア。例えば、`URL`という名前のキーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与える別の `MediaPlayerNotification` オブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログ記録やグラフィカル表現のためにリモートサーバーに送信したりできます。
