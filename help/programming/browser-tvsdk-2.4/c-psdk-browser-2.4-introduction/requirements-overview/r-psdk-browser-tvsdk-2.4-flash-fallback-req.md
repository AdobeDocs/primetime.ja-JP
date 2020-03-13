---
description: Flash Playerを使用するには、お使いの環境が必要な要件を満たしていることを確認します。
seo-description: Flash Playerを使用するには、お使いの環境が必要な要件を満たしていることを確認します。
seo-title: Flash Playerの要件
title: Flash Playerの要件
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Flash Playerの要件{#flash-player-requirements}

Flash Playerを使用するには、お使いの環境が必要な要件を満たしていることを確認します。

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Flash Playerの要件を次に示します。

* 再生するには、Flash Playerバージ `Primetime.js`ョン23以降をインストールします。
* Flash Playerバージョン23以降の更新を求めるメッセージを表示するには、Flash Playerバージョン11.0.0以降をインストールします。

## パッケージの要件 {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Flash Playerでの再生には、次のSWFファイルが必要です。

* ブラウザーTVSDK APIを処理するメインアプリケーションSWFファイル。
* Flash Playerのイ `playerProductInstall.swf` ンストールと更新を処理するSWFファイルです。

また、Flashでのビデオ再生には、SWFまたはファイルの可能性がある認証トークンファイルが必要 `.DAT` です。 SWFファイルへのパス、認証トークンファイル、トークンファイルの名前とタイプは、AdobePSDK APIを使用して指定できます。

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

