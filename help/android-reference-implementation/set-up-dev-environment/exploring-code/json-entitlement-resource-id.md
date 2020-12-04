---
seo-title: エンタイトルメントリソースIDのJSONオブジェクト
title: エンタイトルメントリソースIDのJSONオブジェクト
uuid: f5b659da-1732-404c-bf00-d32a0ae39aa1
description: 次のコードブロックは、エンタイトルメントリソースIDが単純なテキスト文字列の場合のJSONオブジェクトの例を示しています。
seo-description: 次のコードブロックは、エンタイトルメントリソースIDが単純なテキスト文字列の場合のJSONオブジェクトの例を示しています。
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# エンタイトルメントリソースID {#json-object-for-entitlement-resource-id}のJSONオブジェクト

次のコードブロックは、エンタイトルメントリソースIDが単純なテキスト文字列の場合のJSONオブジェクトの例を示しています。 この場合、リソースIDは文字列「resource」です。

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

次のコードブロックは、エンタイトルメントリソースIDがHTMLエンコードされたmRSS文字列の場合のJSONオブジェクトの例を示しています。

```
<rss version="2.0" xmlns:media="https://search.yahoo.com/mrss/"> 
<channel> 
<title>REF_ADOBE</title> 
<item> 
<title>Adobe Primetime Reference</title> 
<guid>1234</guid> 
<media:rating scheme="urn:v-chip">TV-PG</media:rating> 
</item> 
</channel> 
</rss>
```

次のmRSS文字列がリソースIDとして使用されます。

```
"metadata" : { 
    "entitlement" : { 
        "id" : "<rss version=&quot;2.0&quot; 
        xmlns:media=&quot; 
        https://search.yahoo.com/mrss/&quot; 
        ><channel><title>REF_ADOBE</title><item> 
        <title>Adobe Primetime Reference</title><guid> 
        1234</guid><media:rating scheme=&quot;urn:v-chip&quot;> 
        TV-PG</media:rating></item></channel></rss>" 
        } 
} 
```
