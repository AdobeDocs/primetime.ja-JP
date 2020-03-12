---
description: UIフレームワークを使用してBrowser TVSDKが提供するBrowserifyライブラリファイルをアプリで使用し、Browserify互換のプレーヤーを作成します。
seo-description: UIフレームワークを使用してBrowser TVSDKが提供するBrowserifyライブラリファイルをアプリで使用し、Browserify互換のプレーヤーを作成します。
seo-title: UIフレームワークを使用したブラウズ互換プレーヤーの作成
title: UIフレームワークを使用したブラウズ互換プレーヤーの作成
uuid: 544fd872-5ca1-417d-8aab-69613caada0e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# UIフレームワークを使用したブラウズ互換プレーヤーの作成 {#create-a-browserify-compatible-player-using-the-ui-framework}

UIフレームワークを使用してBrowser TVSDKが提供するBrowserifyライブラリファイルをアプリで使用し、Browserify互換のプレーヤーを作成します。

TVSDKに含まれる参照ファイルの例：

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

UIフレームワークを使用してBrowserify互換のアプリを作成するには、アプリコード内に2つのBrowserifyモジ `require` ュール（Browser TVSDKが提供する）が必要です。

1. Require Browserify modules:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. の説明に従って、開発を進めま [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md)す。
>Browserifyを使用してアプリファイルをバンドルできるようになりました。
