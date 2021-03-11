---
description: Adobeアクセスの主なコンポーネントは、Java SDK、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
title: Java SDK、Flash Player、Adobe AIRクライアント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---


# Adobeアクセスコンポーネント{#adobe-access-components}

Adobeアクセスの主なコンポーネントは、Java SDK、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。

SDKのセットアップについて詳しくは、「*コンテンツ保護用のAdobeアクセスSDKの使用」の「SDKのセットアップ」を参照してください。*

AdobeアクセスSDKを使用すると、コンテンツ管理、請求、ユーザーアクセス制御システムなど、組織の既存のビジネスインフラストラクチャと統合するデジタル著作権管理ソリューションを開発できます。 Flash PlayerとAdobe AIRを使用すると、ユーザーが大規模なデジタルコンテンツのライブラリにアクセスし、表示できるアプリケーションを作成し、簡単に展開できます。

## AdobeアクセスSDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobeアクセスは、サーバー実装を作成できる構成要素を提供するJava SDKとして提供されます。 SDKを使用して、組織のビジネスモデルに適したAdobeアクセスソリューションを作成できます。

SDKで提供されるJava APIについて、以下のサブセクションで説明します。

## デバイスグループドメインを管理するためのJava API {#java-apis-for-managing-device-group-domains}

これらのAPIは、デバイスグループドメインに参加および離脱するクライアント要求をサーバーが処理できるようにするために使用されます。

デバイスグループドメインは、相互にライセンスを共有できるデバイスの論理的な集まりです。 この処理を行うには、各デバイスが最初に同じドメインに参加/登録する必要があります。 AdobeアクセスSDKは、サーバー上で実行され、デバイスドメインの参加（登録）要求と、デバイスドメインの離脱（登録解除）要求を処理する必要があります。 どのドメインにも参加していないデバイスは、そのデバイスにバインドされているライセンスが発行されます。このライセンスは、他のデバイスとは共有できません。

## コンテンツ保護用のJava API {#java-apis-for-protecting-content}

これらのAPIは、権限を定義し、配布するコンテンツを準備するために使用されます。 コンテンツ保護APIは次のとおりです。

* ポリシー管理

   ポリシー管理APIは、コンテンツに適用するポリシーを作成および変更するために使用します。 ポリシーの作成や更新が可能です。例えば、すべての使用ルールの取得/設定、カスタム名前空間での追加のパラメーターの許可などを行うことができます。

* コンテンツのパッケージ化

   コンテンツパッケージ化APIは、コンテンツを暗号化し、パッケージ化されたコンテンツからメタデータを取得するために使用されます。

## ライセンス発行用のJava API {#java-apis-for-issuing-licenses}

これらのAPIは、クライアントがサーバーからライセンスを要求する場合に使用されます。 SDKは、クライアントからの次のリクエストをサポートします。

* 認証

   認証APIは、認証要求を処理し、認証トークンを生成するために使用できます。

* ライセンスの生成と取得

   ライセンスの生成と取得APIは、ユーザーのライセンスの生成に使用されます。

* Adobe AIRバージョン1.5のクライアントとコンテンツのサポート

   下位互換性を確保するため、SDKには、AIRバージョン1.5以前のクライアントおよび保護されたコンテンツで使用するために作成されたAIRアプリケーションからの要求を処理するAPIが含まれています。

## リファレンス実装{#reference-implementation}

SDKには、Java APIの使用方法を示す、シンプルなAdobeアクセスデプロイメントのリファレンス実装が含まれています。 このリファレンスの実装には、Java APIに基づくコンテンツのパッケージ化とポリシー管理のためのLicense Server、Watched Folder Packager、AdobeアクセスマネージャーAIRアプリケーション、およびコマンドラインツールが用意されています。 Adobeアクセス参照の実装について詳しくは、*コンテンツの保護*&#x200B;を参照してください。

## 保護されたストリーミング用Adobe Access Server{#adobe-access-server-for-protected-streaming}

AdobeHTTP Dynamic Streamingなど、Adobeアクセスでコンテンツが保護されるストリーミングの場合は、保護されたストリーミング用のAdobe Access Serverも含まれます。 このソリューションは、Tomcatなどのサーブレットコンテナに容易に導入でき、最大のコンテンツ配信ニーズを満たす高いレベルの拡張性とパフォーマンスを実現できます。

## AdobeFlash Player{#adobe-flash-player}

Flash Playerは、軽量のブラウザプラグインおよびランタイムで、一貫した魅力的なユーザーエクスペリエンス、魅力的なオーディオ/ビデオ再生、広範なリーチを提供します。 Flash Playerは、ストリーム化またはダウンロードされたビデオコンテンツの高品質再生を提供します。 コンテンツ発行者の場合、Flash Playerはコンテンツを取り巻く再生画面をカスタマイズする手段を提供し、バナーとオーバーレイを使用した広告を通じて、より深いブランディング体験と収益化を可能にします。 表示向けに、Flash Playerはビデオコンテンツを直感的で視覚的に訴える方法を提供します。

Flash Playerの詳細については、次を参照してください。[www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR{#adobe-air}

Adobe AIRはクロスオペレーティングシステムランタイムで、コンテンツ制作者は、カスタマイズされたマルチメディアアプリケーションを設計することで、Webへの既存の投資をデスクトップに拡張できます。 実証済みのオープンなテクノロジーを基盤とし、信頼できるカスタムアプリケーションの開発と導入をシンプル化した信頼性の高い方法で、より安全で楽しいユーザーエクスペリエンスを提供します。 Adobe AIRでは、リッチメディアを容易に統合して、よりインタラクティブで没入型のユーザーエクスペリエンスを作成できます。 HTML、JavaScript、Flash、Adobe®Flex®ソフトウェアなどの使い慣れたツールを使用して、リッチインターネットアプリケーションの独自の組み合わせをWindows、Macintosh、Linuxに展開できます。

企業はユーザー・インターフェースを完全に制御でき、自社ブランドを反映し強化するユーザー・エクスペリエンスを設計できます。 AdobeアクセスSDKで保護されたコンテンツの再生のサポートが組み込まれているので、Adobe AIRは、カスタムのエンドツーエンドコンテンツ配信チェーンを作成するのに役立ちます。

Adobe AIRの詳細については、次を参照してください。[www.adobe.com/go/air](https://www.adobe.com/go/air)

## ネイティブiOSおよびAndroidアプリケーション{#native-ios-and-android-applications}

ネイティブiOSおよびAndroidアプリケーションAdobe Primetimeのお客様、AdobeアクセスDRM 4.0以降がご利用いただける場合は、モバイルデバイスのネイティブ(非Flash)アプリケーション内で使用されるビデオを保護するために使用できます。 この保護されたコンテンツをアプリケーションが使用できるようにするには、Adobe Primetimeクライアントライブラリを使用して実装する必要があります。

Adobe Primetimeの詳細については、次を参照してください。[https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)