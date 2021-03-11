---
title: 個別化CA CRLの作成
description: 個別化CA CRLの作成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# 個別化CA CRL{#create-individualization-ca-crl}の作成

この証明書失効リスト(CRL)配布ポイントは、個別化サーバーによって発行される各マシン証明書に含まれます。 ライセンスサーバーでのコンピューター証明書の検証中に、このCRLは証明書に一覧表示されている配布ポイントからダウンロードされ（または既にダウンロードされている場合はキャッシュから読み取り）、証明書が失効していないかどうかを確認します。

>[!NOTE]
>
>CRL配布ポイントのURLを設定するには、[!DNL AdobeInitial.properties] `cert.machine.crldp`フィールドを設定する必要があります。 この配布ポイントは、Primetime DRMによって有効性の確認が&#x200B;*行われません*。 このURLが有効であることを確認する必要があります。 無効なURLによるエラーは、検証エラーがライセンスサーバーから表示されるまで表示されません。

以下に、OpenSSLを使用してライセンスサーバーで使用できるCRLを作成する場合のサンプル手順を示します。 Production Indivicalization CAの秘密鍵証明書が取得されたら、これらの手順を安全な方法と環境で実行することをお勧めします。

1. この配布物に含まれる[!DNL create_crl]ディレクトリに作業ディレクトリを変更します。
1. 個別化CA [!DNL pfx]を同じ[!DNL create_crl]ディレクトリにコピーします。

   以降の手順では、個別化CA pfxの名前が[!DNL i15n.pfx]であることを前提としています。 設定に合わせて調整します。
1. 個別化CA [!DNL pfx]ファイルの秘密鍵を抽出します。

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. 秘密鍵を[!DNL pksc8]形式に変換します。

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. CRLを生成します。

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   次の使用例は、デフォルトの1か月の有効期間を持つCRLを作成します。 `-crldays`および`-crlhours`オプションを使用して、デフォルト値を上書きします。

   CRLを生成するには、[!DNL openssl.conf]で指定されている[!DNL index]と[!DNL crlnumber]ファイルを使用します。 デフォルトでは、作業ディレクトリ内の[!DNL demoCA]の場所が使用されます。 指定された[!DNL demoCA]ディレクトリには、サンプル[!DNL index]ファイルと[!DNL crlnumber]ファイルが含まれています。

1. 前の手順で生成したCRLファイルを、ライセンスサーバーが到達可能な適切な場所にデプロイします(例：個別化サーバー[!DNL ROOT])。
1. CRLが配置されたら、ライセンスサーバーを再起動します。
