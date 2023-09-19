---
title: Adobe Primetime DRM をデプロイ
description: Adobe Primetime DRM をデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Adobe Primetime DRM をデプロイ {#configure-adobe-primetime-drm}

Adobe Primetime DRM SDK の主な利点の 1 つは、Tomcat などの任意の Java™アプリケーションサーバーまたはサーブレットコンテナにインストールできる点です。 また、JDK™ 1.5 以降も必要です。 ソフトウェア要件について詳しくは、 Primetime DRM SDK プラットフォームの要件を参照してください。 [https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Primetime DRM をデプロイするための大まかな手順は次のとおりです。

1. Primetime DRM SDK をインストールして設定します。
1. 電子証明書をAdobeから取得する。
1. SDK を使用してライセンスサーバーを作成するか、保護されたストリーミング用の Primetime DRM サーバーをデプロイします。
1. コンテンツのパッケージ化やポリシー管理ツールを作成して、コンテンツのパッケージ化、提供されているコンテンツ準備ツールの使用、またはAdobeHTTP Dynamic Streamingパッケージャーの 1 つのライセンスを取得します。
1. コンテンツの使用ルールを定義し、それらのルールをサポートするポリシーを作成します。
1. パッケージ化およびポリシー管理ツールを使用して、コンテンツをパッケージ化します。
1. 消費者がFlash PlayerやAdobe AIRを使用して保護されたコンテンツを表示できるビデオアプリケーションを開発するか、Primetime DRM をサポートする確立された OVP（オンラインビデオプラットフォーム）を使用します。
1. Flash Playerで使用するSWFファイルを Web サイトにデプロイするか、Adobe AIRインストーラーを投稿してダウンロードします。

これらの手順は、以降の節で展開し、追加情報を含む他のドキュメントへの参照を含みます。

## 64 ビットオペレーティングシステムでの導入{#deploying-on-a-bit-operating-system}

64 ビット版の RedHat や Windows などの 64 ビットオペレーティングシステムは、32 ビット版のオペレーティングシステムよりもはるかに高いパフォーマンスを発揮します。

## Adobe Primetime DRM SDK のインストール {#install-adobe-primetime-drm-sdk}

Primetime DRM SDK は、Java アーカイブ (JAR) ファイルとして提供されます。 Primetime DRM のインストールについて詳しくは、 Using Adobe Primetime DRM SDK for Protecting Content and Secure Deployment Guidelines（コンテンツの保護とセキュアなデプロイメントガイドライン）を参照してください。

## ライセンスサーバの実装 {#implement-a-license-server}

Adobe Primetime DRM SDK を使用して、ライセンスサーバーを作成する必要があります。 Primetime DRM を使用してコンテンツが保護されている場合、ライセンスサーバーによって消費者に対してライセンスが発行されるまで、コンテンツは表示できません。 ID ベースのライセンスを使用する場合、パスワードベースの認証を使用すると、許可されたコンシューマーのみがコンテンツを開いて表示できるようになります。

ライセンスサーバーを実装する場合は、必要な電子証明書をAdobeから取得する必要があります。 証明書のリクエストの詳しい手順については、 Primetime DRM 証明書の登録ドキュメントを参照してください。

ライセンスサーバーの実装と電子証明書の取得について詳しくは、 **コンテンツの保護にAdobe Primetime DRM SDK を使用。**

## コンテンツパッケージおよびポリシー管理ツールの作成{#create-content-packaging-and-policy-management-tools}

Adobe Primetime DRM SDK を使用して、コンテンツパッケージ化およびポリシー管理ツールを作成できます。 ポリシー管理 API を使用すると、管理者は、ポリシーの作成、詳細の表示、更新をおこなうことができます。 パッケージ化 API は、ポリシーをビデオファイルに埋め込み、コンテンツ暗号化キーを使用してファイルを暗号化します。

Primetime DRM SDK には、参照実装 ( [!DNL AdobePackager.jar]) は、コンテンツのパッケージ化およびポリシー管理ツールの例 ( [!DNL AdobePolicyManager.jar]) をクリックします。

コンテンツパッケージおよびポリシー管理ツールの作成について詳しくは、 **コンテンツの保護にAdobe Primetime DRM SDK を使用する。**

## ポリシーの作成とコンテンツのパッケージ化 {#create-policies-and-package-content}

SDK がサポートする使用ルールを使用して、組織のビジネスモデルをサポートするポリシーを定義および作成し、それらのポリシーを使用してコンテンツをパッケージ化する必要があります。 パッケージ化中にコンテンツにポリシーが適用されると、その広さに関係なく、コンテンツの制御を維持できます。

Adobe Primetime DRM のポリシーは、次のような様々な使用ルールをサポートしています。

* 消費者がコンテンツの視聴を開始した後にライセンスが有効になる日数を指定します。
* ライセンスのキャッシュを許可しています。
* コンテンツにアクセスできるクライアントのランタイムとFlash Playerを指定する ( 例えば、ユーザーが特定のAdobe AIRアプリケーションまたは特定のバージョンのバージョンのバージョンを持っている必要がある )。
* 保護されたコンテンツを表示する前に、または匿名アクセスを許可する前に、ユーザー名とパスワードを使用して消費者に認証を求める。

コンテンツのパッケージ化について詳しくは、 *コンテンツの保護*. 使用ルールとそれらがサポートするビジネスモデルについて詳しくは、 *使用ルール*.

## ビデオ再生用のアプリケーションの開発 {#develop-applications-for-video-playback}

消費者がコンテンツにアクセスして表示できるようにするには、Flash PlayerまたはAdobe AIRを使用してビデオ再生アプリケーションを開発します。 ビデオ再生アプリケーションを開発したら、コンシューマーにデプロイする必要があります。 Flash Playerを使用してアプリケーションを開発する場合は、組織の Web サイトでホストします。 Adobe® AIR®を使用してアプリケーションを開発する場合は、消費者が自分のコンピューターにアプリケーションをダウンロードしてインストールできるように、AIRアプリケーションインストーラーを投稿します。

Adobe Primetime DRM で使用するカスタムビデオ再生アプリケーションの開発について詳しくは、 [ActionScript3.0 開発者ガイド](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)、 [Adobeビデオテクノロジーセンター](https://www.adobe.com/devnet/video/)、およびOpen Source Media Framework。
