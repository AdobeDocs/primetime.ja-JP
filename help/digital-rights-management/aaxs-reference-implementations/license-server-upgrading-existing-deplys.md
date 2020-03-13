---
seo-title: 既存の配置のアップグレード
title: 既存の配置のアップグレード
uuid: 57e62a88-e541-435c-8274-7f1602548601
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 既存の配置のアップグレード {#upgrading-existing-deployments}

バージョン3.0 Reference Implementation License ServerまたはWatched Folder Packagerを実行しているサーバーをアップグレードするには、アプリケーションサーバーにデプロイされているファイルを、Adobe Access Reference Implementation Serverに含まれているファイルに置き換えます。 [!DNL .war]

参照実装ライセンスサーバーでドメイン登録を使用する場合は、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成するには、を実行しま `CreateSampleDB.sql`す。 既存のデータベースレコードを保持し、新しいテーブルを追加するには、次のテ `CreateSampleDB.sql`ーブルを作成するコマンドを開いて実行するだけです。

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

ドメインのサポートを使用するには、flashaccess-refimpl.propertiesに次のプロパティを追加する必要があります。

* `HandlerConfiguration.DomainCAs.n` または `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` および、 `DomainRegistrationHandler.ServerCredential.password`または `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

iOSクライアントへのリモートキー配信をサポー [!DNL flashaccess-refimpl.properties] トするには、次のプロパティをに追加する必要があります。

* `HandlerConfiguration.KeyServerCertificate` または `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

