---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: Cookieの使用
title: Cookieの使用
uuid: 618bc59a-032d-445e-a867-ed2bf260570d
translation-type: tm+mt
source-git-commit: ad58732842eb651514a47dd565e31e3d98a84c46

---


# Cookieの使用 {#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

何らかの認証を持つキーサーバーへのリクエストの例を次に示します。

1. 顧客がブラウザーでWebサイトにログインすると、その顧客のログインに、その顧客がコンテンツを表示できることが示されます。
1. ライセンスサーバーの期待に基づいて、アプリケーションが認証トークンを生成します。

   この値はTVSDKに渡されます。
1. TVSDKは、この値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツを復号化するキーを取得すると、リクエストにはcookieヘッダーに認証値が含まれます。

   キーサーバーは、要求が有効であることを認識しています。

Cookieを使用するには：

1. を作成し `cookieManager` 、URIのcookieをcookieStoreに追加します。

   例：

   ```java
   CookieManager cookieManager=new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   >[!TIP]
   >
   >302リダイレクトが有効な場合、Cookieが属するドメインとは異なるドメインに広告リクエストがリダイレクトされる可能性があります。

   TVSDKは、実行時にこ `cookieManager` のクエリを実行し、URLに関連付けられているcookieがあるかどうかを確認し、それらのcookieを自動的に使用します。

   再生中にアプリケーションでcookieを更新する必要がある場合は、JAVA cookieストアで更新が発生するので、 `networkConfiguration.setCookieHeaders` APIを使用しないでください。

   `networkConfiguration.setCookieHeaders` APIは、TVSDKのC++ CookieStoreにcookieを設定します。

   JAVA cookieを使用し、アプリケーションとTVSDK間で共有する場合は、JAVA CookieStoreを使用してcookieのみを管理します。

   再生が初期化される前に、上記のようにCookie Managerを使用してCookieをCookieStoreに設定します。

   CookieStoreに保存されたcookieは、TVSDKによって自動的に取得されます。

   再生中にcookieの値を後で更新する必要がある場合は、同じキーと新しい値フィールドを使用して、CookieStoreの同じ追加メソッドを呼び出します。

   また、
   `networkConfiguration.setReadSetCookieHeader`(false)を呼び出す前に
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   この「setReadSetCookieHeader」をfalseに設定した後、JAVA cookieマネージャーを使用してキーリクエストのcookieを設定します。
   >
   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
このコールバックAPIは、C++ cookieの更新（http応答からのcookie）がある場合は常に呼び出されます。 アプリケーションは、このコールバックをリッスンし、それに応じてJAVA CookieStoreを更新して、JAVAでのネットワーク呼び出しで次のようにcookieを利用できるようにします。

   ```
   private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener() {
   @Override
   public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) {
   List<HttpCookie> cookies = cookiesUpdatedEvent.getHttpCookies();
   for(int i = 0; i < cookies.size(); i++)
   { HttpCookie c = cookies.get(i); // To set this cookie on to the cookie store //c.setValue("newValue"); //If you want to modify the value of the cookie URI myuri = URI.create(cookiesUpdatedEvent.getDomainString()); cookieManager.getCookieStore().add(myuri,c); }
   }
   }
   ```
