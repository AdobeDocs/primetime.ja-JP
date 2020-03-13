---
description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-description: TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。
seo-title: Cookieの使用
title: Cookieの使用
uuid: 7586a5a7-9914-403b-86a9-fbdd28664b07
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Cookieの使用{#work-with-cookies}

TVSDKを使用して、セッション管理、ゲートアクセスなどのために、cookieヘッダーに任意のデータを送信できます。

次に、キーサーバーにリクエストを行う際の認証の例を示します。

1. 顧客がブラウザーでWebサイトにログインし、ログインするとコンテンツの表示が許可されていることが示されます。
1. アプリケーションは、ライセンスサーバーが予期する内容に基づいて認証トークンを生成します。 この値をTVSDKに渡します。
1. TVSDKは、その値をcookieヘッダーに設定します。
1. TVSDKがキーサーバーにリクエストを送信し、コンテンツを復号化するキーを取得すると、そのリクエストはcookieヘッダーに認証値を含むので、キーサーバーはリクエストが有効であることを認識します。

Cookieを使用するには：

1. のプロパティ `cookieHeaders` を使用し `NetworkConfiguration` て、cookieを設定します。 このプ `cookieHeaders` ロパティはMetadataオブジェクトで、Cookieヘッダーに含めるキーと値のペアをこのオブジェクトに追加できます。

   例：

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   デフォルトでは、cookieヘッダーはキーリクエストでのみ送信されます。 Cookieヘッダーをすべてのリクエストと共に送信するには、このプロパティ `NetworkConfiguration` をtrueに `useCookieHeadersForAllRequests` 設定します。

1. を確実に機能させる `NetworkConfiguration` には、メタデータとして設定します。

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. を作成する際に、前の手順のメタデータを指定しま `MediaResource`す。

   例えば、この方法を使用する場合は、 `createFromURL` 次の情報を入力します。

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```

