---
seo-title: 証明書の更新
title: 証明書の更新
uuid: 12a560b0-966b-424e-bfe5-22e9c10d8667
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# 証明書の更新{#renew-certificates}

Adobe Primetime DRM SDKの設定に基づく、次の証明書更新の制限に注意する必要があります。

* Primetime DRM実稼働SDK

   サポート契約を購入すると、Primetime DRM Production SDKの初期の無料証明書セットがアドビから提供されます。 サポート契約がない場合は、2年間有効な更新証明書のセットを購入できます。
* Primetime DRM評価SDK

   このSDKに設定された証明書は1年間有効で、更新できません。
* Primetime DRM体験版SDK

   Primetime DRM体験版SDKは3か月間有効で、アドビは1組の無料の更新証明書を提供しています。

## 新しい証明書の実装と既存のコンテンツに対する古い証明書の使用 {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Primetime DRMでは、以前の（または期限切れの）パッケージ化された証明書でパッケージ化されたコンテンツのライセンスの発行をライセンスサーバーに許可できます。 以前にパッケージ化されたコンテンツからのライセンス要求を受け入れるようにサーバーを設定するには、古い証明書をサーバーに提供し、古い証明書を見つける場所をサーバーが認識できるようにサーバーの設定ファイルを更新します。 詳しくは、「Adobe Primetime DRM SDKを使用したコ *ンテンツの保護」の「Adobe発行の証明書の期限が切れた場合の* 、 *証明書の更新の処理」を参照してください*。

サーバーアプリケーションがPrimetime DRMリファレンスの実装に基づいている場合は、サーバー側のプログラムを更新する必要はありません。 このファイル `flashaccess-refimpl.properties` には、追加のトランスポートおよびライセンスサーバー証明書を指定できるフィールドがあります。 証明書が1つだけの場合は、これらのプロパティを設定する必要はありません。 期限切れの証明書があり、ライセンス応答を発行する際にこれらの証明書を使用する場合は、設定ファイルにこれらの証明書を指定し、サーバーを再起動する必要があります。

古い証明書を指定するには、次のプロパティを使用します。

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

