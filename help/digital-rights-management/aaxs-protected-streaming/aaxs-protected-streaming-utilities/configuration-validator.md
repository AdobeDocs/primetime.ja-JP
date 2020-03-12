---
seo-title: 設定バリデーター
title: 設定バリデーター
uuid: 60ebd35c-290a-4f08-9bd0-178903857149
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# 設定バリデーター {#configuration-validator}

設定ファイルに変更が加えられた場合は、サーバーを起動する前に、Configuration Validatorユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生する可能性があります。

バリデーターを実行するには、次のコマンドを使用します。

```
Validator.bat options  
```

または次のコマンドを実行します。

```
java -jar libs/flashaccess-validator.jar options 
```

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XMLファイルが適切に構成され、設定ファイルのスキーマに準拠していることが確認されます。 グローバル設定ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-global.xml --global
```

テナント構成ファイルに対してファイルベースの検証を実行するには、次のコマンドを実行します。

```
Validator --file path/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントベースの検証も実行できます。この検証レベルでは、スキーマに準拠しているかどうかを確認するだけでなく、指定した値が有効であるかどうかも確認されます（例えば、参照ファイルが存在するかどうかを確認するなど）。 デプロイメントベースの検証は、次の2つのレベルで実行できます。

* テナント — 特定のテナントの構成ファイルと資格情報を検証します。 「tenant1」の設定を検証するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* グローバル — すべてのテナントのグローバル構成ファイルとテナントの検証を検証します。 グローバルなデプロイメントベースの検証を実行するには、次のコマンドを実行します。

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```

