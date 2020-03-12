---
description: 外部CEK機能を使用して、既存のCKMSを使用してライセンスを検証し、パッケージ化します。
seo-description: 外部CEK機能を使用して、既存のCKMSを使用してライセンスを検証し、パッケージ化します。
seo-title: 外部CEKを使用した検索とパッケージライセンス
title: 外部CEKを使用した検索とパッケージライセンス
uuid: 1bfd8c6c-4ae9-47de-8247-085b5360127d
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# 外部CEKを使用した検索とパッケージライセンス{#using-external-cek-to-vend-and-package-licenses}

外部CEK機能を使用して、既存のCKMSを使用してライセンスを検証し、パッケージ化します。

## EncryptContentWithExternalKey.java

これは、ビデオをAAXS暗号化し、CEK（AAXSライセンスサーバーの公開証明書で保護）を含まない ** 、メタデータを作成するコマンドラインツールです。 代わりに、ツールはビデオのメタデータにCEK IDを埋め込みます。

ライセンスの取得時に、AAXSライセンスサーバーは、このコンテンツが外部CEKを使用して保護されたことを識別するメタデータのフラグを監視します。 ライセンスサーバは、メタデータからCEK IDを抽出し、セキュリティで保護されたリポジトリ/CKMSに対してクエリを実行し、適切なCEKを取得します。

## パッケージ化ワークフロー

1. Java 1.6.0_24以降を使用していることを確認します。
1. ツールの使用状況を確認するには： `java -jar AdobePackager_ExternalCEK.jar`
1. コンテンツをパッケージ化するには：

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Javaソースコードは、付属のANTを使用して構築できます。 `build-samples.xml`
>* Flash Access SDK ()は、クラスパ `adobe-flashaccess-sdk.jar`ス上に存在する必要があります
>



## サーバーワークフロー

1. 参照実装を設定します。
1. 既存の場合は、以前のリファレンス実装のデプロイメントをクリーンアップします。

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. ファイルが [!DNL CEKDepot.properties][!DNL flashaccess-refimpl.properties]

1. Adobe Primetime Playerからのライセンス要求の開始
1. 参照インプルのログを観察し、次のようなものを探します。

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. レベルでログを記録するには、設定を [!DNL log4j.xml] 変更する必要がある場合があ `DEBUG` ります(デフ `INFO` ォルトで設定されます)。

## 既知の問題

なし
