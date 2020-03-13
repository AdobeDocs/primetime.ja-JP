---
description: エンタイトルメントの要求と応答は、ライセンスサーバーと顧客のエンタイトルメントサービスとの間の相互に認証されたSSL接続を介して渡されます。
seo-description: エンタイトルメントの要求と応答は、ライセンスサーバーと顧客のエンタイトルメントサービスとの間の相互に認証されたSSL接続を介して渡されます。
seo-title: パブリックAPIを参照
title: パブリックAPIを参照
uuid: f3a17d61-04ee-4bdb-9d64-a98066c6d1c8
translation-type: tm+mt
source-git-commit: 15403abbd53486e1faa2146cda83f41bd8116632

---


# パブリックAPIを参照 {#sees-public-api}

エンタイトルメントの要求と応答は、ライセンスサーバーと顧客のエンタイトルメントサービスとの間の相互に認証されたSSL接続を介して渡されます。

HTTPS URIスキーム( [https://tools.ietf.org/html/rfc7230#section-2.7.2](https://tools.ietf.org/html/rfc7230#section-2.7.2))を使用してエンタイトルメントエンドポイントを定義し、HTTP POSTリクエストメソッド( [https://tools.ietf.org/html/rfc7231#section-4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3))を使用してリクエストを行います。 エンタイトルメントエンドポイントと、バックエンドエンタイトルメントを示すフラグが必要で、パッケージ化時にポリシーに含める必要があります。

## 権利付与要求 {#section_BFBFEF0795CA46D6842C479256B95F95}

エンタイトルメントリクエストの本文は、以下に示すように定義されたJSONオブジェクトになります。

**JSONエンタイトルメントリクエストオブジェクトの定義**

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

エンタイトルメント応答の本文はJSONオブジェクトです。

**JSONエンタイトルメント応答オブジェクトの定義**

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
