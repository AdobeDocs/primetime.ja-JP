---
description: TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。
title: cookie の操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
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

の作成 `cookieManager` をクリックし、URI の cookie を cookieStore に追加します。

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

C++ Cookie が更新されると、イベント MediaPlayerEvent.COOKIES_UPDATED が呼び出されます。 この cookiesUpdatedEvent には、cookie の文字列値を返すメソッド getCookieString() があります。

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
