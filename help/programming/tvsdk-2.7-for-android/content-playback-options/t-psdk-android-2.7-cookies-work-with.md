---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: Cookieの使用
title: Cookieの使用
uuid: a3b966fd-1263-458d-8303-b4e898372ee1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

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

を作成し `cookieManager` 、URIのcookieをcookieStoreに追加します。

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

MediaPlayerEvent.COOKIES_UPDATEDイベントは、C++のcookieが更新されたときに呼び出されます。 このcookiesUpdatedEventには、cookieの文字列値を返すメソッドgetCookieString()があります。

サンプルコードスニペットを以下に示します。

```
private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener()  
{ 
@Override 
public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) 
 { 
 String cookieStr = cookiesUpdatedEvent.getCookieString();  
 logger.i(LOG_TAG + "::MediaPlayer.CookiesUpdatedEventListener#onCookiesUpdated()", "cookieStr " + cookieStr);  
 }  
};
```

