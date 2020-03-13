---
seo-title: アドビが発行した証明書の期限が切れた場合の証明書の更新の処理
title: アドビが発行した証明書の期限が切れた場合の証明書の更新の処理
uuid: 5151ef15-daf6-4fb3-bf83-25ebac1d003b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# アドビが発行した証明書の期限が切れた場合の証明書の更新の処理 {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

アドビから新しい証明書を取得する必要が生じる場合があります。 例えば、実稼働版証明書の有効期限が切れた場合、評価版証明書の有効期限が切れた場合、または評価版証明書から実稼働版証明書に切り替えた場合などです。 証明書の有効期限が切れ、古い証明書を使用したコンテンツを再パッケージ化しない場合。 古い証明書と新しい証明書の両方をLicense Serverに認識させることができます。

次の手順に従って、新しい証明書でサーバーを更新します。

1. （オプション）既存のポリシー更新リストまたは失効リストに新しいエントリを追加する場合は、新しい資格情報で署名し、古い証明書を使用して既存のファイルの署名を検証します。

   例えば、次のコマンドラインを使用して、別の秘密鍵証明書を使用して署名された既存のポリシー更新リストにエントリを追加します。

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Java APIを使用して、新しいポリシー更新リストまたは失効リストでライセンスサーバーを更新します。

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   または：

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   参照実装で使用するプロパティは、と `HandlerConfiguration.RevocationList` です `HandlerConfiguration.PolicyUpdateList`。 署名の検証に使用する証明書も更新します。 `RevocationList.verifySignature.X509Certificate`.

1. 古い証明書を使用してパッケージ化されたコンテンツを使用するには、ライセンスサーバーで古いライセンスサーバー資格情報と新しいライセンスサーバー資格情報が必要です。 新しい証明書と古い証明書でライセンスサーバーを更新します。

   ライセンスサーバーの資格情報の場合：

   * 現在の秘密鍵証明書がコンストラクターに渡されていることを確認 `LicenseHandler` します。

      * 参照実装で、プロパティを使用して設定し `LicenseHandler.ServerCredential` ます。
      * 保護されたストリーミング用のAdobe Access Serverでは、現在の秘密鍵証明書が、flashaccess-tenant.xmlファイルの要素で指定さ `LicenseServerCredential` れた最初の秘密鍵証明書である必要があります。
   * 現在の資格情報と古い資格情報が `AsymmetricKeyRetrieval`

      * 参照実装で、およびプロパティを使用して設 `LicenseHandler.ServerCredential` 定し `AsymmetricKeyRetrieval.ServerCredential. n` ます。
      * Adobe Access Server for Protected Streamingでは、flashaccess-tenant.xmlファイル内の要素内の最初の秘密鍵証明書の後に、古い秘密鍵証明書 `LicenseServerCredential` が指定されています。
   トランスポート資格情報の場合：

   * 現在の秘密鍵証明書がメソッドに渡されていることを確認 `HandlerConfiguration.setServerTransportCredential()` します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.ServerTransportCredential` ます。
      * 保護されたストリーミング用のAdobe Access Serverでは、現在の秘密鍵証明書が、flashaccess-tenant.xmlファイルの要素で指定さ `TransportCredential` れた最初の秘密鍵証明書である必要があります。
   * 古い秘密鍵証明書が `HandlerConfiguration.setAdditionalServerTransportCredentials`()に提供されていることを確認します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.AdditionalServerTransportCredential. n` ます。
      * 保護されたストリーミング用のAdobe Access Serverでは、flashaccess-tenant.xmlファイル内の要素内の最初の `TransportCredential` 秘密鍵証明書の後に指定されます。




1. パッケージ化ツールを更新し、現在の資格情報でコンテンツをパッケージ化していることを確認します。 パッケージ化に最新のライセンスサーバー証明書、トランスポート証明書、およびパッケージャーの証明書が使用されていることを確認します。
1. キーサーバーのライセンスサーバー証明書を更新するには：

   * Adobe Access Key Serverテナント設定ファイルの資格情報を更新します。 flashaccess-keyserver-tenant.xmlに、古いキーサーバー資格情報と新しいキーサーバー資格情報の両方を含めます。
   * 現在の証明書がメソッドに渡されていることを確認 `HandlerConfiguration.setKeyServerCertificate()` します。

      * 参照実装で、プロパティを使用して設定し `HandlerConfiguration.KeyServerCertificate` ます。
      * Protected StreamingのAdobe Access Serverで、Configuration/Tenant/Certificates/KeyServer要素を使用して、にキーサーバーの証明書を指定します。

