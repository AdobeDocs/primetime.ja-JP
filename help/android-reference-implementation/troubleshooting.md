---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---


# トラブルシューティング{#troubleshooting}

* APIレベル10以前を実行している古いデバイスの一部では、権限の問題が原因でログデバイスを開けません。 次の例外が表示されます。`java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **回避策：**

   1. ワークスペースの[!DNL CatalogActivity]プロジェクトの下の[!DNL AndroidManifest.xml]を開きます。

   1. 追加[!DNL `AndroidManfest.xml`]ファイルに対する次の権限です。

      ```
      android.permission.READ_LOGS
      ```
