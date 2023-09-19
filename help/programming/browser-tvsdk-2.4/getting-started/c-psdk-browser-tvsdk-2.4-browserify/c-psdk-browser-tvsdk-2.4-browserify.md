---
description: Browser TVSDK が提供する JS ファイルを使用して、Browserify 互換のプレーヤーを作成できます。
title: Browserify 互換のプレーヤー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 概要 {#browserify-compatible-player-overview}

Browser TVSDK が提供する JS ファイルを使用して、Browserify 互換のプレーヤーを作成できます。

ブラウザー TVSDK は、2 つの Browserify 互換 JS ファイルを提供します。 1 つは、AdobePSDK モジュールと共に使用するためのものです。これは、UI-Framework を使用しないアプリの開発に使用します。 もう 1 つは、UI-Framework モジュールと共に使用するためのもので、UI-Framework を使用してアプリを記述する際に使用する PTP 名前空間を返します。

Browserify を開始するには、次のセットアップコマンドを実行して、 [!DNL final.js] ファイル（Browserify バンドルファイル）を [!DNL example] のディレクトリ [!DNL samples/browerify/reference] および [!DNL samples/browerify/ui-framework]:

1. に移動します。 [!DNL samples/browserify/reference/build].
1. 次のコマンドを実行します。

   1. [!DNL npm install]
   1. [!DNL node_modules/.bin/grunt]

1. に移動します。 [!DNL samples/browserify/ui-framework/build].
1. 手順 2 と同じコマンドを実行します。

この設定が完了したら、TVSDK で提供されるサンプルに基づいて、Browserify 互換の TVSDK アプリを作成できます。
