---
description: 設定ファイルに変更を加える場合は、サーバーを起動する前に、設定バリデーターユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生する可能性があります。
seo-description: 設定ファイルに変更を加える場合は、サーバーを起動する前に、設定バリデーターユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生する可能性があります。
seo-title: 設定バリデーター
title: 設定バリデーター
uuid: 7b44919a-0319-4675-95e2-ad1ad72ec0cb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 設定バリデーター{#configuration-validator}

設定ファイルに変更を加える場合は、サーバーを起動する前に、設定バリデーターユーティリティを実行することをお勧めします。 このユーティリティは、ほとんどの設定エラーを早期に検出してから、要求処理中にエラーが発生する可能性があります。

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

各ライセンスサーバー設定ファイルに対して、バリデーターはファイルベースの検証を実行できます。これにより、XMLファイルが適切な形式で、設定ファイルのスキーマに準拠していることが確認されます。

グローバル設定ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-global.xml --global
```

テナント構成ファイルに対してファイルベースの検証を実行するには、次のように入力します。

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

バリデーターは、デプロイメントベースの検証も実行できます。 この検証レベルでは、スキーマに準拠しているかどうかを確認するだけでなく、指定した値が有効であるかどうかも確認されます。 例えば、参照ファイルが存在することを確認します。

デプロイメントベースの検証は、次のレベルで実行できます。

* `Tenant` — 特定のテナントの構成ファイルと資格情報を検証します。 設定を検証する場合は、次のように入 `<tenant1>`力します。

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
   ```

* `Global` — すべてのテナントのグローバル構成ファイルとテナントの検証を検証します。 グローバルなデプロイメントベースの検証を実行する場合は、次のように入力します。

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -g
   ```

