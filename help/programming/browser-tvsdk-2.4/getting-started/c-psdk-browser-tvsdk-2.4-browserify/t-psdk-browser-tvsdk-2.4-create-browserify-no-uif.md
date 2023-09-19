---
description: Browser TVSDK が提供する Browserify ライブラリファイルをアプリ内で使用して、Browserify 互換のプレーヤーを作成します。
title: UI-Framework を使用しない、Browserify 互換のプレーヤーの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# UI-Framework を使用しない、Browserify 互換のプレーヤーの作成{#create-a-browserify-compatible-player-without-the-ui-framework}

Browser TVSDK が提供する Browserify ライブラリファイルをアプリ内で使用して、Browserify 互換のプレーヤーを作成します。

トピック [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md) に、基本的なビデオプレーヤーの作成時に通常含める一連のブラウザー TVSDK ライブラリを示します。 これをおこなうには、次を追加します。 `script` タグと `src` ライブラリを指す属性。

Browserify 互換のプレーヤーを作成する場合、プロセスは少し異なります。 この場合、 `require` コマンドを使用して [!DNL AdobePSDK.module.js] ファイル（Browser TVSDK によって提供される）をアプリ内で使用する場合。 このファイルは、基本の Player ライブラリファイルを依存関係の適切な順序でまとめて、 `AdobePSDK` 名前空間を使用して、プレーヤーの機能を実装します。

ブラウザー TVSDK は、リリースパッケージに以下のサンプルの Browserify アプリケーションとビルドファイルを提供しています。

* [!DNL [...]/samples/browserify/reference/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/reference/build/package.json]
* [!DNL [...]/samples/browserify/reference/examples/sample.html]
* [!DNL [...]/samples/browserify/reference/examples/sample.js]

Browserify 互換のビデオプレーヤーを作成するには：

1. を返す Browserify 互換ライブラリファイルが必要です。 `AdobePSDK` 名前空間：

   ```
   var AdobePSDK = require('./AdobePSDK.module.js'); 
   var player; 
   function Load () { 
       player = new AdobePSDK.MediaPlayer(); 
   […]
   ```

1. プレーヤーを作成します。詳しくは、 [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-tvsdk.md).

   このタスクの手順 1 では、アプリファイル内の個々の基本プレーヤーライブラリをソースする基本的なプレーヤー手順の手順を置き換えます。
これで、Browserify を使用してアプリファイルをバンドルできます。
