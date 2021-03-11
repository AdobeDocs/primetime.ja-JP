---
description: Flash Playerを使用するには、環境が必要な要件を満たしていることを確認します。
title: Flash Player要件
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 1%

---


# Flash Player要件{#flash-player-requirements}

Flash Playerを使用するには、環境が必要な要件を満たしていることを確認します。

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Flash Playerの要件は次のとおりです。

* `Primetime.js`で再生するには、少なくともFlash Playerバージョン23をインストールしてください。
* Flash Playerバージョン23以降の更新を求めるメッセージを表示するには、少なくともFlash Playerバージョン11.0.0をインストールします。

## パッケージ化要件{#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Flash Playerのある再生には、次のSWFファイルが必要です。

* ブラウザーTVSDK APIを処理するメインアプリケーションのSWFファイル。
* Flash Playerのインストールと更新を処理する`playerProductInstall.swf` SWFファイル。

また、Flashでのビデオ再生には、SWFまたは`.DAT`ファイルの可能性がある認証トークンファイルが必要です。 SWFファイルへのパス、認証トークンファイル、トークンファイルの名前と種類は、AdobePSDK APIを使用して指定できます。

例：

```js
// Set relative or http path to directory containing SWF.  
// Defaults to current directory for the html page. 
AdobePSDK.setSWFPath(<swfPath>); 
 
// Set the relative or http path to directory containing token file(s). 
// Defaults to SWFPath + "token/". 
AdobePSDK.setAuthorizationTokenPath(<authorizationTokenPath>); 
 
// Set the name of the token file, do not include any path in this string. 
AdobePSDK.setAuthorizationTokenFilename("hlsaf_localhost.swf"); 
 
//Set the token type, "DAT" or "SWF". Defaults to "DAT" 
AdobePSDK.setAuthorizationTokenType("SWF");
```

