---
title: ライセンスサーバの展開オプション
description: ライセンスサーバの展開オプション
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# ライセンスサーバの展開オプション{#license-server-deployment-options}

次のいずれかのオプションを使用して、ライセンスサーバを展開できます。

* Adobe Primetime DRM Server for Protected Streaming — このライセンスサーバはストリーミング用に最適化されています。 例えば、Primetime DRM を使用してAdobeHTTP Dynamic Streaming用のサーバーを設定できます。 このサーバーは、必要な設定がほとんどなく、簡単にデプロイでき、複数のテナントをサポートします。 高いレベルの拡張性を実現できます。 この実装はストリーミング用に最適化されているので、Primetime の DRM 機能を完全にサポートするわけではありません。 例えば、ユーザー名/パスワード認証、ドメイン、ライセンスの連携はサポートされていません。 このサーバが発行するライセンスの使用規則は、サーバ設定ファイルを通じて制御され、パッケージ化時に使用するポリシーを上書きします。

  詳しくは、 *保護されたストリーミング用Adobe Primetime DRM サーバーガイド* に、License Server でサポートされる使用ルールの詳細を示します。
* 「参照実装ライセンスサーバー」(Reference Implementation License Server) — この設定を使用して、サーバー実装をカスタマイズできます。 これは、ソースコードを含むライセンスサーバーの実装例です。このコードは、Primetime DRM SDK の API を使用してすべてのタイプのリクエストを管理する方法、およびデータベースに基づくカスタムビジネスロジックを実装する方法を示しています。 このサーバが発行するライセンスの使用規則は、パッケージ時にコンテンツに関連付けられたポリシーによって制御されます。
* カスタムサーバーの実装 — SDK を使用して独自のライセンスサーバーを実装することもできます。 ここでは、API を使用してライセンスサーバーを実装する方法について説明します。
