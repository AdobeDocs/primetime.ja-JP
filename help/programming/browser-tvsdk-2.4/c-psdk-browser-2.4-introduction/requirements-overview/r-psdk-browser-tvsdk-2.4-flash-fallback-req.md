---
description: Flash Playerを使用するには、環境が必要な要件を満たしていることを確認します。
title: Flash Player要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Flash Player要件{#flash-player-requirements}

Flash Playerを使用するには、環境が必要な要件を満たしていることを確認します。

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

次に、このFlash Playerの要件を示します。

* を再生するには `Primetime.js`、少なくともFlash Player23 をインストールします。
* Flash Playerバージョン 23 以降の更新を求めるメッセージを表示するには、少なくともFlash Playerバージョン 11.0.0 をインストールします。

## パッケージの要件 {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Flash Playerの再生には、次のSWFファイルが必要です。

* Browser TVSDK API を処理するメインアプリケーションSWFファイル。
* The `playerProductInstall.swf` SWFのインストールと更新を処理するFlash Playerファイル。

さらに、Flashでのビデオ再生には、SWFまたは `.DAT` ファイル。 SWFファイルへのパス、認証トークンファイルのパス、トークンファイルの名前と種類は、AdobePSDK API を使用して指定できます。

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
