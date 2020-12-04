---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーのプロパティファイル
title: ライセンスサーバーのプロパティファイル
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# ライセンスサーバのプロパティファイル{#license-server-properties-file}

ライセンスサーバーは、[!DNL flashaccess-refimpl.properties]ファイルに設定されたプロパティを参照します。 特定の値の詳細や各プロパティの使用方法の詳細については、そのファイルを直接参照できます。 完全な機能を持つサンプルは、参照実装(`([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`)の[!DNL resources]ディレクトリにあります。

**資格情報**  — プロパティファイルには、Adobeが発行する秘密鍵証明書の場所の設定が含まれます。これらの秘密鍵証明書は、パスワードを持つ[!DNL .pfx]ファイルに指定するか、HSMに保存されている秘密鍵証明書のエイリアスとパスワードを指定できます。 Transport CredentialとLicense Server Credentialに関連するプロパティを少なくとも設定する必要があります。 `config.resourcesDirectory`プロパティで指定したディレクトリを基準に、秘密鍵証明書ファイルの場所を指定します。

**FlashメディアRights Managementサーバ**  — この `flashaccess-refimpl.properties` ファイルには、コンテンツのパッケージ化に関連するプロパティも含まれています。これらのプロパティは、FlashメディアRights ManagementServer 1.xメタデータ変換でのみ使用されます。 このプロパティファイルの値を変更した後、変更が有効になるように、ライセンスサーバーを再起動します。
