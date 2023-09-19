---
description: TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。
title: cookie の操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cookie の操作{#work-with-cookies}

TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。

キーサーバーにリクエストを送信する際の、ある種の認証の例を次に示します。

1. 顧客がブラウザーで Web サイトにログインすると、その顧客のログインに、コンテンツの表示が許可されていることが示されます。
1. アプリケーションは、ライセンスサーバーが期待する内容に基づいて認証トークンを生成します。 その値を TVSDK に渡します。
1. TVSDK は、この値を Cookie ヘッダーに設定します。
1. TVSDK がキーサーバーにリクエストを送信して、コンテンツを復号化するキーを取得すると、そのリクエストの Cookie ヘッダーに認証値が含まれるので、キーサーバーはリクエストが有効であることを認識します。

Cookie を使用するには：

1. の作成 `cookieManager` をクリックし、URI の Cookie を `cookieStore`.

   例：

   >[!IMPORTANT]
   >
   >302 リダイレクトが有効になっている場合、Cookie が属するドメインとは異なるドメインに広告リクエストがリダイレクトされることがあります。

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDK は、実行時にこの cookieManager に対してクエリを実行し、その URL に関連付けられている cookie があるかどうかを確認し、それらを自動的に使用します。

   もう 1 つのオプションは、 `cookieHeaders` in `NetworkConfiguration` を使用して、リクエストに使用する任意の cookie ヘッダー文字列を設定します。 デフォルトでは、この Cookie ヘッダーは、キーリクエストでのみ送信されます。 すべてのリクエストで Cookie ヘッダーを送信するには、 `NetworkConfiguration` メソッド `setUseCookieHeadersForAllRequests`:

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
