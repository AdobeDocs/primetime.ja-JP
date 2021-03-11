---
title: Adobeが発行した証明書の期限が切れた場合の証明書の更新処理
description: Adobeが発行した証明書の期限が切れた場合の証明書の更新処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Adobeが発行した証明書の期限が切れた場合に証明書の更新を処理する{#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Adobeから新しい証明書を取得する必要がある場合があります。 例えば、実稼働版証明書の有効期限が切れた場合、評価版証明書の有効期限が切れた場合、または評価版証明書から実稼働版証明書に切り替えた場合などです。 証明書の有効期限が切れた場合に、古い証明書を使用したコンテンツを再パッケージ化しないようにします。 古い証明書と新しい証明書の両方をLicense Serverに認識させることができます。

新しい証明書でサーバーを更新するには、次の手順に従います。

1. （オプション）既存のポリシー更新リストまたは失効リストに新しいエントリを追加する場合は、新しい資格情報を使用して署名し、古い証明書を使用して既存のファイルの署名を検証してください。

   例えば、次のコマンドラインを使用して、別の秘密鍵証明書を使用して署名された既存のポリシー更新リストにエントリを追加します。

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Java APIを使用して、新しいポリシー更新リストまたは失効リストでライセンスサーバーを更新します。

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   または

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   参照実装で使用するプロパティは、`HandlerConfiguration.RevocationList`と`HandlerConfiguration.PolicyUpdateList`です。 署名の検証に使用する証明書も更新します。`RevocationList.verifySignature.X509Certificate`.

1. 古い証明書を使用してパッケージ化されたコンテンツを使用するには、ライセンスサーバーに古い資格情報と新しいライセンスサーバーの資格情報およびトランスポート資格情報が必要です。 新しい証明書と古い証明書でライセンスサーバーを更新します。

   ライセンスサーバー資格情報の場合：

   * 現在の秘密鍵証明書が`LicenseHandler`コンストラクターに渡されていることを確認します。

      * 参照実装では、`LicenseHandler.ServerCredential`プロパティを使用して設定します。
      * 保護ストリーミング用Adobe Access Serverでは、現在の秘密鍵証明書は、flashaccess-tenant.xmlファイルの`LicenseServerCredential`要素で指定されている最初の秘密鍵証明書である必要があります。
   * 現在の資格情報と古い資格情報が`AsymmetricKeyRetrieval`に提供されていることを確認します

      * 参照実装では、`LicenseHandler.ServerCredential`プロパティと`AsymmetricKeyRetrieval.ServerCredential. n`プロパティを使用して設定します。
      * 保護ストリーミング用Adobe Access Serverでは、flashaccess-tenant.xmlファイルの`LicenseServerCredential`要素の最初の秘密鍵証明書の後に古い秘密鍵証明書が指定されています。

   トランスポート資格情報の場合：

   * 現在の秘密鍵証明書が`HandlerConfiguration.setServerTransportCredential()`メソッドに渡されていることを確認します。

      * 参照実装では、`HandlerConfiguration.ServerTransportCredential`プロパティを使用して設定します。
      * 保護されたストリーミング用Adobe Access Serverでは、現在の秘密鍵証明書は、flashaccess-tenant.xmlファイルの`TransportCredential`要素で指定されている最初の秘密鍵証明書である必要があります。
   * 古い秘密鍵証明書が`HandlerConfiguration.setAdditionalServerTransportCredentials`()に提供されていることを確認します。

      * 参照実装で、`HandlerConfiguration.AdditionalServerTransportCredential. n`プロパティを使用して設定します。
      * 保護されたストリーミング用Adobe Access Serverでは、flashaccess-tenant.xmlファイルの`TransportCredential`要素の最初の秘密鍵証明書の後に指定します。




1. パッケージ化ツールを更新し、現在の資格情報でコンテンツをパッケージ化していることを確認します。 パッケージ化には、最新のライセンスサーバー証明書、トランスポート証明書、およびPackagerの秘密鍵証明書が使用されていることを確認してください。
1. キーサーバーのライセンスサーバー証明書を更新するには：

   * Adobeアクセスキーサーバーのテナント構成ファイルの資格情報を更新します。 flashaccess-keyserver-tenant.xmlに、古いキーサーバー資格情報と新しいキーサーバー資格情報の両方を含めます。
   * 現在の証明書が`HandlerConfiguration.setKeyServerCertificate()`メソッドに渡されていることを確認します。

      * 参照実装では、`HandlerConfiguration.KeyServerCertificate`プロパティを使用して設定します。
      * 保護ストリーミング用Adobe Access Serverで、Configuration/Tenant/Certificates/KeyServer要素を使用して、でキーサーバーの証明書を指定します。

