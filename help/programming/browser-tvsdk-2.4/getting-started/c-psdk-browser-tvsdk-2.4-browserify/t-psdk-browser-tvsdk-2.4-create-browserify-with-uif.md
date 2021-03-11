---
description: ブラウザーTVSDKが提供するブラウザーライブラリファイルをアプリで使用して、UIフレームワークを使用してブラウザー互換のプレイヤーを作成します。
title: UIフレームワークを使用したブラウズ互換プレーヤーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# UI-Framework {#create-a-browserify-compatible-player-using-the-ui-framework}を使用したブラウズ互換プレーヤーの作成

ブラウザーTVSDKが提供するブラウザーライブラリファイルをアプリで使用して、UIフレームワークを使用してブラウザー互換のプレイヤーを作成します。

TVSDKに含まれるブラウザーファイルのサンプル：

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

UIフレームワークを使用してBrowserify互換のアプリを作成するには、アプリコード内に2つのBrowserifyモジュール（Browser TVSDKが提供します）を`require`する必要があります。

1. Require Browserify Modules:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md)の説明に従って開発を進めます。
>Browserifyを使用してアプリファイルをバンドルできるようになりました。
