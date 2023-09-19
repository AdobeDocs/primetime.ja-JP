---
title: 監視
description: 監視
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 監視{#monitoring}

個別化サーバーとキー生成サーバーにはそれぞれステータスページがあり、このページを使用してサーバーの正常性を判断できます。

* **個別化ステータスページ：** [!DNL https://SERVER:PORT/flashaccess/status]

   * アプリサーバーが実行中で、アプリがキー生成サーバーに対してGETリクエストを実行できる場合は、「Alive」を報告します
   * ページで「Alive」が表示されるか、何も表示されません。 アプリケーションに関する情報が表示されないので、このページはファイアウォールの外部からの監視に使用できます。

* **キー生成ステータスページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * アプリサーバーが実行中の場合は「Alive」と報告する
   * すべてのキー生成 URL は、内部でのみアクセス可能である必要があります

* **個別化の統計ページ：** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * 提供されたリクエスト数やキャッシュで使用可能なキー数など、個別化サーバーに関する統計が含まれます
   * このページは、内部でのみアクセス可能である必要があります

* **キー生成統計ページ：** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * 提供された要求数やディスク上で使用可能なキーファイル数など、キー生成サーバーに関する統計が含まれます
   * すべてのキー生成 URL は、内部でのみアクセス可能である必要があります
