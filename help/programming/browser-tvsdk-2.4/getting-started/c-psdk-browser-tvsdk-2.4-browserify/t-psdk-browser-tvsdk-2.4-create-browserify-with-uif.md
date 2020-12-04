---
description: ブラウザーTVSDKが提供するブラウザーライブラリファイルをアプリで使用して、UIフレームワークを使用してブラウザー互換のプレイヤーを作成します。
seo-description: ブラウザーTVSDKが提供するブラウザーライブラリファイルをアプリで使用して、UIフレームワークを使用してブラウザー互換のプレイヤーを作成します。
seo-title: UIフレームワークを使用したブラウズ互換プレーヤーの作成
title: UIフレームワークを使用したブラウズ互換プレーヤーの作成
uuid: 544fd872-5ca1-417d-8aab-69613caada0e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '152'
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
