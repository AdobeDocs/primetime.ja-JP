---
title: ソフトウェア要件
description: ソフトウェア要件
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# ソフトウェア要件{#software-requirements}

* Tomcat 6
* JDK 1.8

## コード配信/パッケージの内容{#code-delivery-package-contents}

Warto DRM On Premises Indivalization Serverパッケージには、次の内容が含まれています。

* [!DNL flashaccess.war]  — 個別化サーバ
* [!DNL flashaccess-kgs.war]  — オプションのキー生成サーバ
* [!DNL /shared]  — 次を含む：

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties]  — プロパティファイルの例

* [!DNL thirdparty/] - Crypto-Jサポートをネイティブライブラリとして含みます。

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar]  — サーバ資格情報のパスワードを暗号化するユーティリティ
* [!DNL ROOT] - [!DNL crossdomain.xml] ファイルを含む

* ECIキャッシュ・ファイル：事前にダウンロード済み
* [!DNL addIndivCert.py]  — オンプレミスの個別化をサポートするために、ライセンスサーバーの信頼ルートを更新するスクリプト
* [!DNL CreateMetadata.jar]  — オンプレミスDRMメタデータを作成するためのユーティリティ
* [!DNL client_sample/]  — クライアントコードスニペットを含むフォルダー
* リリースノート — ドキュメントへの最新情報の追加

## 個別化サーバー証明書の取得{#obtain-individualization-server-certificates}

オンプレミスの個別化サーバーを使用するには、まず2つのデジタル証明書（証明書）を取得する必要があります。

* *個別化トランスポート資格情報* -Adobeが発行
* *個別化CA秘密鍵証明書* - Symantec(VeriSign)が発行

これらの証明書を取得するには、Zendeskチケットを通じて次の宛先にリクエストを送信します。[https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

これらの資格情報は、Primetime DRMライセンスサーバーの操作に必要な資格情報に追加されていることに注意してください。