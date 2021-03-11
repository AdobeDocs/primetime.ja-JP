---
title: 証明書の更新
description: 証明書の更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# 証明書を更新{#renew-certificates}

Adobe PrimetimeDRM SDKの設定に基づく、次の証明書更新の制限事項に注意する必要があります。

* Primetime DRM実稼働SDK

   サポート契約を購入すると、Primetime DRM Production SDK用の初期無料証明書のセットがAdobeによって提供されます。 サポート契約を締結していない場合は、2年間有効な更新証明書のセットを購入できます。
* Primetime DRM評価SDK

   このSDKに設定された証明書は1年間有効で、更新できません。
* Primetime DRM体験版SDK

   Primetime DRM体験版SDKは3か月間有効で、Adobeは1組の無料更新証明書を提供します。

## 新しい証明書の実装と既存のコンテンツに対する古い証明書の使用{#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Primetime DRMでは、以前（または期限切れの）パッケージャーの証明書を使用してパッケージ化されたコンテンツのライセンスの発行をライセンスサーバーに許可できます。 以前にパッケージ化されたコンテンツからのライセンス要求を受け入れるようにサーバーを設定するには、古い証明書をサーバーに提供し、古い証明書を見つける場所がサーバーに認識されるようにサーバーの設定ファイルを更新します。 詳しくは、*Adobe発行証明書の有効期限が切れた場合の証明書更新の処理*&#x200B;について(「*Adobe PrimetimeDRM SDKを使用したコンテンツの保護*」)を参照してください。

サーバーアプリケーションがPrimetime DRM Referenceの実装に基づいている場合は、サーバー側プログラムを更新する必要はありません。 `flashaccess-refimpl.properties`ファイルには、追加のトランスポートおよびライセンスサーバー証明書を指定できるフィールドがあります。 証明書が1つだけの場合は、これらのプロパティを設定する必要はありません。 期限切れの証明書があり、ライセンス応答を発行するときにこれらの証明書を使用する場合は、これらの証明書を設定ファイルに指定し、サーバーを再起動する必要があります。

古い証明書を指定するには、次のプロパティを使用します。

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

