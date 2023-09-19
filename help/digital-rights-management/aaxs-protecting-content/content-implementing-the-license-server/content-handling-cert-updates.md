---
title: 証明書発行の証明書が期限切れになった場合のAdobeの更新の処理
description: 証明書発行の証明書が期限切れになった場合のAdobeの更新の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# 証明書発行の証明書が期限切れになった場合のAdobeの更新の処理 {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Adobeから新しい証明書を取得する必要が生じる場合があります。 例えば、実稼動証明書の有効期限が切れた場合、評価証明書の有効期限が切れた場合、または評価から実稼動証明書に切り替えた場合などです。 証明書の有効期限が切れ、古い証明書を使用したコンテンツを再パッケージ化しない場合。 新旧の証明書と古い証明書の両方をライセンスサーバに認識させることができます。

次の手順を実行して、新しい証明書でサーバーを更新します。

1. （オプション）既存のポリシー更新リストまたは失効リストに新しいエントリを追加する場合は、新しい資格情報で署名し、古い証明書を使用して既存のファイルの署名を検証します。

   例えば、次のコマンドラインを使用して、別の資格情報を使用して署名された既存のポリシー更新リストにエントリを追加します。

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Java API を使用して、新しいポリシー更新リストまたは失効リストでライセンスサーバーを更新します。

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   または

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   参照実装では、使用するプロパティは次のようになります。 `HandlerConfiguration.RevocationList` および `HandlerConfiguration.PolicyUpdateList`. 署名の検証に使用する証明書も更新します。 `RevocationList.verifySignature.X509Certificate`.

1. 古い証明書を使用してパッケージ化されたコンテンツを使用するには、ライセンスサーバーに古いライセンスサーバー資格情報と新しいライセンスサーバー資格情報、およびトランスポート資格情報が必要です。 新しい証明書と古い証明書でライセンスサーバーを更新します。

   ライセンスサーバーの資格情報については、次の手順に従います。

   * 現在の秘密鍵証明書が `LicenseHandler` コンストラクタ：

      * 参照実装で、 `LicenseHandler.ServerCredential` プロパティ。
      * Adobe Access Server for Protected Streaming では、現在の秘密鍵証明書が、 `LicenseServerCredential` 要素を含める必要があります。

   * に現在の資格情報と古い資格情報が提供されていることを確認します。 `AsymmetricKeyRetrieval`

      * 参照実装で、 `LicenseHandler.ServerCredential` および `AsymmetricKeyRetrieval.ServerCredential. n` プロパティ。
      * Adobe Access Server for Protected Streaming では、古い資格情報が `LicenseServerCredential` 要素を含める必要があります。

   トランスポート資格情報の場合：

   * 現在の秘密鍵証明書が `HandlerConfiguration.setServerTransportCredential()` メソッド：

      * 参照実装で、 `HandlerConfiguration.ServerTransportCredential` プロパティ。
      * 保護されたストリーミング用のAdobe Access Serverでは、現在の秘密鍵証明書が、 `TransportCredential` 要素を含める必要があります。

   * 以前の資格情報がに提供されていることを確認します。 `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * 参照実装で、 `HandlerConfiguration.AdditionalServerTransportCredential. n` プロパティ。
      * 保護されたストリーミング用のAdobe Access Serverでは、これは `TransportCredential` 要素を含める必要があります。

1. パッケージツールを更新して、現在の資格情報でコンテンツをパッケージ化していることを確認します。 パッケージ化に最新のライセンスサーバー証明書、トランスポート証明書、および packager 証明書が使用されていることを確認します。
1. キーサーバーのライセンスサーバー証明書を更新するには、次の手順に従います。

   * Adobeアクセスキーサーバーテナント設定ファイルの資格情報を更新します。 古いキーサーバー資格情報と新しいキーサーバー資格情報の両方を flashaccess-keyserver-tenant.xml に含めます。
   * 現在の証明書が `HandlerConfiguration.setKeyServerCertificate()` メソッド。

      * 参照実装で、 `HandlerConfiguration.KeyServerCertificate` プロパティ。
      * 保護されたストリーミング用のAdobe Access Serverで、設定/テナント/証明書/キーサーバー要素を通じてでキーサーバーの証明書を指定します。
