---
title: License Server展開オプション
description: License Server展開オプション
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# License Serverの展開オプション{#license-server-deployment-options}

License Serverは、次のいずれかのオプションを使用して展開できます。

* 保護されたストリーミング用のAdobe PrimetimeDRMサーバ — このライセンスサーバはストリーミング用に最適化されています。 例えば、Primetime DRMを使用してAdobeHTTP Dynamic Streaming用にサーバーを設定できます。 このサーバは、必要な構成がほとんどなく、容易に導入でき、複数のテナントをサポートします。 高いレベルの拡張性を実現できます。 この実装はストリーミング用に最適化されているので、Primetime DRMの完全な機能はサポートされません。 例えば、ユーザー名とパスワードの認証、ドメイン、ライセンスのチェーンはサポートされていません。 このサーバーが発行するライセンスの使用規則は、サーバー設定ファイルを通じて制御されます。このファイルは、パッケージ化の際に使用するポリシーを上書きします。

   License Serverでサポートされる使用ルールの詳細については、『保護されたストリーミング用Adobe PrimetimeDRMサーバーガイド』を参照してください。**
* リファレンス実装ライセンスサーバー — この設定を使用してサーバー実装をカスタマイズできます。 これは、Primetime DRM SDKのAPIを使用してすべてのタイプのリクエストを管理する方法、およびデータベースに支援されたカスタムビジネスロジックを実装する方法を示すソースコードを含むライセンスサーバー実装の例です。 このサーバが発行するライセンスの使用規則は、パッケージ時にコンテンツに関連付けられたポリシーによって制御されます。
* カスタムサーバーの実装 — 独自のライセンスサーバーをSDKに実装することもできます。 この情報では、APIを使用してライセンスサーバーを実装する方法を説明します。

