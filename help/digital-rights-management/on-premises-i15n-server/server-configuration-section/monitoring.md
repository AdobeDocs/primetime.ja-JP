---
title: 監視
description: 監視
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 監視{#monitoring}

個別化サーバーとキー生成サーバーにはそれぞれステータスページがあり、このページを使用してサーバーの正常性を判断できます。

* **個別化ステータスページ：** [!DNL https://SERVER:PORT/flashaccess/status]

   * アプリサーバーが実行中で、アプリが主要生成サーバーにGETリクエストを行える場合は、「Alive」と報告します。
   * ページは、「生きている」か何も報告しません。 アプリケーションに関する情報が表示されないため、このページはファイアウォールの外部からの監視に使用できます。

* **キー生成ステータスページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * アプリケーションサーバーが実行中の場合に「アライブ」を報告
   * すべてのキー生成URLは、内部でのみアクセス可能である必要があります

* **個別化の統計ページ：** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * 提供された要求数やキャッシュで使用可能なキー数など、個別化サーバーに関する統計が含まれます
   * このページは内部でのみアクセス可能である必要があります

* **「Key Generation Statistics」ページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * 提供された要求数、ディスク上で使用可能なキーファイル数など、キー生成サーバーに関する統計情報が含まれます
   * すべてのキー生成URLは、内部でのみアクセス可能である必要があります

