---
seo-title: コード配信/パッケージの内容
title: コード配信/パッケージの内容
uuid: 13de2fd4-9079-496c-a087-25176c118864
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# コード配信/パッケージの内容{#code-delivery-package-contents}

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

