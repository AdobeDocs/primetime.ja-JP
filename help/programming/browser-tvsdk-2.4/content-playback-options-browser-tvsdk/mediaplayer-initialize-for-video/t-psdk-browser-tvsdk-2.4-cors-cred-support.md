---
description: XMLHttpRequestsのwithCredentials属性がサポートされるようになりました。クロス接触チャネルリソース共有(CORS)リクエストでは、様々なリクエストタイプに対するターゲットドメインのcookieを含めることができます。
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: XMLHttpRequestsのwithCredentials属性がサポートされるようになりました。クロス接触チャネルリソース共有(CORS)リクエストでは、様々なリクエストタイプに対するターゲットドメインのcookieを含めることができます。
seo-title: 接触チャネル間のリソース共有
title: 接触チャネル間のリソース共有
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# 接触チャネル間のリソース共有{#cross-origin-resource-sharing}

XMLHttpRequestsのwithCredentials属性がサポートされるようになりました。クロス接触チャネルリソース共有(CORS)リクエストでは、様々なリクエストタイプに対するターゲットドメインのcookieを含めることができます。

クライアントがマニフェスト、セグメントまたはキーをリクエストする場合、サーバーでは、クライアントが後続のリクエストで渡す必要があるcookieを設定できます。 Cookieの読み取りと書き込みを許可するには、クライアントが接触チャネル間リクエストの`withCredentials`属性を`true`に設定する必要があります。

特定のメディアリソースを再生する際に、ほとんどのタイプのリクエストに対して`withCredentials`サポートを有効にするには：

1. `CORSConfig`オブジェクトを作成します。

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. `corsConfig`を`NetworkConfiguration`オブジェクトに接続し、`useCookieHeaderForAllRequests`を`true`に設定します。

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. `MediaPlayerItemConfig`オブジェクトに`networkConfig`を設定します。

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. `MediaPlayerItemConfig`を`MediaPlayer.replaceCurrentResource`メソッドに渡します。

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>`useCookieHeaderForAllRequests`フラグは、ライセンス要求には影響しません。 ライセンス要求の`withCredentials`属性を`true`に設定するには、保護データに`withCredentials`属性を設定するか、保護データの`httpRequestHeaders`に認証キーを指定する必要があります。 例：

```
# Example 1 
{ 
    "com.widevine.alpha": {  
        "withCredentials":true,  
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i]" } 
} 
 
# Example 2 
{ 
    "com.widevine.alpha": { 
        "httpRequestHeaders": {  
            "authorization": "true"  
            }, 
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i>]" }
        } 
}
```

一部のサーバーでは、応答内の`Access-Control-Allow-Origin`フィールドがワイルドカード(&#39;*&#39;)に設定されているので、このフラグはライセンス要求に影響を与えません。 ただし、資格情報フラグを`true`に設定した場合、ワイルドカードは`Access-Control-Allow-Origin`で使用できません。 すべてのタイプのリクエストに対して`useCookieHeaderForAllRequests`を`true`に設定すると、ライセンスリクエストに対して次のエラーが表示される場合があります。

次の情報を覚えておいてください。

* `withCredentials=true`による呼び出しが失敗すると、ブラウザーTVSDKは、`withCredentials`を使用しない呼び出しを再試行します。
* `networkConfiguration.useCookieHeaderForAllRequests=false`で呼び出しが行われると、`withCredentials`属性なしでXHRリクエストが行われます。