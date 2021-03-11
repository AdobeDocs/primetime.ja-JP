---
title: Adobe発行の証明書の有効期限が切れた場合の証明書の更新の処理
description: Adobe発行の証明書の有効期限が切れた場合の証明書の更新の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Adobe発行の証明書の有効期限が切れた場合の証明書の更新の処理{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Adobeから新しい証明書を取得する必要がある場合があります。 例えば、評価用証明書の有効期限が切れた場合や、評価用証明書から実稼働用証明書に切り替えた場合に、実稼働用証明書の有効期限が切れます。 証明書の有効期限が切れたときに、古い証明書を使用するコンテンツを再パッケージ化しない場合は、新旧の証明書と古い証明書の両方をLicense Serverに認識させることができます。

サーバーを新しい証明書で更新するには：

1. （オプション）既存のDRMポリシー更新リストまたは失効リストに新しいエントリを追加する場合は、新しい資格情報を使用して署名し、古い証明書を使用して既存のファイルの署名を検証する必要があります。

   例えば、次のコマンドラインを使用して、別の秘密鍵証明書を使用して署名された既存のDRMポリシー更新リストにエントリを追加できます。

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. （オプション）Java APIを使用して、新しいDRMポリシー更新リストまたは失効リストでライセンスサーバーを更新します。

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   または

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   参照実装で使用するプロパティは、`HandlerConfiguration.RevocationList`と`HandlerConfiguration.PolicyUpdateList`です。 また、署名の検証に使用する証明書を更新する必要もあります。`RevocationList.verifySignature.X509Certificate`.

1. 新しい証明書と古い証明書でライセンスサーバーを更新します。

   古い証明書を使用してパッケージ化されたコンテンツを使用する場合は、ライセンスサーバーが古い資格情報と新しいライセンスサーバーの資格情報にアクセスでき、トランスポート資格情報も持っていることを確認してください。

   ライセンスサーバー資格情報の場合：

   * 現在の秘密鍵証明書が`LicenseHandler`コンストラクターに渡されていることを確認します。

      * 参照実装で、`LicenseHandler.ServerCredential`プロパティを使用して設定します。
      * 保護ストリーミング用のAdobe PrimetimeDRMサーバーでは、現在の秘密鍵証明書がflashaccess-tenant.xmlファイルの`LicenseServerCredential`要素で指定されている最初の秘密鍵証明書である必要があります。
   * 現在の資格情報と古い資格情報が`AsymmetricKeyRetrieval`に提供されていることを確認します

      * 参照実装で、`LicenseHandler.ServerCredential`プロパティと`AsymmetricKeyRetrieval.ServerCredential. n`プロパティを使用して設定します。

      * 保護ストリーミング用のPrimetime DRMサーバーでは、flashaccess-tenant.xmlファイルの`LicenseServerCredential`要素内の最初の秘密鍵証明書の後に古い秘密鍵証明書が指定されます。

   トランスポート資格情報の場合：

   * 現在の秘密鍵証明書が`HandlerConfiguration.setServerTransportCredential()`メソッドに渡されていることを確認します。

      * 参照実装で、`HandlerConfiguration.ServerTransportCredential`プロパティを使用して設定します。
      * 保護されたストリーミング用のPrimetime DRMサーバーでは、現在の秘密鍵証明書が[!DNL flashaccess-tenant.xml]ファイルの`TransportCredential`要素で指定されている最初の秘密鍵証明書である必要があります。
   * 古い秘密鍵証明書が`HandlerConfiguration.setAdditionalServerTransportCredentials`()に提供されていることを確認します。

      * 参照実装で、`HandlerConfiguration.AdditionalServerTransportCredential. n`プロパティを使用して設定します。
      * 保護されたストリーミング用のPrimetime DRMサーバーでは、flashaccess-tenant.xmlファイルの`TransportCredential`要素内の最初の秘密鍵証明書の後に指定します。




1. パッケージ化ツールを更新し、現在の資格情報でコンテンツをパッケージ化していることを確認します。 パッケージ化には、最新のライセンスサーバー証明書、トランスポート証明書、およびPackagerの秘密鍵証明書が使用されていることを確認してください。
1. 次の手順に従って、キーサーバーのライセンスサーバー証明書を更新します。

   * flashaccess-keyserver-tenant.xmlに古いキーサーバー資格情報と新しいキーサーバー資格情報の両方を含めて、Adobe PrimetimeDRMキーサーバーテナント設定ファイルの秘密鍵証明書を更新します。
   * 現在の証明書が`HandlerConfiguration.setKeyServerCertificate()`メソッドに渡されていることを確認します。

      * 参照実装で、`HandlerConfiguration.KeyServerCertificate`プロパティを使用して設定します。
      * 保護されたストリーミング用のPrimetime DRMサーバーで、Configuration/Tenant/Certificates/KeyServer要素を使用して、でキーサーバーの証明書を指定します。

