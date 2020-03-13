---
description: TVSDKは、請求指標をXML形式でアドビに送信します。
seo-description: TVSDKは、請求指標をXML形式でアドビに送信します。
seo-title: 請求指標の送信
title: 請求指標の送信
uuid: f4a7f50e-f457-434e-bf26-1e06cb15a038
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# 請求指標の送信 {#transmit-billing-metrics}

TVSDKは、請求指標をXML形式でアドビに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

ネットワークキャプチャツールを使用してTVSDKがアドビに送信する統計を監視する場合、次のようなユニットが表示されます。

```xml
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

Booleanプロパティ、お `drmProtected`よび `adsEnabled`Trueの `midrollEnabled` 場合にのみ表示されます。