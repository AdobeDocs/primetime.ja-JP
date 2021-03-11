---
description: このガイドは、ブラウザーTVSDKを使用したビデオプレーヤーアプリケーションの開発方法に関する情報を提供します。
title: 製品の概要とオーディエンス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# 製品の概要とオーディエンス{#product-overview-and-audience}

このガイドは、ブラウザーTVSDKを使用したビデオプレーヤーアプリケーションの開発方法に関する情報を提供します。

## 製品概要{#section_1C66E736CEFD4246B7C7C99AADD48118}

Adobe Primetimeソフトウェア開発キット(Browser TVSDK)は、高度なビデオ再生機能、コンテンツ保護、広告をブラウザベースのビデオプレイヤアプリケーションに追加できるツールキットです。 ブラウザーTVSDKは、ブラウザーベースのビデオアプリケーションを構築するためのJavaScript APIを提供し、次のモードでの再生のサポートを含みます。

* HTML5のみ
* 自動フラッシュフォールバックを伴うHTML5
* Flashが常に

このリリースには、Browser TVSDK APIとサンプルリファレンス実装が含まれています。

### UIフレームワーク

ブラウザー用のJavaScriptベースのビデオプレーヤーアプリケーションのUI開発を高速化するために、ブラウザーTVSDKには、以下のAPIから成るUIフレームワークが含まれています。

* 再生/一時停止、ボリュームなどの初期設定のUIコントロールを含める
* 高度な再生UIコントロールの追加（または削除）が容易になり、DOM構造を直接操作する必要はありません
* 関連するUIコントロールの動作を簡単に設定
* カスタムUIコントロールの作成
* 要件に基づいてプレイヤーUIをスキン表示する

UIフレームワークのAPIについて詳しくは、[ブラウザーTVSDK 2.4のUIフレームワーク](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html)を参照してください。

## オーディエンス{#section_DFC9DECC2E30426DBBDDEA4E288E666C}

このガイドは、読者がJavaScriptを使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 ビデオプレーヤーを実装し、ブラウザーTVSDK機能を組み込むことができます。