---
description: Primetime DRM の主なコンポーネントは、Java SDK と、Flash PlayerおよびAdobe AIRクライアントランタイム環境で構成されます。
title: Java SDK、Flash Player、Adobe AIRクライアント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM は、サーバー実装を作成できる構築ブロックを提供する Java SDK として提供されます。 SDK を使用して、組織のビジネスモデルに適した Primetime DRM ソリューションを作成できます。

SDK で提供される Java API については、以下のサブセクションで説明します。

## デバイスグループドメインを管理するための Java API{#java-apis-for-managing-device-group-domains}

これらの API を使用すると、デバイスグループドメインに参加して離脱するためのクライアントリクエストをサーバーが処理できます。

デバイスグループドメインは、相互にライセンスを共有できるデバイスの論理的な集まりです。 これを実現するには、各デバイスが最初に同じドメインに参加または登録する必要があります。 サーバー上で実行されている Primetime DRM SDK は、デバイスドメインの参加（登録）リクエストと、デバイスドメインの退出（登録解除）リクエストを処理する必要があります。 どのドメインにも参加していないデバイスは、そのデバイスに結び付けられたライセンスが発行され、他のデバイスとは共有できなくなります。

## コンテンツ保護用の Java API{#java-apis-for-protecting-content}

これらの API は、権限を定義し、配布するコンテンツを準備するために使用されます。 コンテンツ保護 API は次のとおりです。

* ポリシー管理

  ポリシー管理 API は、コンテンツに適用するポリシーを作成および変更するために使用します。 ポリシーは、すべての使用ルールの取得/設定や、カスタム名前空間での追加のパラメーターの許可など、作成または更新できます。

* コンテンツのパッケージ化

  コンテンツパッケージ化 API は、コンテンツを暗号化し、パッケージ化されたコンテンツからメタデータを取得するために使用されます。

## ライセンス発行用の Java API{#java-apis-for-issuing-licenses}

これらの API は、クライアントがサーバーからライセンスをリクエストする際に使用されます。 SDK は、クライアントからの次のリクエストをサポートします。

* 認証

  認証 API は、認証リクエストの処理と認証トークンの生成に使用できます。

* ライセンスの生成と取得

  ライセンス生成および獲得 API は、ユーザーのライセンスを生成するために使用されます。

* Adobe AIRバージョン 1.5 のクライアントとコンテンツのサポート

  下位互換性を保つため、SDK には、AIRバージョン 1.5 以前のクライアントと保護されたコンテンツで使用するために作成されたAIRアプリケーションからのリクエストを処理する API があります。

## 参照実装 {#reference-implementation}

SDK には、Java API の使用方法を示すシンプルなAdobe Primetime DRM デプロイメントである参照実装が含まれています。 この参照実装では、License Server、Watched Folder Packager、Primetime DRM Manager AIRアプリケーション、および Java API に基づくコンテンツパッケージ化とポリシー管理のためのコマンドラインツールが提供されます。 Primetime DRM 参照実装について詳しくは、コンテンツの保護を参照してください。
