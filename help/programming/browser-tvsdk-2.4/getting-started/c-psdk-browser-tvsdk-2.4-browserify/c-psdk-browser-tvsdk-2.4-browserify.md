---
description: ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレイヤーを作成できます。
seo-description: ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレイヤーを作成できます。
seo-title: ブラウザー対応プレイヤー
title: ブラウザー対応プレイヤー
uuid: 1832c826-d5d0-41b0-852f-286c8e4fa0f3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# 概要{#browserify-compatible-player-overview}

ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレイヤーを作成できます。

ブラウザーTVSDKは、2つのブラウザー互換JSファイルを提供します。 1つは、AdobePSDKモジュールで使用するためのものです。これは、UI-Frameworkを使用しないアプリを開発するためのものです。 もう1つはUI-Frameworkモジュールで使用するためのものです。UI-Frameworkを使用してアプリを作成する際に使用するPTP名前空間を返します。

Browserifyを使い始めるには、次のセットアップコマンドを実行して、[!DNL samples/browerify/reference]と[!DNL samples/browerify/ui-framework]の下の[!DNL example]ディレクトリ内に[!DNL final.js]ファイル（Browserifyバンドルファイル）を作成します。

1. [!DNL samples/browserify/reference/build]に移動します。
1. 次のコマンドを実行します。

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. [!DNL samples/browserify/ui-framework/build]に移動します。
1. 手順2と同じコマンドを実行します。

この設定を完了すると、TVSDKで提供されるサンプルに基づいて、ブラウズ互換のTVSDKアプリを作成できます。
