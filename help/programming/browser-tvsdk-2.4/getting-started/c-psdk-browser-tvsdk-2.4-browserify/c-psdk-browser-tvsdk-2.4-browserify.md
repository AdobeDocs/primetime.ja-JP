---
description: ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレーヤーを作成できます。
seo-description: ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレーヤーを作成できます。
seo-title: ブラウズ互換のプレーヤー
title: ブラウズ互換のプレーヤー
uuid: 1832c826-d5d0-41b0-852f-286c8e4fa0f3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 概要 {#browserify-compatible-player-overview}

ブラウザーTVSDKが提供するJSファイルを使用して、ブラウザー互換のプレーヤーを作成できます。

ブラウザーTVSDKは、2つのBrowserify互換JSファイルを提供します。 1つは、AdobePSDKモジュールで使用するためのものです。これは、UI-Frameworkを使用しないアプリの開発を目的としています。 もう1つはUI-Frameworkモジュールで使用するためのものです。ui-Frameworkを使用してアプリを作成する際に使用するPTP名前空間を返します。

Browserifyを使用するには、次の設定コマンドを実行して、およびの下のディレクトリ内にフ [!DNL final.js] ァイル（Browserifyバンドルファイル）を [!DNL example] 作成し [!DNL samples/browerify/reference] ます [!DNL samples/browerify/ui-framework]。

1. に移動しま [!DNL samples/browserify/reference/build]す。
1. 次のコマンドを実行します。

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. に移動しま [!DNL samples/browserify/ui-framework/build]す。
1. 手順2と同じコマンドを実行します。

この設定を行うと、TVSDKに付属のサンプルに基づいて、ブラウズ互換のTVSDKアプリを作成できます。
