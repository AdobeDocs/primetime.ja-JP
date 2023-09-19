---
description: flashaccess-global.xml 設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。
title: グローバル設定ファイル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# グローバル設定ファイル{#global-configuration-file}

flashaccess-global.xml 設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。

設定ファイルは、 [!DNL LicenseServer.ConfigRoot] ディレクトリ。

詳しくは、 [!DNL configs] ディレクトリを参照してください。

グローバル設定ファイルには、次の内容が含まれます。

* Caching — メモリ内の設定ファイルのキャッシュを制御します。

  詳しくは、 *設定ファイルの更新* を参照してください。
* 「ログ」 — ログ・レベルと、ログ・ファイルのロールの頻度を指定します。
* 「HSM パスワード」 — サーバーの資格情報を保存するために HSM が使用されている場合にのみ必要です。

Primetime DRM にあるグローバル設定ファイルの例のコメントを参照してください。 `<DVD>`\Adobe Primetime Protected Streaming 用の DRM サーバ\configs を参照してください。
