---
description: TVSDK は、請求指標を XML 形式でAdobeに送信します。
title: 請求指標の送信
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# 請求指標の送信 {#transmit-billing-metrics}

TVSDK は、請求指標を XML 形式でAdobeに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

TVSDK がAdobeに送信する統計を監視するためにネットワークキャプチャツールを使用する場合、次のような単位が表示されます。

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

boolean プロパティ `drmProtected`, `adsEnabled`、および `midrollEnabled` 真の場合にのみ表示されます。
