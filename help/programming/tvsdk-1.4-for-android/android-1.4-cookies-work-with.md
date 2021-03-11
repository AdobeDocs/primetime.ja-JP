---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
title: cookieの使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# cookieを使用する{#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

次に、キーサーバーに要求を行う場合の認証の種類の例を示します。

1. 顧客がブラウザーでWebサイトにログインし、ログインにコンテンツの表示が許可されていることが示されます。
1. アプリケーションは、ライセンスサーバーが予期する内容に基づいて認証トークンを生成します。 その値をTVSDKに渡します。
1. TVSDKは、その値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツの復号化キーを取得すると、そのリクエストのCookieヘッダーに認証値が含まれるので、キーサーバーはリクエストが有効であることを認識します。

Cookieを使用するには：

1. `cookieManager`を作成し、URIのcookieを`cookieStore`に追加します。

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

   もう1つの方法は、`NetworkConfiguration`で`cookieHeaders`を使用して、リクエストに使用する任意のcookieヘッダー文字列を設定することです。 デフォルトでは、このCookieヘッダーはキーリクエストでのみ送信されます。 Cookieヘッダーをすべてのリクエストと共に送信するには、`NetworkConfiguration`メソッド`setUseCookieHeadersForAllRequests`を使用します。

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
