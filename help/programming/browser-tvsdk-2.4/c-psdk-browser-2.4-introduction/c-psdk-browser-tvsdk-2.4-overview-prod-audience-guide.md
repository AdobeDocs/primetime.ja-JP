---
description: このガイドは、ブラウザーTVSDKを使用してビデオプレーヤーアプリケーションを開発する方法に関する情報を提供します。
seo-description: このガイドは、ブラウザーTVSDKを使用してビデオプレーヤーアプリケーションを開発する方法に関する情報を提供します。
seo-title: 製品の概要と閲覧者
title: 製品の概要と閲覧者
uuid: 902baabf-5e85-4d9c-8b5a-70ec0842e1bc
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 製品の概要と閲覧者{#product-overview-and-audience}

このガイドは、ブラウザーTVSDKを使用してビデオプレーヤーアプリケーションを開発する方法に関する情報を提供します。

## 製品の概要 {#section_1C66E736CEFD4246B7C7C99AADD48118}

Adobe Primetime Software Development Kit(Browser TVSDK)は、高度なビデオ再生機能、コンテンツ保護および広告をブラウザーベースのビデオプレーヤーアプリケーションに追加できるツールキットです。 ブラウザーTVSDKは、ブラウザーベースのビデオアプリケーションを構築するためのJavaScript APIを提供し、次のモードでの再生のサポートを含みます。

* HTML5のみ
* HTML5（自動フラッシュフォールバックを使用）
* Flash常に

このリリースには、Browser TVSDK APIとサンプルリファレンスの実装が含まれています。

### UIフレームワーク

ブラウザー用のJavaScriptベースのビデオプレーヤーアプリケーションのUI開発を促進するために、ブラウザーTVSDKには、次の操作を行うAPIから成るUIフレームワークが含まれています。

* 再生/一時停止、ボリュームなどの初期設定のUIコントロールを含める
* DOM構造を直接操作しなくても、高度な再生UIコントロールを簡単に追加（または削除）できます。
* 関連するUIコントロールの動作を簡単に設定
* カスタムUIコントロールの作成
* 要件に基づいてプレイヤーのUIにスキンを適用する

UIフレームワークのAPIについて詳しくは、「 [UIフレームワーク（ブラウザーTVSDK 2.4用）」を参照してください](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html)。

## オーディエンス {#section_DFC9DECC2E30426DBBDDEA4E288E666C}

このガイドは、JavaScriptを使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 ビデオプレーヤーを実装し、ブラウザーTVSDK機能を組み込むことができます。