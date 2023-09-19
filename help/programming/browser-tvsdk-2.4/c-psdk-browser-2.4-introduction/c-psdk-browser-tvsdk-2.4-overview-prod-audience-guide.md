---
description: このガイドでは、Browser TVSDK を使用してビデオプレーヤーアプリケーションを開発する方法について説明します。
title: 製品の概要とオーディエンス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 製品の概要とオーディエンス{#product-overview-and-audience}

このガイドでは、Browser TVSDK を使用してビデオプレーヤーアプリケーションを開発する方法について説明します。

## 製品の概要 {#section_1C66E736CEFD4246B7C7C99AADD48118}

Adobe Primetime Software Development Kit(Browser TVSDK) は、高度なビデオ再生機能、コンテンツ保護、広告をブラウザーベースのビデオプレーヤーアプリケーションに追加できるツールキットです。 ブラウザー TVSDK は、ブラウザーベースのビデオアプリケーションを構築するための JavaScript API を提供し、次のモードでの再生のサポートを含みます。

* HTML5 のみ
* HTML5 （自動フラッシュフォールバックを使用）
* Flashが常に

このリリースには、Browser TVSDK API とサンプルのリファレンス実装が含まれています。

### UI フレームワーク

ブラウザー用の JavaScript ベースのビデオプレーヤーアプリケーションの UI 開発を高速化するために、 Browser TVSDK には、以下の API で構成される UI フレームワークが含まれています。

* 再生/一時停止、ボリュームなどのデフォルトの UI コントロールを含める
* DOM の構造を直接操作することなく、高度な再生 UI コントロールを簡単に追加（または削除）できます
* 関連する UI コントロールの動作を簡単に設定
* カスタム UI コントロールの作成
* 要件に基づいてプレーヤー UI をスキニングします。

UI フレームワークの API について詳しくは、 [ブラウザー TVSDK 2.4 用の UI フレームワーク](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html).

## 対象ユーザ {#section_DFC9DECC2E30426DBBDDEA4E288E666C}

このガイドは、読者が JavaScript を使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 ビデオプレーヤーを実装し、Browser TVSDK 機能を組み込むことができます。
