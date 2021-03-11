---
description: Adobeでは、設定ファイルに変更を加える場合、サーバを開始する前にConfiguration Validatorユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生します。
title: 設定バリデーター
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 構成バリデーター{#configuration-validator}

Adobeでは、設定ファイルに変更を加える場合、サーバを開始する前にConfiguration Validatorユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生します。

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

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XMLファイルが適切に形成され、設定ファイルのスキーマに準拠していることが確認されます。

グローバル設定ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-global.xml --global
```

テナント構成ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントベースの検証も実行できます。 スキーマとの適合性をチェックするだけでなく、この検証レベルでも、指定した値が有効であることが確認されます。 例えば、参照ファイルが存在することを確認します。

デプロイメントベースの検証は、次のレベルで実行できます。

* `Tenant`  — 特定のテナントの構成ファイルと資格情報を検証します。`<tenant1>`の設定を検証する場合は、次のように入力します。

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
   ```

* `Global`  — すべてのテナントのグローバル構成ファイルとテナント検証を検証します。グローバルなデプロイメントベースの検証を実行する場合は、次のように入力します。

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -g
   ```

