---
seo-title: アドビが発行した証明書の期限が切れた場合の証明書の更新の処理
title: アドビが発行した証明書の期限が切れた場合の証明書の更新の処理
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# アドビが発行した証明書の期限が切れた場合の証明書の更新の処理{#handling-certificate-updates-when-adobe-issued-certificates-expire}

アドビから新しい証明書を入手する必要がある場合があります。 例えば、評価版証明書の有効期限が切れた場合や、評価版証明書から実稼働版証明書に切り替えた場合に、実稼働版証明書の有効期限が切れます。 証明書の有効期限が切れ、古い証明書を使用するコンテンツを再パッケージ化しない場合は、License Serverに古い証明書と新しい証明書の両方を認識させることができます。

新しい証明書でサーバーを更新するには：

1. （オプション）既存のDRMポリシー更新リストまたは失効リストに新しいエントリを追加する場合、新しい秘密鍵証明書で署名し、古い証明書を使用して既存のファイルの署名を検証する必要があります。

   例えば、次のコマンドラインを使用して、別の秘密鍵証明書を使用して署名された既存のDRMポリシー更新リストにエントリを追加できます。

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. （オプション）Java APIを使用して、新しいDRMポリシー更新リストまたは失効リストでライセンスサーバーを更新します。

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   または：

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   参照実装で使用するプロパティは、と `HandlerConfiguration.RevocationList` です `HandlerConfiguration.PolicyUpdateList`。 また、署名の検証に使用する証明書を更新する必要があります。 `RevocationList.verifySignature.X509Certificate`.

1. 新しい証明書と古い証明書でライセンスサーバーを更新します。

   古い証明書を使用してパッケージ化されたコンテンツを使用する場合は、ライセンスサーバーが古いライセンスサーバーの資格情報と新しいライセンスサーバーの資格情報にアクセスできることを確認します。

   ライセンスサーバーの資格情報の場合：

   * 現在の秘密鍵証明書がコンストラクターに渡されていることを確認 `LicenseHandler` します。

      * 参照実装で、プロパティを使用して設定し `LicenseHandler.ServerCredential` ます。
      * Adobe Primetime DRM Server for Protected Streamingでは、現在の秘密鍵証明書が、flashaccess-tenant.xmlファイルの要素で指定されている最初の秘 `LicenseServerCredential` 密鍵証明書である必要があります。
   * 現在の資格情報と古い資格情報が `AsymmetricKeyRetrieval`

      * 参照実装で、およびプロパティを使用して `LicenseHandler.ServerCredential` 設定し `AsymmetricKeyRetrieval.ServerCredential. n` ます。

      * Primetime DRM Server for Protected Streamingでは、flashaccess-tenant.xmlファイル内の要素内の最初の秘密鍵証明書の後に、古い秘密鍵証明書 `LicenseServerCredential` が指定されています。
   トランスポート資格情報の場合：

   * 現在の秘密鍵証明書がメソッドに渡されていることを確認 `HandlerConfiguration.setServerTransportCredential()` します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.ServerTransportCredential` ます。
      * 保護されたストリーミングのPrimetime DRMサーバーでは、現在の秘密鍵証明書がファイル内の要素で指定された最初の秘密鍵証明書 `TransportCredential` である必要があ [!DNL flashaccess-tenant.xml] ります。
   * 古い秘密鍵証明書が `HandlerConfiguration.setAdditionalServerTransportCredentials`()に提供されていることを確認します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.AdditionalServerTransportCredential. n` ます。
      * 保護されたストリーミングのPrimetime DRMサーバーでは、flashaccess-tenant.xmlファイル内の要素内の最初の `TransportCredential` 秘密鍵証明書の後に指定されます。




1. パッケージ化ツールを更新し、現在の資格情報でコンテンツをパッケージ化していることを確認します。 パッケージ化に最新のライセンスサーバー証明書、トランスポート証明書、およびパッケージャーの証明書が使用されていることを確認します。
1. 次の手順に従って、キーサーバーのライセンスサーバー証明書を更新します。

   * flashaccess-keyserver-tenant.xmlに古いキーサーバーの資格情報と新しいキーサーバーの資格情報の両方を含めて、Adobe Primetime DRM Key Serverテナント設定ファイルの資格情報を更新します。
   * 現在の証明書がメソッドに渡されていることを確認 `HandlerConfiguration.setKeyServerCertificate()` します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.KeyServerCertificate` ます。
      * Primetime DRM Server for Protected Streamingで、Configuration/Tenant/Certificates/KeyServer要素を使用して、にキーサーバーの証明書を指定します。

