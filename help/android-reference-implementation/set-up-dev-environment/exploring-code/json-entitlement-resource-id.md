---
title: エンタイトルメントリソース ID の JSON オブジェクト
description: 次のコードブロックは、エンタイトルメントリソース ID が単純なテキスト文字列の場合の JSON オブジェクトの例を示しています。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# エンタイトルメントリソース ID の JSON オブジェクト {#json-object-for-entitlement-resource-id}

次のコードブロックは、エンタイトルメントリソース ID が単純なテキスト文字列の場合の JSON オブジェクトの例を示しています。 この場合、リソース ID は文字列「resource」です。

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

次のコードブロックは、エンタイトルメントリソース ID がHTMLでエンコードされた mRSS 文字列の場合の JSON オブジェクトの例を示しています。

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

次の mRSS 文字列がリソース ID として使用されます。

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
