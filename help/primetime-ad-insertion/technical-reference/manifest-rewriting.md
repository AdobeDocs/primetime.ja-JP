---
title: マニフェストの書き換えと広告取得ルール
description: 'マニフェストの書き換えと広告取得ルール '
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# マニフェストの書き換えと広告取得ルール{#manifest-rewriting}

PrimetimeAd Insertionは、単純な検索/置換ルールを使用して、フラグメントの書き直しやアセットの取得を行うことができます。  これは、httpsをhttp要求にダウンコンバートする場合に使用できます。これにより、TLSのハンドシェイクを削除してパフォーマンスを向上させることができます。  また、同じCDNから広告アセットとCDNアセットを配信する場合にも使用できます。

ルールは、通常の式検索/置換として定義され、送信前、またはマニフェストに挿入後にURLを変換するために使用できます。

このルールの例では、すべての広告リクエストを、httpsからhttpにダウンコンバートします。

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

次のルールは、コンテンツCDNを使用して、Adobeの広告ストレージCDNにある広告を配信します。

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

BootstrapAPIの`ptprotoswitch`パラメーターを変更すると、ルールの名前を付けたり、有効/無効にしたりできます。これは、実行するルールをカンマで区切ったリストです。  例えば、次の2つのルールは、`ptprotoswitch=adfetch_rule1,adfetch_rule2`を設定することで実行できます。

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

お客様のアカウントに対してこれらのルールを作成/有効にするには、テクニカルサポートにお問い合わせください。