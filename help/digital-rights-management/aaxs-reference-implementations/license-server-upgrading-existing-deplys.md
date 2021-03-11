---
title: 既存の配置のアップグレード
description: 既存の配置のアップグレード
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# 既存の配置をアップグレード{#upgrading-existing-deployments}

バージョン3.0 Reference Implementation License ServerまたはWatched Folder Packagerを実行しているサーバーをアップグレードするには、Application Serverにデプロイされている[!DNL .war]ファイルを、Adobeアクセスリファレンス実装サーバーに含まれているファイルに置き換えます。

参照実装ライセンスサーバーでドメイン登録を使用する場合は、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成するには、`CreateSampleDB.sql`を実行します。 既存のデータベースレコードを保持し、新しいテーブルを追加するには、`CreateSampleDB.sql`を開き、次のテーブルを作成するコマンドのみを実行します。

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

ドメインサポートを使用するには、flashaccess-refimpl.propertiesに次のプロパティを追加する必要があります。

* `HandlerConfiguration.DomainCAs.n` または  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` および `DomainRegistrationHandler.ServerCredential.password`、または  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

iOSクライアントへのリモートキー配信をサポートするには、次のプロパティを[!DNL flashaccess-refimpl.properties]に追加する必要があります。

* `HandlerConfiguration.KeyServerCertificate` または  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

