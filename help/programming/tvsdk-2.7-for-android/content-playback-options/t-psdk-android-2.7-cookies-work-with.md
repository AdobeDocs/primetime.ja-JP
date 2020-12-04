---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: cookieの使用
title: cookieの使用
uuid: a3b966fd-1263-458d-8303-b4e898372ee1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '258'
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

`cookieManager`を作成し、URIのcookieをcookieStoreに追加します。

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

MediaPlayerEvent.COOKIES_UPDATEDイベントは、C++のCookieが更新されたときに呼び出されます。 このcookiesUpdatedEventには、cookieの文字列値を返すメソッドgetCookieString()があります。

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

