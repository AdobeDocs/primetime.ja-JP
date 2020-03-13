---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーのプロパティファイル
title: ライセンスサーバーのプロパティファイル
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバーのプロパティファイル{#license-server-properties-file}

ライセンスサーバは、ファイル内に設定されたプロパティを参 [!DNL flashaccess-refimpl.properties] 照します。 特定の値の詳細や各プロパティの使用方法の詳細については、そのファイルを直接参照できます。 完全に機能するサンプルは、参照実装のデ [!DNL resources] ィレクトリ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`)にあります。

**資格情報** — プロパティファイルには、アドビが発行する資格情報の場所の設定が含まれます。 これらの秘密鍵証明書は、パスワードを含 [!DNL .pfx] むファイルで指定するか、HSMに保存される秘密鍵証明書のエイリアスとパスワードを指定できます。 Transport CredentialとLicense Serverの秘密鍵証明書に関連するプロパティを少なくとも設定する必要があります。 プロパティで指定したディレクトリを基準とした、秘密鍵証明書ファイルの場所を指定 `config.resourcesDirectory` します。

**Flash Media Rights Management Server** — このファイル `flashaccess-refimpl.properties` には、コンテンツのパッケージ化に関連するプロパティも含まれています。 これらのプロパティは、Flash Media Rights Management Server 1.xメタデータの変換にのみ使用されます。 このプロパティファイルの値を変更した後、変更を有効にするには、ライセンスサーバーを再起動します。
