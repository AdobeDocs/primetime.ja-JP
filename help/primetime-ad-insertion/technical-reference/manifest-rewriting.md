---
title: マニフェストの書き換えと広告取得ルール
description: マニフェストの書き換えと広告取得ルール
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# マニフェストの書き換えと広告取得ルール {#manifest-rewriting}

PrimetimeAd Insertionは、単純な検索/置換ルールを使用してフラグメントの書き直しやアセットの取得をおこなうことができます。  これを使用して、https を http リクエストにダウンコンバートし、TLS のハンドシェイクを削除することでパフォーマンスを向上させることができます。  これは、同じ CDN から広告アセットと CDN アセットを配信する場合にも使用できます。

ルールは、正規表現の検索/置換として定義され、送信前やマニフェストに挿入後に url を変換するために使用できます。

このルールの例では、すべての広告リクエストがdomain.comに https から http にダウンコンバートされます。

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

次のルールでは、コンテンツ CDN を使用して、Adobeの広告ストレージ CDN に配置された広告を配信します。

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

ルールは、 `ptprotoswitch` パラメーターを指定します。BootstrapAPI は、実行するルールのコンマ区切りリストです。  例えば、これら 2 つのルールは、 `ptprotoswitch=adfetch_rule1,adfetch_rule2`:

```
<ruleSet>
    <rule name="rule1">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
    <rule name="rule2">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
</ruleSet>
```

お使いのアカウントでこれらのルールを作成/有効にするには、テクニカルサポートにお問い合わせください。
