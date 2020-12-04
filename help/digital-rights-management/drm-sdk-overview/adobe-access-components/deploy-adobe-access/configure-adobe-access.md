---
seo-title: Adobe PrimetimeDRMの導入
title: Adobe PrimetimeDRMの導入
uuid: c14c2792-d207-4f39-b856-610520bdaa28
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---


# Adobe PrimetimeDRMを展開{#configure-adobe-primetime-drm}

Adobe PrimetimeDRM SDKの主な利点は、TomcatなどのJava™アプリケーションサーバーやサーブレットコンテナにインストールできることです。 また、JDK™ 1.5以降が必要です。 ソフトウェアの要件について詳しくは、Primetime DRM SDKプラットフォームの要件を参照してください。[https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Primetime DRMをデプロイするための高レベルの手順は次のとおりです。

1. Primetime DRM SDKをインストールして設定します。
1. Adobeからデジタル証明書を取得します。
1. SDKを使用してライセンスサーバーを作成するか、Primetime DRM Server for Protected Streamingをデプロイします。
1. コンテンツのパッケージ化およびポリシー管理ツールを作成して、コンテンツのパッケージ化、提供されているコンテンツ準備ツールの使用、またはAdobeHTTP Dynamic Streamingパッケージャーのライセンス認証を行います。
1. コンテンツの使用ルールを定義し、それらのルールをサポートするポリシーを作成します。
1. パッケージ化およびポリシー管理ツールを使用して、コンテンツをパッケージ化します。
1. コンシューマーがFlash PlayerやAdobe AIRを使用して保護されたコンテンツを表示できるビデオアプリケーションを開発するか、Primetime DRMをサポートする確立されたOVP（オンラインビデオプラットフォーム）を使用します。
1. Flash Playerで使用するSWFファイルをWebサイトにデプロイするか、Adobe AIRのインストーラーを投稿してダウンロードします。

これらの手順は、以降の節で説明します。詳細は、他のドキュメントを参照して参照してください。

## 64ビットのオペレーティングシステムでの展開{#deploying-on-a-bit-operating-system}

64ビット版のRedHatやWindowsなどの64ビット版のオペレーティングシステムは、32ビット版のオペレーティングシステムよりもはるかに高いパフォーマンスを提供します。

## Adobe PrimetimeDRM SDKのインストール{#install-adobe-primetime-drm-sdk}

Primetime DRM SDKは、Javaアーカイブ(JAR)ファイルとして提供されます。 Primetime DRMのインストールについて詳しくは、「Using Suite DRM SDK for Protecting Content and Secure Deployment Guidelines」を参照してください。

## ライセンスサーバーの実装{#implement-a-license-server}

Adobe PrimetimeDRM SDKを使用する場合は、License Serverを作成する必要があります。 Primetime DRMを使用してコンテンツが保護されている場合、License Serverによってライセンスがコンシューマーに対して発行されるまで、コンテンツは表示されません。 IDベースのライセンスを使用する場合、パスワードベースの認証により、許可されたユーザーだけがコンテンツを開いて表示できるようになります。

License Serverを実装する場合は、必要なデジタル証明書をAdobeから取得する必要があります。 証明書の要求に関する詳細な手順については、Primetime DRM証明書登録ドキュメントを参照してください。

License Serverの実装とデジタル証明書の取得について詳しくは、**コンテンツ保護用にAdobe PrimetimeDRM SDKを使用するを参照してください。**

## コンテンツのパッケージ化とポリシー管理ツールの作成{#create-content-packaging-and-policy-management-tools}

Adobe PrimetimeDRM SDKを使用して、コンテンツのパッケージ化およびポリシー管理ツールを作成できます。 ポリシー管理APIを使用して、管理者はポリシーの作成、表示の詳細および更新を行うことができます。 パッケージ化APIは、ポリシーをビデオファイルに埋め込み、コンテンツ暗号化キーを使用してファイルを暗号化します。

Primetime DRM SDKには、コンテンツのパッケージ化およびポリシー管理ツール([!DNL AdobePolicyManager.jar])の例を提供する参照実装([!DNL AdobePackager.jar])が含まれています。

コンテンツのパッケージ化とポリシー管理ツールの作成について詳しくは、**コンテンツ保護のためのAdobe PrimetimeDRM SDKの使用を参照してください。**

## ポリシーとパッケージコンテンツの作成{#create-policies-and-package-content}

SDKがサポートする使用ルールを使用して、組織のビジネスモデルをサポートするポリシーを定義して作成し、それらのポリシーを使用してコンテンツをパッケージ化する必要があります。 パッケージ化の際にコンテンツにポリシーが適用されると、どの程度広範囲にコンテンツが配布されても、コンテンツの制御を維持できます。

Adobe PrimetimeDRMのポリシーは、以下を含む様々な使用ルールをサポートしています。

* ユーザーがコンテンツの視聴を開始した後にライセンスが有効になる日数を指定します。
* ライセンスのキャッシュを許可します。
* コンテンツにアクセスできるクライアントランタイムとバージョンを指定する(例えば、ユーザーが特定のAdobe AIRアプリケーションまたは特定のFlash Playerを持っている必要がある)。
* 保護されたコンテンツを表示する前、または匿名アクセスを許可する前に、ユーザー名とパスワードを使用してユーザーが自分を認証するように要求する。

コンテンツのパッケージ化について詳しくは、*コンテンツの保護*&#x200B;を参照してください。 使用ルールとそれらがサポートするビジネスモデルについて詳しくは、*使用ルール*&#x200B;を参照してください。

## ビデオ再生用アプリケーションの開発{#develop-applications-for-video-playback}

消費者がコンテンツにアクセスして表示できるようにするには、Flash PlayerまたはAdobe AIRを使用してビデオ再生アプリを開発します。 ビデオ再生アプリケーションを開発したら、コンシューマーに配信する必要があります。 Flash Playerを使用してアプリを開発する場合は、組織のWebサイトでアプリをホストします。 Adobe® AIR®を使用してアプリケーションを開発する場合は、AIRアプリケーションインストーラーを投稿して、ユーザーが自分のコンピューターにアプリケーションをダウンロードしてインストールできるようにします。

Adobe PrimetimeDRMで使用するカスタムビデオ再生アプリケーションの開発について詳しくは、『ActionScript3.0開発ガイド[』の「ビデオの使用」、『](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)Adobeビデオテクノロジセンター[』、Open Source Media Frameworkを参照してください。](https://www.adobe.com/devnet/video/)