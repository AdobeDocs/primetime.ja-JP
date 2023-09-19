---
title: 証明書を更新
description: 証明書を更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 証明書を更新{#renew-certificates}

Adobe Primetime DRM SDK の設定に基づく、次の証明書の更新制限に注意する必要があります。

* Primetime DRM 実稼動 SDK

  Adobeは、サポート契約を購入した際に、Primetime DRM Production SDK 用の最初の無料証明書のセットを提供します。 サポート契約がない場合は、2 年間有効な更新証明書のセットを購入できます。
* Primetime DRM 評価 SDK

  この SDK の証明書セットは 1 年間有効で、更新できません。
* Primetime DRM 体験版 SDK

  Primetime DRM 体験版 SDK は 3 ヶ月間有効で、Adobeは 1 組の無料の更新証明書を提供しています。

## 新しい証明書を実装し、既存のコンテンツに古い証明書を使用する {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Primetime DRM では、以前の（または期限切れの）パッケージ化されたパッケージ化された（または期限切れの）パッケージ化されたコンテンツに対して、ライセンスサーバーがライセンスを発行することを許可できます。 以前にパッケージ化されたコンテンツからのライセンス要求を受け入れるようにサーバーを設定するには、古い証明書をサーバーに提供し、サーバーが古い証明書を見つける場所をサーバーが把握できるようにサーバーの設定ファイルを更新します。 詳しくは、 *証明書発行の証明書が期限切れになったときのAdobeの更新の処理* in *コンテンツの保護にAdobe Primetime DRM SDK を使用*.

サーバーアプリケーションが Primetime DRM 参照実装に基づいている場合、サーバー側プログラムを更新する必要はありません。 Adobe Analytics の `flashaccess-refimpl.properties` ファイルには、追加のトランスポートおよびライセンスサーバー証明書を指定できるフィールドがあります。 証明書が 1 つだけの場合、これらのプロパティを設定する必要はありません。 期限切れの証明書があり、ライセンス応答を発行する際にこれらの証明書を使用する場合は、構成ファイルにこれらの証明書を指定し、サーバーを再起動する必要があります。

古い証明書を指定するには、次のプロパティを使用します。

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`
