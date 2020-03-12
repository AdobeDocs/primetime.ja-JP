---
description: VODコンテンツに広告を挿入できます。
seo-description: VODコンテンツに広告を挿入できます。
seo-title: 時間範囲を広告に置換
title: 時間範囲を広告に置換
uuid: 50cdcc06-7df5-414b-95d4-c684bc68dce3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 時間範囲を広告に置換{#replace-time-ranges-with-an-ad}

VODコンテンツに広告を挿入できます。

この場合、との間の `TimeRanges` がタイ `begin` ムラ `end` インか `localTime` ら削除されます。 これらは、「」「」「」「」「」「」に置き換 `AdBreak` えら `begin` れま `begin+replaceDuration`す。 置換期間がパラメーターとして存在しない場合、サーバーは返されたAdbreakに対して判断を行います。

>[!NOTE]
>
>カスタム範囲に対しては、必ず特定の置換期間を指定する必要があります。 このカスタム範囲を置き換える広告がない場合は、置き換え期間を0にします。

範囲をPrimetime ad decisioning広告に置き換えます。

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

