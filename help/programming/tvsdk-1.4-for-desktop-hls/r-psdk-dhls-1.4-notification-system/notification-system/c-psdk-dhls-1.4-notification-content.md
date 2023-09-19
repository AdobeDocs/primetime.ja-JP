---
description: MediaPlayerNotification は、プレーヤーのステータスに関連する情報を提供します。
title: 通知コンテンツ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 通知コンテンツ{#notification-content}

MediaPlayerNotification は、プレーヤーのステータスに関連する情報を提供します。

TVSDK は、 `MediaPlayerNotification` 通知。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * INFO、WARN、ERROR のいずれかを入力
   * `code`：通知の数値表現。
   * `name`：人間が判読できる、通知の説明（SEEK_ERROR など）
   * `metadata`：通知に関する関連情報を含むキーと値のペア。 例えば、 `URL` は通知に関連する URL を示す値を提供します。

   * `innerNotification`：別のへの参照 `MediaPlayerNotification` オブジェクトを直接表示します。

この情報をローカルに保存して後で分析したり、ログ記録やグラフィカル表示のためにリモートサーバーに送信したりできます。
