---
description: TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。
title: cookie の操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# cookie の操作 {#work-with-cookies}

TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。

次に、認証を使用したキーサーバーへのリクエスト例を示します。

1. 顧客がブラウザーで Web サイトにログインすると、その顧客のログインに、この顧客がコンテンツの表示を許可されたことが示されます。
1. ライセンスサーバーで期待される内容に基づいて、アプリケーションが認証トークンを生成します。

   この値は TVSDK に渡されます。
1. TVSDK は、この値を Cookie ヘッダーに設定します。
1. TVSDK がキーサーバーに対して、コンテンツを復号化するためのキーを取得するリクエストをおこなうと、そのリクエストの Cookie ヘッダーに認証値が含まれます。

   キーサーバーは、リクエストが有効であることを認識します。

Cookie を使用するには：

1. の作成 `cookieManager` をクリックし、URI の cookie を cookieStore に追加します。

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
   >302 リダイレクトが有効になっている場合、Cookie が属するドメインとは異なるドメインに広告リクエストがリダイレクトされることがあります。

   TVSDK がこれをクエリする `cookieManager` の実行時に、は URL に関連付けられている cookie があるかどうかを確認し、それらの cookie を自動的に使用します。

   再生中にアプリケーションで cookie を更新する必要がある場合は、 `networkConfiguration.setCookieHeaders` 更新がおこなわれる API は JAVA Cookie ストアで発生します。

   `networkConfiguration.setCookieHeaders` API は、TVSDK の C++ CookieStore に対して Cookie を設定します。

   JAVA Cookie を使用し、アプリケーションと TVSDK の間で共有する場合、JAVA CookieStore を使用して Cookie を管理します。

   再生が初期化される前に、前述のように Cookie Manager を使用して Cookie を CookieStore に設定します。

   CookieStore に保存された Cookie は、TVSDK によって自動的に取得されます。

   再生中に cookie の値を後で更新する必要がある場合は、同じキーと新しい値フィールドを使用して、CookieStore と同じ add メソッドを呼び出します。

   また、
   `networkConfiguration.setReadSetCookieHeader`(false) を呼び出す前に
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >この「setReadSetCookieHeader」を false に設定した後、JAVA Cookie マネージャーを使用して、キーリクエストの Cookie を設定します。

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
このコールバック API は、C++ cookie に更新があると（http 応答からの cookie）呼び出されます。 アプリケーションは、このコールバックをリッスンする必要があり、それに応じて JAVA CookieStore を更新して、JAVA でのネットワーク呼び出しで次のように Cookie を利用できるようにします。

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
