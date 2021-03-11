---
title: グローバル設定ファイル
description: グローバル設定ファイル
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# グローバル構成ファイル{#global-configuration-file}

flashaccess-global.xml設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。 このファイルは、*LicenseServer.ConfigRoot*&#x200B;にある必要があります。 グローバル設定ファイルの例については、configsディレクトリを参照してください。 グローバル設定ファイルには、次の情報が含まれます。

* 「キャッシュ」 — メモリ内の設定ファイルのキャッシュを制御します。 キャッシュ設定の詳細は、「設定ファイルの更新」を参照してください。
* 「ログ」 — ログ・レベルと、ログ・ファイルをロールする頻度を指定します。
* 「HSMパスワード」 — サーバー秘密鍵証明書の保存にHSMが使用される場合にのみ必要です。

詳しくは、`<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs`にあるグローバル設定ファイルの例のコメントを参照してください。
