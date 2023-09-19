---
description: UI-Framework を使用して Browserify 互換のプレーヤーを作成するには、Browser TVSDK が提供するライブラリファイルをアプリ内で使用します。
title: UI-Framework を使用した Browserify 互換プレーヤーの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# UI-Framework を使用した Browserify 互換プレーヤーの作成 {#create-a-browserify-compatible-player-using-the-ui-framework}

UI-Framework を使用して Browserify 互換のプレーヤーを作成するには、Browser TVSDK が提供するライブラリファイルをアプリ内で使用します。

TVSDK に含まれている Browserify ファイルのサンプル：

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

UI-Framework を使用して Browserify 互換のアプリを作成するには、次の手順を実行する必要があります `require` アプリコード内の 2 つの BrowserSerify モジュール（Browser TVSDK が提供）:

1. 参照モジュールの要求：

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. 開発を進めます。詳しくは、 [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>これで、Browserify を使用してアプリファイルをバンドルできます。
