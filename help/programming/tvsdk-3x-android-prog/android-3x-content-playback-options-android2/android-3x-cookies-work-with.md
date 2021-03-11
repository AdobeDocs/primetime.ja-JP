---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
title: cookieの使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Cookieを使用する{#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

認証を使用したキーサーバーへのリクエスト例を以下に示します。

1. 顧客がブラウザーでWebサイトにログインし、ログインにこの顧客がコンテンツの表示を許可されていることが示されます。
1. ライセンスサーバーの期待値に基づいて、アプリケーションが認証トークンを生成します。

   この値はTVSDKに渡されます。
1. TVSDKは、この値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツの復号化キーを取得すると、そのリクエストのCookieヘッダーに認証値が含まれます。

   キーサーバーは、要求が有効であることを認識しています。

Cookieを使用するには：

1. `cookieManager`を作成し、URIのcookieをcookieStoreに追加します。

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
   >302リダイレクトが有効な場合、cookieが属するドメインとは別のドメインに広告リクエストがリダイレクトされる場合があります。

   TVSDKは、実行時にこの`cookieManager`をクエリし、URLに関連付けられたCookieがあるかどうかを確認し、それらのCookieを自動的に使用します。

   再生中にアプリケーションでcookieを更新する必要がある場合は、`networkConfiguration.setCookieHeaders` APIを使用しないでください。更新はJAVA cookieストアで行われます。

   `networkConfiguration.setCookieHeaders` APIは、TVSDKのC++ CookieStoreにcookieを設定します。

   JAVA cookieを使用し、アプリケーションとTVSDKの間で共有する場合、JAVA CookieStoreを使用してcookieのみを管理します。

   再生が初期化される前に、前述のCookie Managerを使用してCookieをCookieStoreに設定します。

   CookieStoreに保存されたCookieは、TVSDKによって自動的に取得されます。

   再生中に後でcookieの値を更新する必要がある場合は、同じキーと新しい値フィールドを使用して、CookieStoreの同じ追加メソッドを呼び出します。

   また、
   `networkConfiguration.setReadSetCookieHeader`(false)を呼び出す前に
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >この「setReadSetCookieHeader」をfalseに設定した後、JAVA cookieマネージャーを使用してキーリクエストのcookieを設定します。

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
このコールバックAPIは、C++ cookie（http応答からのcookie）に更新がある場合に必ず呼び出されます。アプリケーションは、このコールバックをリッスンする必要があり、それに応じてJAVA CookieStoreを更新し、JAVAでのネットワーク呼び出しで次のようにcookieを利用できるようにします。

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
