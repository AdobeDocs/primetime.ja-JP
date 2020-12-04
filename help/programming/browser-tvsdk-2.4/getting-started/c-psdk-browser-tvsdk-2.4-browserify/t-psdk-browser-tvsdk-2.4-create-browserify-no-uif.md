---
description: ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレイヤーを作成します。
seo-description: ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレイヤーを作成します。
seo-title: UIフレームワークを使用しないブラウズ互換プレーヤーの作成
title: UIフレームワークを使用しないブラウズ互換プレーヤーの作成
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# UIフレームワークを使用しないブラウズ互換プレーヤーの作成{#create-a-browserify-compatible-player-without-the-ui-framework}

ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレイヤーを作成します。

トピック[](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md)には、基本ビデオプレーヤーの作成時に通常含める一連のブラウザーTVSDKライブラリがリストされます。 これを行うには、ライブラリを指す`src`属性を持つ`script`タグを追加します。

このプロセスは、Browserify互換のプレーヤーを作成する場合と少し異なります。 この場合は、`require`コマンドを使用して（ブラウザーTVSDKが提供する）[!DNL AdobePSDK.module.js]ファイルをアプリに含めます。 このファイルは、基本プレーヤーライブラリファイルを依存関係の適切な順序でバンドルし、プレーヤーに機能を実装するために使用する`AdobePSDK`名前空間を返します。

Browser TVSDKは、リリースパッケージに次のサンプルのBrowser Filesとビルドファイルを用意しています。

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

ブラウズ互換のビデオプレーヤーを作成するには：

1. `AdobePSDK`名前空間を返すブラウザ互換ライブラリファイルを要求する：

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md)の説明に従って、プレイヤーを作成します。

   このタスクの手順1は、アプリファイル内の個々の基本プレーヤーライブラリのソースとなる、基本的なプレーヤーの手順の手順を置き換えます。
Browserifyを使用してアプリファイルをバンドルできるようになりました。
