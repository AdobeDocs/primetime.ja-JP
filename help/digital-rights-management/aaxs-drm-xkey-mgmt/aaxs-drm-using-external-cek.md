---
description: 外部 CEK 機能を使用して、既存の CKMS を使用してライセンスをバンドおよびパッケージ化します。
title: 外部 CEK を使用してライセンスを送信し、パッケージ化する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 外部 CEK を使用してライセンスを送信し、パッケージ化する{#using-external-cek-to-vend-and-package-licenses}

外部 CEK 機能を使用して、既存の CKMS を使用してライセンスをバンドおよびパッケージ化します。

## EncryptContentWithExternalKey.java

これは、ビデオを AAXS — 暗号化し、次のようなメタデータを作成するコマンドラインツールです。 *not* に CEK が含まれている（AAXS ライセンスサーバーの公開証明書で保護）。 代わりに、このツールによってビデオのメタデータに CEK ID が埋め込まれます。

ライセンスの取得中に、AAXS ライセンスサーバーは、メタデータ内にフラグを観測し、このコンテンツが外部 CEK を使用して保護されたことを識別します。 ライセンスサーバーは、メタデータから CEK ID を抽出し、セキュリティで保護されたリポジトリ/CKMS に対してクエリを実行し、適切な CEK を取得します。

## パッケージ化ワークフロー

1. Java 1.6.0_24 以降を使用していることを確認します。
1. ツールの使用状況を確認するには： `java -jar AdobePackager_ExternalCEK.jar`
1. コンテンツをパッケージ化するには：

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Java ソースコードは、付属の ANT を使用して構築できます。 `build-samples.xml`
>* Flash AccessSDK ( `adobe-flashaccess-sdk.jar`) はクラスパス上に存在する必要があります
>

## サーバーワークフロー

1. 「参照実装」を設定します。
1. 既存の場合は、以前の参照実装のデプロイメントをクリーンアップします。

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. 次の項目があることを確認します。 [!DNL CEKDepot.properties] ～と一緒にファイルを作る [!DNL flashaccess-refimpl.properties]

1. Adobe Primetime Player からのライセンスリクエストの開始
1. Ref Impl ログを観察して、次のような情報を確認します。

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. 変更が必要になる場合があります [!DNL log4j.xml] ログを記録する設定 `DEBUG` レベル ( `INFO` はデフォルトで設定されています )

## 既知の問題

なし
