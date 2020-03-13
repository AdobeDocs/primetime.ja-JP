---
description: Adobe Accessの主なコンポーネントは、Java SDKと、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
seo-description: Adobe Accessの主なコンポーネントは、Java SDKと、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
seo-title: Java SDK、Flash PlayerおよびAdobe AIRクライアント
title: Java SDK、Flash PlayerおよびAdobe AIRクライアント
uuid: 6b6c5aa2-56ee-4476-a05b-dcbbe3b9001e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Adobe Accessコンポーネント{#adobe-access-components}

Adobe Accessの主なコンポーネントは、Java SDKと、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。

SDKの設定について詳しくは、「Adobe Access SDKを使用したコンテンツの保護」のSDK *の設定を参照してください。*

Adobe Access SDKを使用すると、コンテンツ管理、課金、ユーザーアクセス制御システムなど、組織の既存のビジネスインフラストラクチャと統合するデジタル著作権管理ソリューションを開発できます。 Flash PlayerおよびAdobe AIRを使用すると、ユーザーがデジタルコンテンツの大きなライブラリにアクセスして表示できるアプリケーションを作成し、簡単にデプロイできます。

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Accessは、サーバー実装を作成できる構築ブロックを提供するJava SDKとして提供されます。 SDKを使用すると、組織のビジネスモデルに適したAdobe Accessソリューションを作成できます。

SDKで提供されるJava APIについて、以下のサブセクションで説明します。

## デバイスグループドメインを管理するためのJava API {#java-apis-for-managing-device-group-domains}

これらのAPIを使用すると、サーバーはデバイスグループドメインに参加および離脱するクライアント要求を処理できます。

デバイスグループドメインは、相互にライセンスを共有できるデバイスの論理的な集まりです。 これを行うには、各デバイスが最初に同じドメインに参加/登録する必要があります。 サーバー上で実行されるAdobe Access SDKは、デバイスドメインの参加（登録解除）要求と、デバイスドメインの離脱（登録解除）要求を処理する必要があります。 どのドメインにも参加していないデバイスは、そのデバイスにバインドされたライセンスが発行され、他のデバイスと共有することはできません。

## コンテンツ保護用のJava API {#java-apis-for-protecting-content}

これらのAPIは、権限を定義し、配布するコンテンツを準備するために使用されます。 コンテンツ保護APIは次のとおりです。

* ポリシー管理

   ポリシー管理APIは、コンテンツに適用するポリシーを作成および変更するために使用します。 ポリシーの作成や更新が可能です。例えば、すべての使用ルールの取得/設定や、カスタム名前空間での追加パラメーターの許可などです。

* コンテンツのパッケージ化

   コンテンツパッケージ化APIは、コンテンツを暗号化し、パッケージ化されたコンテンツからメタデータを取得するために使用されます。

## ライセンス発行用のJava API {#java-apis-for-issuing-licenses}

これらのAPIは、クライアントがサーバーからライセンスを要求する場合に使用されます。 SDKは、クライアントからの次のリクエストをサポートします。

* 認証

   認証APIを使用して、認証要求を処理し、認証トークンを生成できます。

* ライセンスの生成と取得

   ライセンス生成および獲得APIは、ユーザのライセンスを生成するために使用されます。

* Adobe AIRバージョン1.5のクライアントとコンテンツのサポート

   後方互換性を確保するため、SDKには、AIRバージョン1.5以前のクライアントおよび保護されたコンテンツで使用するために作成されたAIRアプリケーションからの要求を処理するAPIが含まれています。

## リファレンスの実装 {#reference-implementation}

SDKには、Java APIの使用方法を示す、シンプルなAdobe Accessのデプロイメントであるリファレンス実装が含まれています。 リファレンスの実装では、Java APIに基づくコンテンツのパッケージ化とポリシー管理のためのLicense Server、Watched Folder Packager、Adobe Access Manager AIRアプリケーション、およびコマンドラインツールが提供されます。 Adobe Accessリファレンスの実装について詳しくは、「コンテンツの保護」を参 *照してくださ*&#x200B;い。

## 保護されたストリーミング用のAdobe Access Server {#adobe-access-server-for-protected-streaming}

Adobe HTTP Dynamic Streamingなど、Adobe Accessでコンテンツが保護されるストリーミングの場合、このソフトウェアにはProtected Streaming用のAdobe Access Serverも含まれます。 このソリューションは、Tomcatなどのサーブレットコンテナに簡単に導入でき、最大のコンテンツ配信ニーズを満たす高い拡張性とパフォーマンスを実現できます。

## Adobe Flash Player {#adobe-flash-player}

Flash Playerは、一貫した魅力的なユーザーエクスペリエンス、魅力的なオーディオ/ビデオ再生、広範なリーチを提供する、軽量のブラウザプラグインおよびランタイムです。 Flash Playerは、ストリーム化またはダウンロードされたビデオコンテンツの高品質な再生を提供します。 コンテンツの発行者の場合、Flash Playerはコンテンツを囲む再生画面をカスタマイズする手段を提供し、バナーやオーバーレイを使用した広告を通じて、より深いブランディング体験と収益化を実現します。 Flash Playerは、ビデオコンテンツを視覚的にわかりやすく表示する方法をユーザーに提供します。

Flash Playerについて詳しくは、次を参照してください。www.adobe.com/go/flashplayer [](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIRは、コンテンツ制作者がWebへの既存の投資を、カスタマイズされたマルチメディアアプリケーションを設計することでデスクトップに拡張できる、クロスオペレーティングシステムランタイムです。 実証済みのオープンなテクノロジーを基盤としており、信頼性の高いシンプルな方法で、より安全で楽しいユーザーエクスペリエンスを提供できるカスタムアプリケーションを開発および導入できます。 Adobe AIRを使用すると、企業はリッチメディアを簡単に統合して、よりイマーシブでインタラクティブなユーザーエクスペリエンスを作成できます。 開発者は、HTML、JavaScript、Flash、Adobe® Flex®などの使い慣れたツールを使用して、独自のリッチインターネットアプリケーションの組み合わせをWindows、Macintosh、Linuxのいずれかにデプロイできます。

企業はユーザーインターフェイスを完全に制御し、自社ブランドを反映し強化するユーザーエクスペリエンスを設計できます。 Adobe Access SDKで保護されたコンテンツの再生のサポートが組み込まれているので、Adobe AIRは、カスタムのエンドツーエンドのコンテンツ配信チェーンを作成するのに役立ちます。

Adobe AIRについて詳しくは、次を参照してください。www.adobe.com/go/air [](https://www.adobe.com/go/air)

## ネイティブiOSおよびAndroidアプリケーション {#native-ios-and-android-applications}

ネイティブiOSおよびAndroidアプリケーションAdobe Primetimeのお客様のみ利用可能、Adobe Access DRM 4.0以降は、モバイルデバイス上のネイティブ（Flash以外の）アプリケーション内で使用されるビデオを保護するために使用できます。 この保護されたコンテンツをアプリケーションで使用するには、Adobe Primetime Clientライブラリを使用して実装する必要があります。

Adobe Primetimeについて詳しくは、次を参照してください。https://www.adobe.com/solutions/primetime.html [](https://www.adobe.com/solutions/primetime.html)