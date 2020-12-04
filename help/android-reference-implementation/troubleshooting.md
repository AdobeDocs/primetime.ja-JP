---
seo-title: トラブルシューティング
title: トラブルシューティング
uuid: b7a41ea7-86c5-442c-b751-86a9055c5e35
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
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
