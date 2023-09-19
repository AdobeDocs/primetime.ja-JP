---
title: ソフトウェア要件
description: ソフトウェア要件
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# ソフトウェア要件 {#software-requirements}

* Tomcat 6
* JDK 1.8

## コード配信/パッケージコンテンツ{#code-delivery-package-contents}

Adobe Primetime DRM On Premises Individualization Server パッケージには、次の内容が含まれています。

* [!DNL flashaccess.war]  — 個別化サーバー
* [!DNL flashaccess-kgs.war]  — オプションのキー生成サーバー
* [!DNL /shared]  — 次を含む：

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties]  — サンプルのプロパティファイル

* [!DNL thirdparty/] - Crypto-J サポートをネイティブライブラリとして含みます。

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar]  — サーバの秘密鍵証明書のパスワードを暗号化するユーティリティ
* [!DNL ROOT] - a を含む [!DNL crossdomain.xml] ファイル

* ECI キャッシュファイル — 事前にダウンロード済み
* [!DNL addIndivCert.py] - On Premises の個別化をサポートするためにライセンスサーバーの信頼のルートを更新するスクリプト
* [!DNL CreateMetadata.jar]  — オンプレミスの DRM メタデータを作成するユーティリティ
* [!DNL client_sample/]  — クライアントコードスニペットを含むフォルダー
* リリースノート — ドキュメントに最後に追加したすべての分

## 個別化サーバー証明書の取得{#obtain-individualization-server-certificates}

オンプレミスの個別化サーバーを使用するには、最初に 2 つのデジタル資格情報（証明書）を取得する必要があります。

* *個別化トランスポート秘密鍵証明書* -Adobe発行
* *個別化 CA 資格情報* - Symantec(VeriSign) が発行

これらの証明書を取得するには、Zendesk チケットを使用して次の宛先にリクエストを送信します。 [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

これらの資格情報に加えて、Primetime DRM ライセンスサーバーの運用に必要な資格情報が含まれます。
