---
description: ブラウザーTVSDKは、請求指標をXML形式でAdobeに送信します。
title: 請求指標の送信
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---


# 請求指標を送信{#transmit-billing-metrics}

ブラウザーTVSDKは、請求指標をXML形式でAdobeに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

ネットワークキャプチャツールを使用して、Browser TVSDKがAdobeに送信する統計を監視する場合は、次のようなユニットが表示されます。

```
<?xml version="1.0" encoding="UTF-8"?>
<request>
    <sc_xml_ver>1.0</sc_xml_ver>
    <reportSuiteID>primesample2</reportSuiteID>
    <visitorID>947310128cb56f41</visitorID>
    <pageURL>https://. . ..m3u8</pageURL>
    <timestamp>2016-4-7T10:1:4</timestamp>
    <contextData>
        <billingMetrics>
            <publisherID>com.adobe.primetime.reference.PrimetimeReference</publisherID>
            <contentType>vod</contentType>
            <adsEnabled>true</adsEnabled>
            <midrollEnabled>true</midrollEnabled>
            <platform>Mac OSX 10.11.5</platform>
            <tvsdkVersion>2,4,0,1559</tvsdkVersion>
            <contentURL>https://. . ..m3u8</contentURL>
        </billingMetrics>
    </contextData>
</request>
```

ブール値のプロパティ`drmProtected`、`adsEnabled`、および`midrollEnabled`は、trueの場合にのみ表示されます。