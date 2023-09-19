---
title: 設定バリデーター
description: 設定バリデーター
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 設定バリデーター {#configuration-validator}

Adobeは、設定ファイルに変更が加えられた場合には、サーバーを起動する前に、設定バリデーターユーティリティを実行することをお勧めします。 このユーティリティは、リクエストの処理中にエラーが発生する前に、ほとんどの設定エラーを早期に検出できます。

バリデーターを実行するには、次のコマンドを使用します。

```
Validator.bat options  
```

または次のコマンドを使用します。

```
java -jar libs/flashaccess-validator.jar options 
```

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XML ファイルが適切な形式で、設定ファイルスキーマに準拠していることが確認されます。 グローバル設定ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-global.xml --global
```

テナント設定ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントに基づいた検証も実行できます。また、スキーマに適合するかどうかを確認するだけでなく、指定された値が有効かどうかも確認します（例えば、参照されるファイルが存在するかどうかを確認します）。 デプロイメントベースの検証は、次の 2 つのレベルで実行できます。

* 「テナント」 — 特定のテナントの設定ファイルと資格情報を検証します。 「tenant1」の設定を検証するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* 「グローバル」 — すべてのテナントのグローバル設定ファイルおよびテナント検証を検証します。 グローバルデプロイメントベースの検証を実行するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```
