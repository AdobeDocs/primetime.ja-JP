---
seo-title: 暗号化されたコンテンツのパッケージ化
title: 暗号化されたコンテンツのパッケージ化
uuid: 1e271167-107d-41df-8a7c-3075cb3acc0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 暗号化されたコンテンツのパッケージ化{#package-encrypted-content}

1. ディレクトリをロー `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` カルファイルシステムにコピーします。
1. ローカルフォル `Command Line Tools\` ダーで、サーバーで動作 `flashaccesstools.properties` するようにファイルを更新します。

   少なくとも次のプロパティを変更する必要があります。

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`:ライセンスサーバ証明書のパス(通常は、またはで終 [!DNL .cer]わりま [!DNL .der] す [!DNL .pem])。

   * `encrypt.license.serverurl=[license-server-url]`:ライセンスサーバーのURL:   `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`:トランスポート証明書のパス(通常は、、またはで終 [!DNL .cer]わる [!DNL .der]証明書で [!DNL .pem]す)。

   * `encrypt.sign.certfile=[packager-credentials.pfx]`:Packager証明書のパス(これはで終わり [!DNL .pfx]ます)。

   * `encrypt.sign.certpass=[password]`:Packager証明書のパスワードです。
   >[!NOTE]
   >
   >パスワードのスクランブルを解除しないようにします。

1. ポリシーを作成します。

   ローカルフォル `Command Line Tools\` ダーで、次のコマンドを実行します。

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   このコマンドは、匿名ライセンスサーバー認証( [!DNL examplepolicy.pol] オプション)を使用するという名前のポリシーフ `-x` ァイルを作成します。
1. 暗号化するMP4、FLVまたはF4Vビデオファイルをローカルフォルダーにコピーし `Command Line Tools\` ます。
1. コンテンツをパッケージ化します。

   ソースビデオファイルが次のようなものであるとしま [!DNL sample.mp4]す。 ローカルフォル `Command Line Tools\` ダーで、次のコマンドを実行します。

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >HLS、HDS、またはDASHのコンテンツをパッケージ化する場合は、 [Adobe Primetime Offline Packagerなど、別のパッケージ化ツールを使用する必要があります](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)。

1. 暗号化されたファイルアーティファクト（この場合はと） [!DNL sample_encrypted.mp4] をにコ [!DNL sample_encrypted.mp4.metadata]ピーしま `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`す。

この時点で、プロセスのパッケージ化段階が完了しました。

>[!NOTE]
>
>コンテンツのパッケージ化、ポリシーの作成などのコマンドラインツールについて詳しくは、 [Adobe Primetime DRMコマンドラインツールを参照してください](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md)。
