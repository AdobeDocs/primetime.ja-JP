---
title: 既存のデプロイメントのアップグレード
description: 既存のデプロイメントのアップグレード
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# 既存のデプロイメントのアップグレード {#upgrading-existing-deployments}

バージョン 3.0 参照実装ライセンスサーバーまたは監視フォルダーパッケージャーを実行しているサーバーをアップグレードするには、 [!DNL .war] アプリケーション・サーバー上にデプロイされたファイルで、Adobe・アクセス参照実装サーバーに含まれるファイル。

参照実装ライセンスサーバーでドメイン登録を使用する場合は、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成するには、を実行します。 `CreateSampleDB.sql`. 既存のデータベースレコードを保持し、新しいテーブルを追加するには、を開きます。 `CreateSampleDB.sql`コマンドを実行して、次のテーブルを作成します。

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

ドメインサポートを使用するには、以下のプロパティを flashaccess-refimpl.properties に追加する必要があります。

* `HandlerConfiguration.DomainCAs.n` または `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` および `DomainRegistrationHandler.ServerCredential.password`または `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

次のプロパティをに追加する必要があります。 [!DNL flashaccess-refimpl.properties] iOSクライアントへのリモートキー配信をサポートするには：

* `HandlerConfiguration.KeyServerCertificate` または `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
