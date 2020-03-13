---
description: Adobe Flash Playerの使用に役立つAPIがいくつかあります。
seo-description: Adobe Flash Playerの使用に役立つAPIがいくつかあります。
seo-title: Adobe Flash Playerの役に立つAPI
title: Adobe Flash Playerの役に立つAPI
uuid: eae314c0-fd9e-480f-ae1c-9b5f3eb4db4b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Adobe Flash Playerの役に立つAPI{#helpful-apis-for-the-adobe-flash-player}

Adobe Flash Playerの使用に役立つAPIがいくつかあります。

## AdobePSDK.MediaResource {#section_8C339FA1386D4B1A926A1459B2619E5E}

```js
new MediaResource(url, type, metadata, forceFlash)
```

サポートされている場合は、このパラメータを使 `forceFlash` 用して、再生技術の決定シーケンスを上書きし、実装にFlash Playerの使用を強制できます。

<!--<a id="section_FEE3205B532446498771F7DD55B5E79F"></a>-->

```js
AdobePSDK.PlayerTechnology = { 
/** 
* Determine the {AdobePSDK.PlayerTechnology} that would be used for the given 
* media resource. 
* @param {AdobePSDK.MediaResource} mediaResource 
* @returns {AdobePSDK.PlayerTechnology.Type} 
*/ 
getSupportedTechnology(mediaResource); 
}; 
 
AdobePSDK.PlayerTechnology.Type = {  
MSE, 
VIDEO_TAG,  
FLASH,  
UNKNOWN 
}; 
 
/** 
* Set the path to the SWF relative to the main html page or using http URL. 
* Defaults to the current directory of the html page. 
* 
* @param swfPath 
*/ 
AdobePSDK.setSWFPath(swfPath); 
 
/** 
* Set the path to the folder containing the authorization token(s). 
* If not set, defaults to the token folder within the SWFPath: SWFPath + "token/". 
* @param authorizationTokenPath 
*/ 
AdobePSDK.setAuthorizationTokenPath(authorizationTokenPath); 
 
/** 
* Set the name of the authorization token file. Defaults to "hlsAF_localhost.dat". 
* @param authorizationTokenFileName 
*/ 
AdobePSDK.setAuthorizationTokenFilename(authorizationTokenFilename); 
 
/** 
* Set the authorization token type, can be "SWF" or "DAT". Defaults to "DAT" 
* @param {String} authorizationTokenType 
*/ 
AdobePSDK.setAuthorizationTokenType(authorizationTokenType);
```

