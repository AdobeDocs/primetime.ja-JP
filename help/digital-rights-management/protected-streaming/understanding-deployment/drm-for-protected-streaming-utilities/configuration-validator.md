---
description: Adobeでは、設定ファイルに変更を加える場合、サーバを起動する前に Configuration Validator ユーティリティを実行することをお勧めします。 このユーティリティは、リクエストの処理中にエラーが発生する前に、ほとんどの設定エラーを早期に検出できます。
title: 設定バリデーター
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 設定バリデーター{#configuration-validator}

Adobeでは、設定ファイルに変更を加える場合、サーバを起動する前に Configuration Validator ユーティリティを実行することをお勧めします。 このユーティリティは、リクエストの処理中にエラーが発生する前に、ほとんどの設定エラーを早期に検出できます。

バリデーターを実行するには、次のように入力します。

```
Validator.bat  
<i class="+ topic ph hi-d="" i "="">
  options  
</i class="+ topic>
```

または

```
java -jar libs/flashaccess-validator.jar  
<i class="+ topic ph hi-d="" i "="">
  options 
</i class="+ topic>
```

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XML ファイルの形式が正しく、設定ファイルスキーマに準拠していることが確認されます。

グローバル設定ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-global.xml --global
```

テナント設定ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントベースの検証も実行できます。 この検証レベルでは、スキーマとの適合を確認するだけでなく、指定した値が有効であることも確認します。 例えば、参照ファイルが確実に存在するようにします。

デプロイメントベースの検証は、次のレベルで実行できます。

* `Tenant`  — 特定のテナントの設定ファイルと資格情報を検証します。 の設定を検証する場合は、 `<tenant1>`、タイプ：

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
  ```

* `Global`  — すべてのテナントのグローバル設定ファイルとテナント検証を検証します。 グローバルデプロイメントベースの検証を実行する場合は、次のように入力します。

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -g
  ```
