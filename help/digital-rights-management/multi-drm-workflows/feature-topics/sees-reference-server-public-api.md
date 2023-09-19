---
description: 使用権限のリクエストと応答は、ライセンスサーバーとお客様の使用権限サービスの間の、相互に認証された SSL 接続を介して渡されます。
title: パブリック API を確認
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# パブリック API を確認 {#sees-public-api}

使用権限のリクエストと応答は、ライセンスサーバーとお客様の使用権限サービスの間の、相互に認証された SSL 接続を介して渡されます。

HTTPS URI スキーム ( [https://tools.ietf.org/html/rfc7230#section-2.7.2](https://tools.ietf.org/html/rfc7230#section-2.7.2)) は、使用権限エンドポイントと HTTPPOSTリクエストメソッド ( [https://tools.ietf.org/html/rfc7231#section-4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3)) は、リクエストに使用されます。 エンタイトルメントエンドポイントと、バックエンドエンタイトルメントを示すフラグが必要で、パッケージ化時にポリシーに含める必要があります。

## 使用権限のリクエスト {#section_BFBFEF0795CA46D6842C479256B95F95}

エンタイトルメントリクエストの本文は、次に示すように定義された JSON オブジェクトになります。

**JSON 使用権限リクエストオブジェクトの定義**

```
{ 
 "title" : "Entitlement Request", 
 "type" : "object", 
 "properties" : { 
  "messageID" : { 
   "type" : "string", 
   "description" : "Unique ID for this message (GUID).  Used to confirm that the subsequent response is actually for this request." 
  }, 
  "version" : { 
   "type" : "integer", 
   "description" : "Version number of the protocol, currently 1." 
  }, 
  "requestType" : { 
   "type" : "integer", 
   "description" : "Request type. 1 - time based entitlement request, 2 - device registration entitlement request 3 - device bound entitlement request." 
  }, 
  "contentID" : { 
   "type" : "string", 
   "description" : "Content ID (GUID) that was given to the content during packaging time." 
  }, 
  "customerCookie" : { 
   "type" : "string", 
   "description" : "Customer cookie. Cookie is just arbitrary string up to 32 characters long." 
  } 
    }, 
 "required" : ["messageID", "version", "contentID"] 
}
```

## 権利付与の応答 {#section_F15A9FD6BAD946B3B4C5C14612F90154}

使用権限の応答の本文は JSON オブジェクトです。

**JSON 使用権限の応答オブジェクトの定義**

```
{ 
  "title" : "Entitlement Response", 
  "type" : "object", 
  "properties" : { 
    "messageID" : { 
    "type" : "string", 
    "description" : "Unique ID from the Entitlement Request message.   
      Must match, or entitlement will be denied." 
  }, 
  "version" : { 
    "type" : "integer", 
    "description" : "Version number of the protocol; must be <= the version number  
      from the Entitlement Request message." 
  }, 
  "isAllowed" : { 
    "type" : "boolean", 
    "description" : "Grant the license or not." 
  }, 
  "epTokenURL" : { 
    "type" : "string", 
    "description" : "ExpressPlay Token URL" 
  }, 
  "error" : { 
    "type" : "integer", 
    "description" : "An error number produced by the entitlement server.  
      Will be passed to the client as the 'code' field of the server error response." 
  }, 
  "errorText" : { 
    "type" : "string", 
    "description" : "Additional error information produced by the entitlement server.  
      Will be passed to the client as the 'text' field of the server error response." 
  }, 
  "required" : ["messageID", "version", "isAllowed", "epTokenURL"] 
}
```
