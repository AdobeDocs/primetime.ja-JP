---
description: バージョン 3.0 の Reference Implementation License Server または Watched Folder Packager をサポートするサーバーをアップグレードするには、アプリケーションサーバーにデプロイされている.war ファイルを、Adobe Primetime DRM Reference Implementation Server に含まれているファイルに置き換える必要があります。
title: 既存のデプロイメントのアップグレード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 概要 {#upgrade-existing-deployments-overview}

バージョン 3.0 の Reference Implementation License Server または Watched Folder Packager をサポートするサーバーをアップグレードするには、アプリケーションサーバーにデプロイされている.war ファイルを、Adobe Primetime DRM Reference Implementation Server に含まれているファイルに置き換える必要があります。

参照実装ライセンスサーバーでドメイン登録を使用するには、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成し、を実行する必要があります。 `CreateSampleDB.sql`.

データベース・レコードを保持し、新しい表を追加する手順は、次のとおりです。

1. 開く `CreateSampleDB.sql` 次のテーブルを作成するコマンドを実行します。

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. 次のプロパティをに追加します。 [!DNL flashaccess-refimpl.properties] ドメインサポートを使用するには、次の手順に従います。

   * `HandlerConfiguration.DomainCAs.n` または `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` および `DomainRegistrationHandler.ServerCredential.password` または `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. 次のプロパティをに追加します。 [!DNL flashaccess-refimpl.properties] iOSクライアントへのリモートキー配信をサポートするには：

   * `HandlerConfiguration.KeyServerCertificate` または `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
