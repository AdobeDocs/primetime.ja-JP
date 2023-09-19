---
title: 個別化 CA CRL の作成
description: 個別化 CA CRL の作成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 個別化 CA CRL の作成{#create-individualization-ca-crl}

この証明書失効リスト (CRL) 配布ポイントは、個別化サーバーが発行した各コンピュータ証明書に含まれます。 ライセンスサーバーでのコンピューター証明書の検証中に、この CRL は証明書に一覧表示されている配布ポイントからダウンロードされ（既にダウンロードされている場合はキャッシュから読み取られ）、証明書が失効されていないか確認されます。

>[!NOTE]
>
>CRL 配布ポイントの URL を設定するには、 [!DNL AdobeInitial.properties] `cert.machine.crldp` フィールドに入力します。 この配分ポイントは、 *not* Primetime DRM によって有効性が確認されました。 この URL が有効であることを確認する必要があります。 無効な URL によって生じるエラーは、ライセンスサーバーから検証エラーが表示されるまで、表示されません。

以下に、OpenSSL を使用してライセンスサーバーが使用できる CRL を作成する手順の例を示します。 Adobeでは、実稼動用の個別化 CA の資格情報を取得した後、これらの手順を安全な方法と環境で実行することをお勧めします。

1. 作業ディレクトリを [!DNL create_crl] このディストリビューションに含まれるディレクトリ。
1. 個別化 CA をコピーする [!DNL pfx] 同様に [!DNL create_crl] ディレクトリ。

   以降の手順では、個別化 CA の pfx に名前が付けられていることを前提としています [!DNL i15n.pfx]. 設定に応じてを調整します。
1. 個別化 CA の抽出 [!DNL pfx] ファイルの秘密鍵。

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. 秘密鍵をに変換します。 [!DNL pksc8] 形式を使用します。

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. CRL を生成します。

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   次の使用例は、デフォルトの有効期間が 1 か月の CRL を作成します。 以下を使用します。 `-crldays` および `-crlhours` デフォルト値を上書きするオプションです。

   CRL の生成では、 [!DNL index] および [!DNL crlnumber] ファイルが [!DNL openssl.conf]. デフォルトでは、 [!DNL demoCA] 作業ディレクトリ内の場所が使用されます。 サンプル [!DNL index] および [!DNL crlnumber] ファイルは、指定された [!DNL demoCA] ディレクトリ。

1. 前の手順で生成した CRL ファイルを、ライセンスサーバーがアクセス可能な適切な場所にデプロイします（例：個別化サーバー）。 [!DNL ROOT]) をクリックします。
1. CRL が設定されたら、ライセンスサーバーを再起動します。
