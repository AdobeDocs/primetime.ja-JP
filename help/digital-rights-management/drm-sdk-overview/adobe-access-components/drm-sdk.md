---
description: Primetime DRMの主なコンポーネントは、Java SDKと、Flash PlayerおよびAdobe AIRクライアントのランタイム環境で構成されます。
seo-description: Primetime DRMの主なコンポーネントは、Java SDKと、Flash PlayerおよびAdobe AIRクライアントのランタイム環境で構成されます。
seo-title: Java SDK、Flash PlayerおよびAdobe AIRクライアント
title: Java SDK、Flash PlayerおよびAdobe AIRクライアント
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRMは、サーバー実装を作成できる構築ブロックを提供するJava SDKとして提供されます。 SDKを使用すると、組織のビジネスモデルに適したPrimetime DRMソリューションを作成できます。

SDKで提供されるJava APIについて、以下のサブセクションで説明します。

## デバイスグループドメインを管理するためのJava API{#java-apis-for-managing-device-group-domains}

これらのAPIを使用すると、サーバーはデバイスグループドメインに参加および離脱するクライアント要求を処理できます。

デバイスグループドメインは、相互にライセンスを共有できるデバイスの論理的な集まりです。 これを行うには、各デバイスが最初に同じドメインに参加/登録する必要があります。 サーバー上で実行されるPrimetime DRM SDKは、デバイスドメインの参加（登録解除）要求と、デバイスドメインの離脱（登録解除）要求を処理する必要があります。 どのドメインにも参加していないデバイスは、そのデバイスにバインドされたライセンスが発行され、他のデバイスと共有することはできません。

## コンテンツ保護用のJava API{#java-apis-for-protecting-content}

これらのAPIは、権限を定義し、配布するコンテンツを準備するために使用されます。 コンテンツ保護APIは次のとおりです。

* ポリシー管理

   ポリシー管理APIは、コンテンツに適用するポリシーを作成および変更するために使用します。 ポリシーの作成や更新が可能です。例えば、すべての使用ルールの取得/設定や、カスタム名前空間での追加パラメーターの許可などです。

* コンテンツのパッケージ化

   コンテンツパッケージ化APIは、コンテンツを暗号化し、パッケージ化されたコンテンツからメタデータを取得するために使用されます。

## ライセンス発行用のJava API{#java-apis-for-issuing-licenses}

これらのAPIは、クライアントがサーバーからライセンスを要求する場合に使用されます。 SDKは、クライアントからの次のリクエストをサポートします。

* 認証

   認証APIを使用して、認証要求を処理し、認証トークンを生成できます。

* ライセンスの生成と取得

   ライセンス生成および獲得APIは、ユーザのライセンスを生成するために使用されます。

* Adobe AIRバージョン1.5のクライアントとコンテンツのサポート

   後方互換性を確保するため、SDKには、AIRバージョン1.5以前のクライアントおよび保護されたコンテンツで使用するために作成されたAIRアプリケーションからの要求を処理するAPIが含まれています。

## リファレンスの実装 {#reference-implementation}

SDKには、Java APIの使用方法を示す、シンプルなAdobe Primetime DRMデプロイメントであるリファレンス実装が含まれています。 リファレンスの実装では、Java APIに基づくコンテンツのパッケージ化とポリシー管理のためのLicense Server、Watched Folder Packager、Primetime DRM Manager AIRアプリケーション、およびコマンドラインツールが提供されます。 Primetime DRM参照の実装について詳しくは、コンテンツの保護を参照してください。