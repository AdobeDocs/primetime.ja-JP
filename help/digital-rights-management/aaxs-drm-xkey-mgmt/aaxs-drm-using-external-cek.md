---
description: 外部CEK機能を使用して、既存のCKMSを使用してライセンスを検証し、パッケージ化します。
title: 外部CEKを使用したライセンスの変更とパッケージ化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# 外部CEKを使用したVENDおよびパッケージライセンス{#using-external-cek-to-vend-and-package-licenses}

外部CEK機能を使用して、既存のCKMSを使用してライセンスを検証し、パッケージ化します。

## EncryptContentWithExternalKey.java

これは、ビデオをAAXS暗号化し、CEKを&#x200B;*含まない*&#x200B;のメタデータを作成するコマンドラインツールです（AAXSライセンスサーバーの公開証明書で保護）。 代わりに、ビデオのメタデータにCEK IDが埋め込まれます。

ライセンスの取得時に、AAXSライセンスサーバーはメタデータ内のフラグを観察し、このコンテンツが外部CEKを使用して保護されたことを識別します。 ライセンスサーバーは、メタデータからCEK IDを抽出し、セキュリティで保護されたリポジトリ/CKMSをクエリして、適切なCEKを取得します。

## パッケージ化のワークフロー

1. Java 1.6.0_24以降を使用していることを確認します。
1. ツールの使用状況を確認するには：`java -jar AdobePackager_ExternalCEK.jar`
1. コンテンツをパッケージ化するには：

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Javaソースコードは、付属のANT `build-samples.xml`を使用して構築できます。
>* Flash AccessSDK (`adobe-flashaccess-sdk.jar`)はクラスパス上に存在する必要があります

>



## サーバーワークフロー

1. リファレンスの実装を設定します。
1. 既存の場合は、以前のリファレンス導入のデプロイメントをクリーンアップします。

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. [!DNL flashaccess-refimpl.properties]の横に[!DNL CEKDepot.properties]ファイルがあることを確認します

1. Adobe Primetimeプレイヤーからのライセンス要求の開始
1. 参照インプルログを観察し、次のような情報を確認します。

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. [!DNL log4j.xml]設定を変更して、`DEBUG`レベルでログを記録する必要がある場合があります（デフォルトでは`INFO`が設定されます）

## 既知の問題

なし
