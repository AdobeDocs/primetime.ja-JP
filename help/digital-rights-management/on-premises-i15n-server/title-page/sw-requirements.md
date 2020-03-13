---
description: 'null'
seo-description: 'null'
seo-title: ソフトウェア要件
title: ソフトウェア要件
uuid: 9faa229b-1abf-4b55-b293-247777bcb1db
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# ソフトウェア要件 {#software-requirements}

* Tomcat 6
* JDK 1.8

## コード配信/パッケージの内容{#code-delivery-package-contents}

Adobe Primetime DRM On Premises Individualization Serverパッケージには、次のものが含まれています。

* [!DNL flashaccess.war]  — 個別化サーバー
* [!DNL flashaccess-kgs.war]  — オプションのキー生成サーバ
* [!DNL /shared]  — 次を含む：

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties]  — サンプルプロパティファイル

* [!DNL thirdparty/] - Crypto-Jのサポートをネイティブライブラリとして含みます。

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar]  — サーバの資格情報のパスワードを暗号化するユーティリティ
* [!DNL ROOT]  — ファイルを含 [!DNL crossdomain.xml] む

* ECIキャッシュ・ファイル：事前にダウンロード
* [!DNL addIndivCert.py]  — オンプレミスの個別化をサポートするために、ライセンスサーバーの信頼のルートを更新するスクリプト
* [!DNL CreateMetadata.jar]  — オンプレミスのDRMメタデータを作成するためのユーティリティ
* [!DNL client_sample/]  — クライアントコードスニペットを含むフォルダー
* リリースノート — ドキュメントに追加された最新の情報

## 個別化サーバー証明書の取得{#obtain-individualization-server-certificates}

オンプレミスの個別化サーバーを使用するには、まず2つのデジタル証明書（証明書）を取得する必要があります。

* *個別化トランスポート証明書* — 発行元：アドビ
* *個別化CA秘密鍵証明書* - Symantec (VeriSign)が発行

これらの証明書を取得するには、Zendeskチケットを通じて次の宛先にリクエストを送信します。https://adobeprimetime.zendesk.com [](https://adobeprimetime.zendesk.com)

これらの資格情報は、Primetime DRMライセンスサーバーの運用に必要な資格情報に追加されています。