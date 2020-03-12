---
description: バージョン3.0 Reference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe Primetime DRM Reference Implementation Serverに含まれているファイルに置き換える必要があります。
seo-description: バージョン3.0 Reference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe Primetime DRM Reference Implementation Serverに含まれているファイルに置き換える必要があります。
seo-title: 既存のデプロイのアップグレード
title: 既存のデプロイのアップグレード
uuid: 1a40aae9-f639-41fa-b42d-cf8cdfcde694
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# 概要 {#upgrade-existing-deployments-overview}

バージョン3.0 Reference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe Primetime DRM Reference Implementation Serverに含まれているファイルに置き換える必要があります。

参照実装ライセンスサーバーでドメイン登録を使用するには、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成し、を実行する必要がありま `CreateSampleDB.sql`す。

データベース・レコードを保持し、新しい表を追加する手順は、次のとおりです。

1. 次のテー `CreateSampleDB.sql` ブルを作成するコマンドを開いて実行します。

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. ドメインサポートを使用するには、 [!DNL flashaccess-refimpl.properties] 次のプロパティをに追加します。

   * `HandlerConfiguration.DomainCAs.n` または `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` また `DomainRegistrationHandler.ServerCredential.password` は `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. iOSクライアントへのリモートキ [!DNL flashaccess-refimpl.properties] ー配信をサポートするため、に次のプロパティを追加します。

   * `HandlerConfiguration.KeyServerCertificate` または `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`