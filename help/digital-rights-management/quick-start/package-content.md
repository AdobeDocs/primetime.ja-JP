---
title: 暗号化されたコンテンツのパッケージ化
description: 暗号化されたコンテンツのパッケージ化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 暗号化されたコンテンツのパッケージ化{#package-encrypted-content}

1. をコピーします。 `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` ディレクトリをローカルファイルシステムに追加します。
1. ローカルの `Command Line Tools\` フォルダー、を更新します。 `flashaccesstools.properties` ファイルを使用して、サーバーと連携します。

   少なくとも次のプロパティを変更する必要があります。

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`：ライセンスサーバー証明書のパス（通常、次で終わる） [!DNL .cer], [!DNL .der] または [!DNL .pem]) をクリックします。

   * `encrypt.license.serverurl=[license-server-url]`：ライセンスサーバー URL（例： ）。    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`：トランスポート証明書のパス（通常、次の語句で終わる） [!DNL .cer], [!DNL .der]または [!DNL .pem]) をクリックします。

   * `encrypt.sign.certfile=[packager-credentials.pfx]`:Packager 証明書のパス ( 末尾が [!DNL .pfx]) をクリックします。

   * `encrypt.sign.certpass=[password]`:Packager 証明書のパスワードです。

   >[!NOTE]
   >
   >パスワードのスクランブルを行わないようにしてください。

1. ポリシーを作成します。

   ローカルの `Command Line Tools\` フォルダーに移動するには、次のコマンドを実行します。

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   このコマンドは、 [!DNL examplepolicy.pol] 匿名ライセンスサーバ認証 ( `-x` オプション )。
1. 暗号化する MP4、FLV または F4V ビデオファイルをローカルファイルにコピーします `Command Line Tools\` フォルダー。
1. コンテンツをパッケージ化します。

   ソースビデオファイルが [!DNL sample.mp4]. ローカルの `Command Line Tools\` フォルダーに移動するには、次のコマンドを実行します。

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >HLS、HDS、DASH のコンテンツをパッケージ化する場合は、次のような別のパッケージツールを使用する必要があります。 [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. 暗号化されたファイルアーティファクトをコピーします ( この場合は [!DNL sample_encrypted.mp4] および [!DNL sample_encrypted.mp4.metadata]) から `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

この時点で、プロセスのパッケージ化フェーズが完了しました。

>[!NOTE]
>
>コンテンツのパッケージ化、ポリシーの作成などを行うコマンドラインツールについて詳しくは、 [Adobe Primetime DRM コマンドラインツール](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
