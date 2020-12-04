---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: cookieの使用
title: cookieの使用
uuid: 7586a5a7-9914-403b-86a9-fbdd28664b07
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '256'
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

1. Cookieを設定するには、`NetworkConfiguration`の`cookieHeaders`プロパティを使用します。 `cookieHeaders`プロパティはMetadataオブジェクトです。このオブジェクトにキーと値のペアを追加して、Cookieのヘッダーに含めることができます。

   例：

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   デフォルトでは、cookieヘッダーはキーリクエストでのみ送信されます。 Cookieヘッダーをすべてのリクエストと共に送信するには、`NetworkConfiguration`プロパティ`useCookieHeadersForAllRequests`をtrueに設定します。

1. `NetworkConfiguration`が確実に機能するように、メタデータとして設定します。

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. `MediaResource`を作成する際に前の手順のメタデータを指定します。

   例えば、`createFromURL`メソッドを使用する場合は、次の情報を入力します。

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```

