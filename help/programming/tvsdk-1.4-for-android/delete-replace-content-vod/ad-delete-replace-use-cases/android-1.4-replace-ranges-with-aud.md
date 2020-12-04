---
description: VODコンテンツに広告を挿入できます。
seo-description: VODコンテンツに広告を挿入できます。
seo-title: 時間範囲の広告への置換
title: 時間範囲の広告への置換
uuid: 50cdcc06-7df5-414b-95d4-c684bc68dce3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# 時間範囲を広告{#replace-time-ranges-with-an-ad}に置換

VODコンテンツに広告を挿入できます。

この場合、`localTime`の`begin`と`end`の間の`TimeRanges`は、タイムラインから削除されます。 これらは、`begin`の`AdBreak`から`begin+replaceDuration`に置き換えられます。 置き換え時間がパラメーターとして存在しない場合、サーバーは返されたAdbreakに対して判定を行います。

>[!NOTE]
>
>カスタム範囲に対しては、必ず特定の置き換え時間を指定する必要があります。 このカスタム範囲を置き換える広告がない場合は、置き換え時間を0にします。

範囲をPrimetime ad decisioningの広告に置き換えます。

```
{   
    "properties": [],
    "stream": {
        "manifests": [ {
            "url": 
              "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
            "type": "hls"
        } ],
                 
        "metadata": {
            "time-ranges": {
                "type": "replace",
                "time-range-list": [ {
                    "begin": 0,
                    "end": 15000,
                    "replacement-duration": 15000 
                },
                {
                    "begin": 69000,
                    "end": 99000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 251000,
                    "end": 281000,
                    "replacement-duration": 30000
                },
                {
                    "begin": 514000,
                    "end": 544000,
                    "replacement-duration": 30000
                } ]
            },
            "ad": {
                "targeting": [ {
                    "value": "MulAdsAvail12346",
                    "key": "osmfKeyMulAdsAvail12346"
                } ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - Replace TimeRange with Auditude Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

