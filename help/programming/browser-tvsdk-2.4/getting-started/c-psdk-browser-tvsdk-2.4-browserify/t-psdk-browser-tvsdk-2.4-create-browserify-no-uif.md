---
description: ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレイヤーを作成します。
title: UIフレームワークを使用しないブラウズ互換プレーヤーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '229'
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
