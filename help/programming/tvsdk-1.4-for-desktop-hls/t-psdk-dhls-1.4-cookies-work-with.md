---
description: TVSDK を使用して、セッション管理やゲートアクセスなどのために、Cookie ヘッダーに任意のデータを送信できます。
title: cookie の操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '234'
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

1. 以下を使用します。 `cookieHeaders` プロパティ： `NetworkConfiguration` を使用して cookie を設定します。 The `cookieHeaders` プロパティは Metadata オブジェクトです。このオブジェクトにキーと値のペアを追加して、Cookie のヘッダーに含めることができます。

   例：

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   デフォルトでは、cookie ヘッダーはキーリクエストでのみ送信されます。 すべてのリクエストで Cookie ヘッダーを送信するには、 `NetworkConfiguration` プロパティ `useCookieHeadersForAllRequests` を true に設定します。

1. 次の手順を実行します。 `NetworkConfiguration` は機能し、メタデータとして設定します。

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. 前の手順で作成したメタデータを指定します。 `MediaResource`.

   例えば、 `createFromURL` メソッドで、次の情報を入力します。

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```
