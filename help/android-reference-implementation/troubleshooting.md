---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---

# トラブルシューティング{#troubleshooting}

* API レベル 10 以前を実行している一部の古いデバイスでは、権限の問題が原因で、Logcat がログデバイスを開けません。 次の例外が表示されます。 `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **回避策：**

   1. 開く [!DNL AndroidManifest.xml] の下に [!DNL CatalogActivity] プロジェクトを作成します。

   1. 次の権限を [!DNL `AndroidManfest.xml`] ファイル：

      ```
      android.permission.READ_LOGS
      ```
