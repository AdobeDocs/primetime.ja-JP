---
seo-title: Adobe Accessの導入
title: Adobe Accessの導入
uuid: 9f9a9931-f607-4b1a-9209-0236a4c197ca
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Adobe Accessの導入 {#deploy-adobe-access}

Adobe Access SDKの主な利点は、TomcatなどのJava™アプリケーションサーバーやサーブレットコンテナにインストールできることです。 また、JDK™ 1.5以降が必要です。 ソフトウェア要件について詳しくは、Adobe Access SDKプラットフォームの要件を参照してください。 [:https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Adobe Accessを導入するための高度な手順は次のとおりです。

1. Adobe Access SDKをインストールし、設定します。
1. アドビからデジタル証明書を取得します。
1. SDKを使用してライセンスサーバーを作成するか、Protected Streaming用のAdobe Access Serverをデプロイします。
1. コンテンツのパッケージ化やポリシー管理ツールの作成、提供されているコンテンツ準備ツールの使用、またはAdobe HTTP Dynamic Streaming Packagerのライセンスの取得を行います。
1. コンテンツの使用ルールを定義し、それらのルールをサポートするポリシーを作成します。
1. パッケージ化およびポリシー管理ツールを使用して、コンテンツをパッケージ化します。
1. Flash PlayerまたはAdobe AIRを使用して保護されたコンテンツをユーザーが表示できるビデオアプリケーションを開発するか、Adobe Accessをサポートする確立済みのOVP(Online Video Platform)を使用します。
1. Flash Playerで使用するSWFファイルをWebサイトにデプロイするか、ダウンロード用のAdobe AIRインストーラーを投稿します。

これらの手順は、以降の節で拡張され、追加情報を含む他のドキュメントへの参照と共に表示されます。

## 64ビットオペレーティングシステムへの展開 {#deploying-on-a-bit-operating-system}

64ビット版のRedHatやWindowsなどの64ビット版のオペレーティングシステムは、32ビット版のオペレーティングシステムよりもはるかに高いパフォーマンスを提供します。

## Adobe Access SDKのインストール {#install-adobe-access-sdk}

Adobe Access SDKは、Javaアーカイブ(JAR)ファイルとして提供されます。 Adobe Accessのインストールについて詳しくは、『Using Adobe Access SDK for Protecting Content *and* Secure Deployment Guidelines *』を参照してください*。

## ライセンスサーバの実装 {#implement-a-license-server}

Adobe Access SDKを使用する場合は、ライセンスサーバーを作成する必要があります。 Adobe Accessを使用してコンテンツが保護されている場合、ライセンスサーバーによってライセンスが消費者に対して発行されるまで、コンテンツは表示されません。 IDベースのライセンスを使用する場合、パスワードベースの認証により、許可されたユーザーのみがコンテンツを開いて表示できるようになります。

License Serverを実装する場合は、必要なデジタル証明書をアドビから入手する必要があります。 証明書の要求の詳細な手順については、『Adobe Access証明書の登録』ドキュメントを参照してください。

License Serverの実装とデジタル証明書の取得について詳しくは、* Using Adobe Access SDK for Protecting Contentを参照してください。*

## コンテンツのパッケージ化およびポリシー管理ツールの作成 {#create-content-packaging-and-policy-management-tools}

Adobe Access SDKを使用して、コンテンツのパッケージ化およびポリシー管理ツールを作成できます。 ポリシー管理APIを使用すると、管理者はポリシーの作成、詳細の表示および更新を行うことができます。 パッケージ化APIは、ポリシーをFLVまたはF4Vファイルに埋め込み、コンテンツ暗号化キーを使用してファイルを暗号化します。

Adobe Access SDKには、コンテンツのパッケージ化の例とポ [!DNL AdobePackager.jar]リシー管理ツール()を提供するリファレンス実装( [!DNL AdobePolicyManager.jar])が含まれます。

コンテンツのパッケージ化およびポリシー管理ツールの作成について詳しくは、「Adobe Access SDKを使 *用したコンテンツの保護」を参照してください*。

## ポリシーの作成とコンテンツのパッケージ化 {#create-policies-and-package-content}

SDKがサポートする使用ルールを使用する場合は、組織のビジネスモデルをサポートするポリシーを定義して作成し、それらのポリシーを使用してコンテンツをパッケージ化する必要があります。 パッケージ化の際にポリシーがコンテンツに適用されたら、どの程度広く配布されても、コンテンツの制御を維持できます。

Adobe Accessのポリシーは、次のような様々な使用ルールをサポートしています。

* ユーザーがコンテンツの視聴を開始した後、ライセンスが有効な日数を指定します。
* ライセンスのキャッシュを許可します。
* コンテンツにアクセスできるクライアントランタイムとバージョンを指定する（例えば、ユーザーは特定のAdobe AIRアプリケーションまたは特定のバージョンのFlash Playerを持っている必要がある）。
* ユーザーは、保護されたコンテンツを表示する前、または匿名アクセスを許可する前に、ユーザー名とパスワードを使用して自分を認証する必要があります。

コンテンツのパッケージ化について詳しくは、「コンテンツの保護」 *を参照してくださ*&#x200B;い。 使用ルールとそれらがサポートするビジネスモデルについて詳しくは、「使用ルール」を参照 *してくださ*&#x200B;い。

## ビデオ再生用のアプリの開発 {#develop-applications-for-video-playback}

ユーザーがコンテンツにアクセスして表示できるようにするには、Flash PlayerまたはAdobe AIRを使用してビデオ再生アプリケーションを開発します。 ビデオ再生アプリケーションを開発したら、コンシューマーにデプロイする必要があります。 Flash Playerを使用してアプリケーションを開発する場合は、組織のWebサイトでホストします。 Adobe® AIR®を使用してアプリケーションを開発する場合は、AIRアプリケーションのインストーラーをポストして、ユーザーが自分のコンピューターにアプリケーションをダウンロードしてインストールできるようにします。

Adobe Accessで使用するカスタムビデオ再生アプリケーションの開発について詳しくは、 [ActionScript 3.0 Developer Guide*の「Working with Video](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)」という章、* [Adobe Video Technology Center](https://www.adobe.com/devnet/video/)、Open Source Media Frameworkを参照してください。