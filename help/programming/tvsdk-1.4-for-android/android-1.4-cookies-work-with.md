---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: Cookieの使用
title: Cookieの使用
uuid: f060b520-ceec-48ca-929f-683566fe6ae7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Cookieの使用{#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

次に、キーサーバーにリクエストを行う際の認証の例を示します。

1. 顧客がブラウザーでWebサイトにログインし、ログインするとコンテンツの表示が許可されていることが示されます。
1. アプリケーションは、ライセンスサーバーが予期する内容に基づいて認証トークンを生成します。 この値をTVSDKに渡します。
1. TVSDKは、その値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツを復号化するキーを取得すると、そのリクエストはcookieヘッダーに認証値を含むので、キーサーバーはリクエストが有効であることを認識します。

Cookieを使用するには：

1. を作成 `cookieManager` し、URIのcookieをに追加します `cookieStore`。

   例：

   >[!IMPORTANT]
   >
   >302リダイレクトが有効な場合、Cookieが属するドメインとは異なるドメインに広告リクエストがリダイレクトされる可能性があります。

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDKは、実行時にこのcookieManagerに対してクエリを実行し、URLに関連付けられているcookieがあるかどうかを確認し、それらを自動的に使用します。

   別の方法として、リクエストに `cookieHeaders` 使用す `NetworkConfiguration` る任意のcookieヘッダー文字列をに設定する方法があります。 デフォルトでは、このcookieヘッダーはキーリクエストでのみ送信されます。 すべてのリクエストと共にcookieヘッダーを送信するには、次の方法を使用 `NetworkConfiguration` しま `setUseCookieHeadersForAllRequests`す。

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

