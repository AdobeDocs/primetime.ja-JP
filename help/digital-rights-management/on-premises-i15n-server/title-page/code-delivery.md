---
title: コード配信/パッケージの内容
description: コード配信/パッケージの内容
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# コード配信/パッケージの内容{#code-delivery-package-contents}

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

