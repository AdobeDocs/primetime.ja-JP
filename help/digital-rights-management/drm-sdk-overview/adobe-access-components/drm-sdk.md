---
description: Primetime DRMの主なコンポーネントは、Java SDK、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
seo-description: Primetime DRMの主なコンポーネントは、Java SDK、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
seo-title: Java SDK、Flash Player、Adobe AIRクライアント
title: Java SDK、Flash Player、Adobe AIRクライアント
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Adobe PrimetimeDRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRMは、サーバー実装を作成できる構成要素を提供するJava SDKとして提供されます。 SDKを使用して、組織のビジネスモデルに適したPrimetime DRMソリューションを作成できます。

SDKで提供されるJava APIについて、以下のサブセクションで説明します。

## デバイスグループドメインを管理するためのJava API{#java-apis-for-managing-device-group-domains}

これらのAPIは、デバイスグループドメインに参加および離脱するクライアント要求をサーバーが処理できるようにするために使用されます。

デバイスグループドメインは、相互にライセンスを共有できるデバイスの論理的な集まりです。 この処理を行うには、各デバイスが最初に同じドメインに参加/登録する必要があります。 サーバー上で実行されているPrimetime DRM SDKは、デバイスドメインの参加（登録解除）要求と、デバイスドメインの離脱（登録解除）要求を処理する必要があります。 どのドメインにも参加していないデバイスは、そのデバイスにバインドされているライセンスが発行されます。このライセンスは、他のデバイスとは共有できません。

## コンテンツ保護用のJava API{#java-apis-for-protecting-content}

これらのAPIは、権限を定義し、配布するコンテンツを準備するために使用されます。 コンテンツ保護APIは次のとおりです。

* ポリシー管理

   ポリシー管理APIは、コンテンツに適用するポリシーを作成および変更するために使用します。 ポリシーの作成や更新が可能です。例えば、すべての使用ルールの取得/設定、カスタム名前空間での追加のパラメーターの許可などを行うことができます。

* コンテンツのパッケージ化

   コンテンツパッケージ化APIは、コンテンツを暗号化し、パッケージ化されたコンテンツからメタデータを取得するために使用されます。

## ライセンス発行用のJava API{#java-apis-for-issuing-licenses}

これらのAPIは、クライアントがサーバーからライセンスを要求する場合に使用されます。 SDKは、クライアントからの次のリクエストをサポートします。

* 認証

   認証APIは、認証要求を処理し、認証トークンを生成するために使用できます。

* ライセンスの生成と取得

   ライセンスの生成と取得APIは、ユーザーのライセンスの生成に使用されます。

* Adobe AIRバージョン1.5のクライアントとコンテンツのサポート

   下位互換性を確保するため、SDKには、AIRバージョン1.5以前のクライアントおよび保護されたコンテンツで使用するために作成されたAIRアプリケーションからの要求を処理するAPIが含まれています。

## リファレンス実装{#reference-implementation}

SDKには、Java APIの使用方法を示すシンプルなAdobe PrimetimeDRMデプロイメントのリファレンス実装が含まれています。 このリファレンスの実装には、Java APIに基づくコンテンツのパッケージ化とポリシー管理のためのライセンスサーバー、監視フォルダーパッケージャー、Primetime DRM Manager AIRアプリケーション、およびコマンドラインツールが用意されています。 Primetime DRM参照の実装について詳しくは、「コンテンツの保護」を参照してください。