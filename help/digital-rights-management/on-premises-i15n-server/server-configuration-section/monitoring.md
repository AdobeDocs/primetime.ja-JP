---
seo-title: 監視
title: 監視
uuid: ee62c55f-0d44-40f4-a2c7-39456f4d3d99
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# 監視{#monitoring}

個別化サーバーとキー生成サーバーにはそれぞれステータスページがあり、このページを使用してサーバーの正常性を判断できます。

* **個別化ステータスページ：** [!DNL https://SERVER:PORT/flashaccess/status]

   * アプリサーバーが実行中で、アプリケーションがキー生成サーバーにGETリクエストを行える場合は、「Alive」とレポートします。
   * ページは「生きている」か何も報告しません。 アプリケーションに関する情報が表示されないので、このページはファイアウォールの外部からの監視に使用できます。

* **キー生成ステータスページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * アプリサーバーが実行中の場合は「Alive」と報告
   * すべてのキー生成URLは、内部でのみアクセス可能である必要があります

* **個別化の統計ページ：** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * 提供された要求数やキャッシュで使用可能なキー数など、個別化サーバーに関する統計が含まれます
   * このページは内部でのみアクセス可能である必要があります

* **キー生成統計ページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * 提供された要求の数や、ディスク上で使用可能なキーファイルの数など、キー生成サーバーに関する統計が含まれます
   * すべてのキー生成URLは、内部でのみアクセス可能である必要があります

