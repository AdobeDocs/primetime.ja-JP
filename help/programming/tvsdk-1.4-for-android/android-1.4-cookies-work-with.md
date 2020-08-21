---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: cookieの使用
title: cookieの使用
uuid: f060b520-ceec-48ca-929f-683566fe6ae7
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# cookieの使用{#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

次に、キーサーバーに要求を行う場合の認証の種類の例を示します。

1. 顧客がブラウザーでWebサイトにログインし、ログインにコンテンツの表示が許可されていることが示されます。
1. アプリケーションは、ライセンスサーバーが予期する内容に基づいて認証トークンを生成します。 その値をTVSDKに渡します。
1. TVSDKは、その値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツの復号化キーを取得すると、そのリクエストのCookieヘッダーに認証値が含まれるので、キーサーバーはリクエストが有効であることを認識します。

Cookieを使用するには：

1. を作成 `cookieManager` し、URI用のcookieを自分に追加し `cookieStore`ます。

   例：

   >[!IMPORTANT]
   >
   >302リダイレクトが有効な場合、cookieが属するドメインとは別のドメインに広告リクエストがリダイレクトされる場合があります。

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDKは、実行時にこのcookieManagerをクエリし、URLに関連付けられたcookieがあるかどうかを確認し、それらを自動的に使用します。

   別の方法として、リクエストに使用 `cookieHeaders` する任意のcookieヘッダー文字列 `NetworkConfiguration` を設定するために、を使用することもできます。 デフォルトでは、このCookieヘッダーはキーリクエストでのみ送信されます。 Cookieヘッダーをすべてのリクエストと共に送信するには、次の `NetworkConfiguration` 方法を使用し `setUseCookieHeadersForAllRequests`ます。

```java
   NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
    
   Metadata cookie = new MetadataNode(); 
   cookie.setValue("reqPayload", “1234567”); 
   networkConfiguration.setCookieHeaders(cookie); 
   networkConfiguration.setUseCookieHeadersForAllRequests( true ); 
    
   // Set NetworkConfiguration as Metadata:                                                                   
   MetadataNode resourceMetadata = new MetadataNode(); 
   resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                            networkConfiguration); 
    
   // Call MediaResource.createFromURL to set the metadata: 
   MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
   // Load the resource 
   mediaPlayer.replaceCurrentItem(resource);
```
