---
seo-title: 暗号化されたコンテンツのパッケージ化
title: 暗号化されたコンテンツのパッケージ化
uuid: 1e271167-107d-41df-8a7c-3075cb3acc0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# 暗号化されたコンテンツをパッケージ化{#package-encrypted-content}

1. `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\`ディレクトリをローカルファイルシステムにコピーします。
1. ローカルの`Command Line Tools\`フォルダーで、`flashaccesstools.properties`ファイルを更新してサーバーと連携させます。

   少なくとも次のプロパティを変更する必要があります。

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`:ライセンスサーバー証明書のパス(通常は、またはで終わ [!DNL .cer]り [!DNL .der] ます [!DNL .pem])。

   * `encrypt.license.serverurl=[license-server-url]`:ライセンスサーバーのURLの例：    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`:トランスポート証明書へのパス(通常は、、、 [!DNL .cer]またはで終わり [!DNL .der]ま [!DNL .pem]す)。

   * `encrypt.sign.certfile=[packager-credentials.pfx]`:Packager証明書へのパス(末尾が [!DNL .pfx])。

   * `encrypt.sign.certpass=[password]`:Packager証明書のパスワードです。
   >[!NOTE]
   >
   >パスワードのスクランブルを解除しないようにします。

1. ポリシーを作成します。

   ローカルの`Command Line Tools\`フォルダーで、次のコマンドを実行します。

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   このコマンドは、匿名ライセンスサーバー認証（`-x`オプション）を使用する[!DNL examplepolicy.pol]という名前のポリシーファイルを作成します。
1. 暗号化するMP4、FLVまたはF4Vビデオファイルをローカル`Command Line Tools\`フォルダーにコピーします。
1. コンテンツをパッケージ化します。

   ソースビデオファイルが[!DNL sample.mp4]であるとします。 ローカルの`Command Line Tools\`フォルダーで、次のコマンドを実行します。

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >HLS、HDS、またはDASHのコンテンツをパッケージ化する場合は、[Adobe Primetimeオフラインパッケージャー](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)など、別のパッケージャーツールを使用する必要があります。

1. 暗号化されたファイルアーティファクト（この場合は[!DNL sample_encrypted.mp4]と[!DNL sample_encrypted.mp4.metadata]）を`<Your Content Server - Tomcat Install Dir>\webapps\ROOT`にコピーします。

この時点で、プロセスのパッケージ化段階が完了しました。

>[!NOTE]
>
>コンテンツのパッケージ化、ポリシーの作成などのためのコマンドラインツールについて詳しくは、[Adobe PrimetimeDRMコマンドラインツール](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md)を参照してください。
