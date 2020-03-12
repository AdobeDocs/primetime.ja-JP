---
seo-title: トラブルシューティング
title: トラブルシューティング
uuid: b7a41ea7-86c5-442c-b751-86a9055c5e35
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# トラブルシューティング{#troubleshooting}

* APIレベル10以前を実行している一部の古いデバイスでは、権限の問題が原因で、ログデバイスを開けません。 次の例外が表示されます。回 `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied`**避策：**

   1. ワークス [!DNL AndroidManifest.xml] ペース内のプ [!DNL CatalogActivity] ロジェクトの下で開きます。

   1. ファイルに次の権限を追加 [!DNL `AndroidManfest.xml`] します。

      ```
      android.permission.READ_LOGS
      ```
