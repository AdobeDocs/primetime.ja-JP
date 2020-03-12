---
description: XMLHttpRequestsのwithCredentials属性がサポートされ、クロスオリジンリソース共有(CORS)リクエストに、様々なリクエストタイプのターゲットドメインのcookieを含めることができます。
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: XMLHttpRequestsのwithCredentials属性がサポートされ、クロスオリジンリソース共有(CORS)リクエストに、様々なリクエストタイプのターゲットドメインのcookieを含めることができます。
seo-title: クロスオリジンリソース共有
title: クロスオリジンリソース共有
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# クロスオリジンリソース共有 {#cross-origin-resource-sharing}

XMLHttpRequestsのwithCredentials属性がサポートされ、クロスオリジンリソース共有(CORS)リクエストに、様々なリクエストタイプのターゲットドメインのcookieを含めることができます。

クライアントがマニフェスト、セグメントまたはキーをリクエストする場合、サーバーは、クライアントが後続のリクエストに渡す必要のあるcookieを設定できます。 Cookieの読み取りと書き込みを許可するには、クライアントはクロスオリジンリクエストの `withCredentials` 属性をに設定 `true` する必要があります。

特定のメディア `withCredentials` リソースを再生する際に、ほとんどのタイプの要求をサポートするには：

1. オブジェクトを作 `CORSConfig` 成します。

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. をオブジェ `corsConfig` クトにア `NetworkConfiguration` タッチし、に設 `useCookieHeaderForAllRequests` 定しま `true`す。

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. オブジ `networkConfig` ェクトに設 `MediaPlayerItemConfig` 定します。

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. メソッ `MediaPlayerItemConfig` ドに渡 `MediaPlayer.replaceCurrentResource` します。

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>このフラ `useCookieHeaderForAllRequests` グは、ライセンス要求には影響しません。 ライセンス要求 `withCredentials` に対し `true` て属性をに設定するには、保護データに属性を設定するか、保護デ `withCredentials` ータのに認証キーを指定する必要 `httpRequestHeaders` があります。 例：

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

一部のサーバーは応答でフィールドをワイルドカード(&#39;*&#39;) `Access-Control-Allow-Origin` に設定しているので、このフラグはライセンス要求に影響しません。 ただし、資格情報フラグがに設定されている場合、ワ `true`イルドカードはで使用できませ `Access-Control-Allow-Origin`ん。 すべてのタイプの `useCookieHeaderForAllRequests` 要求 `true` に対してをに設定すると、ライセンス要求に対して次のエラーが表示される場合があります。

次の情報を記憶しておきます。

* の呼び出しが失敗す `withCredentials=true` ると、ブラウザーTVSDKは、を使用せずに呼び出しを再試行しま `withCredentials`す。
* を使用して呼び出すと、XHR `networkConfiguration.useCookieHeaderForAllRequests=false`リクエストは属性なしで行われ `withCredentials` ます。