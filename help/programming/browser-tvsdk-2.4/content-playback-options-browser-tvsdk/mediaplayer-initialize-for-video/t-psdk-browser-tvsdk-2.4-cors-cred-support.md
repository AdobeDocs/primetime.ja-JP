---
description: XMLHttpRequests で withCredentials 属性をサポートすると、クロスオリジンリソース共有 (CORS) リクエストで、様々なリクエストタイプに対してターゲットドメインの cookie を含めることができます。
keywords: CORS；クロスオリジン；リソース共有；cookie；資格情報を使用
title: クロスオリジンリソース共有
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# クロスオリジンリソース共有 {#cross-origin-resource-sharing}

XMLHttpRequests で withCredentials 属性をサポートすると、クロスオリジンリソース共有 (CORS) リクエストで、様々なリクエストタイプに対してターゲットドメインの cookie を含めることができます。

クライアントがマニフェスト、セグメントまたはキーをリクエストする場合、サーバーは、クライアントが後続のリクエストで渡す必要がある Cookie を設定できます。 Cookie の読み取りと書き込みを許可するには、クライアントが `withCredentials` 属性 `true` クロスオリジンリクエスト用。

有効にするには `withCredentials` 特定のメディアリソースの再生時に、ほとんどのタイプのリクエストをサポートします。

1. を作成します。 `CORSConfig` オブジェクト。

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. を添付 `corsConfig` から `NetworkConfiguration` オブジェクトとセット `useCookieHeaderForAllRequests` から `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. 設定 `networkConfig` （内） `MediaPlayerItemConfig` オブジェクト。

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. 合格 `MediaPlayerItemConfig` から `MediaPlayer.replaceCurrentResource` メソッド。

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>The `useCookieHeaderForAllRequests` フラグはライセンスリクエストには影響しません。 次の手順で `withCredentials` 属性 `true` ライセンスリクエストの場合、 `withCredentials` 属性を設定するか、 `httpRequestHeaders` 保護データを取得します。 例：

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

このフラグは、一部のサーバーが `Access-Control-Allow-Origin` ワイルドカード (&#39;) のフィールド&#42;&#39;) が返されます。 ただし、資格情報フラグが `true`の場合、ワイルドカードはで使用できません `Access-Control-Allow-Origin`. 次の場合、 `useCookieHeaderForAllRequests` から `true` すべてのタイプのリクエストで、ライセンスリクエストに次のエラーが表示される場合があります。

次の情報に留意してください。

* での呼び出し時 `withCredentials=true` 失敗した場合、Browser TVSDK は、 `withCredentials`.
* を使用して呼び出しがおこなわれたとき `networkConfiguration.useCookieHeaderForAllRequests=false`を指定しない場合、XHR リクエストは `withCredentials` 属性。
