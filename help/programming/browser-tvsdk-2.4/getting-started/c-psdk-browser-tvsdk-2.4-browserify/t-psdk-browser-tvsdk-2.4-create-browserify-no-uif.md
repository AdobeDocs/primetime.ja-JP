---
description: ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレーヤーを作成します。
seo-description: ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレーヤーを作成します。
seo-title: UIフレームワークを使用しないブラウズ互換プレーヤーの作成
title: UIフレームワークを使用しないブラウズ互換プレーヤーの作成
uuid: c4315bc8-c75d-4dd9-8680-946c1197be1e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# UIフレームワークを使用しないブラウズ互換プレーヤーの作成{#create-a-browserify-compatible-player-without-the-ui-framework}

ブラウザーTVSDKが提供するBrowserifyライブラリファイルをアプリで使用して、Browserify互換のプレーヤーを作成します。

このトピック [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) には、基本ビデオプレーヤーの作成時に通常含める一連のブラウザーTVSDKライブラリが記載されています。 これを行うには、ライブラリを指 `script` す属性を `src` 持つタグを追加します。

このプロセスは、Browserifyと互換性のあるプレーヤーを作成する場合と少し異なります。 この場合は、コマンドを使 `require` 用して(ブラウザーTVSDK [!DNL AdobePSDK.module.js] が提供する)ファイルをアプリに含めます。 このファイルは、基本プレーヤーライブラリファイルを依存関係の適切な順序でバンドルし、プレーヤーの機能を実装す `AdobePSDK` るために使用する名前空間を返します。

ブラウザーTVSDKは、リリースパッケージに次のサンプルのBrowserifyアプリケーションおよびビルドファイルを提供します。

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

ブラウズ互換のビデオプレーヤーを作成するには：

1. 名前空間を返すBrowserify互換のライブラリファイルを必 `AdobePSDK` 須にする：

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. 「 」の説明に従って、プレイヤーを作成しま [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md)す。

   このタスクの手順1は、アプリファイル内の個々の基本プレーヤーライブラリをソースにする基本プレーヤーの手順の手順を置き換えます。
Browserifyを使用してアプリファイルをバンドルできるようになりました。
