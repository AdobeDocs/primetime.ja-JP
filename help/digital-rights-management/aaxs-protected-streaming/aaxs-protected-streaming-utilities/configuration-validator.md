---
title: 構成バリデーター
description: 構成バリデーター
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# 構成バリデーター{#configuration-validator}

Adobeでは、設定ファイルに変更が加えられた場合に、サーバを起動する前に、設定検証ユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生します。

バリデーターを実行するには、次のコマンドを使用します。

```
Validator.bat options  
```

または次のコマンドを実行します。

```
java -jar libs/flashaccess-validator.jar options 
```

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XMLファイルが適切に形成され、設定ファイルのスキーマに準拠していることが確認されます。 グローバル設定ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-global.xml --global
```

テナント構成ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントベースの検証も実行できます。スキーマとの適合性をチェックするだけでなく、このレベルの検証でも、指定した値が有効であるかどうかがチェックされます（例えば、参照ファイルが存在するかどうかが確認されます）。 デプロイメントベースの検証は、次の2つのレベルで実行できます。

* 「テナント」 — 特定のテナントの構成ファイルと資格情報を検証します。 「tenant1」の構成を検証するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* グローバル：すべてのテナントのグローバル構成ファイルとテナント検証を検証します。 グローバルなデプロイメントベースの検証を実行するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```

