---
description: バージョン3.0のReference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe PrimetimeDRM Reference Implementation Serverに含まれるファイルに置き換える必要があります。
seo-description: バージョン3.0のReference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe PrimetimeDRM Reference Implementation Serverに含まれるファイルに置き換える必要があります。
seo-title: 既存の展開のアップグレード
title: 既存の展開のアップグレード
uuid: 1a40aae9-f639-41fa-b42d-cf8cdfcde694
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# 概要{#upgrade-existing-deployments-overview}

バージョン3.0のReference Implementation License ServerまたはWatched Folder Packagerをサポートするサーバーをアップグレードするには、Application Serverにデプロイされた.warファイルを、Adobe PrimetimeDRM Reference Implementation Serverに含まれるファイルに置き換える必要があります。

参照実装ライセンスサーバーでドメイン登録を使用するには、新しいデータベーステーブルがいくつか必要です。 参照実装データベース全体を再作成し、`CreateSampleDB.sql`を実行する必要があります。

データベース・レコードを保持し、新しい表を追加する手順は、次のとおりです：

1. `CreateSampleDB.sql`を開き、次のテーブルを作成するコマンドを実行します。

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. ドメ追加インサポートを使用するには、[!DNL flashaccess-refimpl.properties]に次のプロパティを指定します。

   * `HandlerConfiguration.DomainCAs.n` または  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` および `DomainRegistrationHandler.ServerCredential.password` または  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. iOSクライアント追加に対するリモートキー配信をサポートするために、[!DNL flashaccess-refimpl.properties]に対する次のプロパティを指定します。

   * `HandlerConfiguration.KeyServerCertificate` または  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`