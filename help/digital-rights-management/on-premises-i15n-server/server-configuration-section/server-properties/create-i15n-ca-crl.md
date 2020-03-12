---
seo-title: 個別化CA CRLの作成
title: 個別化CA CRLの作成
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 個別化CA CRLの作成{#create-individualization-ca-crl}

この証明書失効リスト(CRL)配布ポイントは、個別化サーバーによって発行される各コンピューター証明書に含まれます。 ライセンスサーバーでのコンピューター証明書の検証中に、このCRLは証明書に一覧表示されている配布ポイントからダウンロードされ（または、既にダウンロードされている場合はキャッシュから読み取られ）、証明書が失効していないことを確認します。

>[!NOTE]
>
>CRL配布ポイントのURLを設定するには、フィールドを設定する必要があり [!DNL AdobeInitial.properties] ます `cert.machine.crldp` 。 この配布ポイントは、Primetime DRM *によって* 、有効性に関してチェックされません。 このURLが有効であることを確認する必要があります。 無効なURLによるエラーは、ライセンスサーバーから検証エラーが表示されるまで表示されません。

以下に、OpenSSLを使用して、ライセンスサーバーで使用できるCRLを作成するための簡単な手順の例を示します。 Production Individualization CAの秘密鍵証明書を取得した後は、これらの手順を安全な方法と環境で実行することをお勧めします。

1. 作業ディレクトリを、この配布に含まれ [!DNL create_crl] るディレクトリに変更します。
1. 個別化CAを同じディレ [!DNL pfx] クトリにコピー [!DNL create_crl] します。

   以降の手順では、個別化CA pfxに名前が付けられていることを前提としていま [!DNL i15n.pfx]す。 設定に合わせて調整します。
1. 個別化CAファイルの [!DNL pfx] 秘密鍵を抽出します。

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. 秘密鍵を形式に変換し [!DNL pksc8] ます。

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. CRLを生成します。

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   この例では、デフォルトの1か月の有効期間を持つCRLを作成します。 デフォルト値を上 `-crldays` 書きする `-crlhours` には、およびオプションを使用します。

   CRLを生成するには、で指 [!DNL index] 定され [!DNL crlnumber] たとファイルを使用しま [!DNL openssl.conf]す。 デフォルトでは、作業デ [!DNL demoCA] ィレクトリ内の場所が使用されます。 サンプ [!DNL index] ルとフ [!DNL crlnumber] ァイルは、指定されたディレクトリに含ま [!DNL demoCA] れます。

1. 前の手順で生成したCRLファイルを、ライセンスサーバーが到達可能な適切な場所(例：個別化サー [!DNL ROOT]バー)。
1. CRLを設定したら、ライセンスサーバーを再起動します。
