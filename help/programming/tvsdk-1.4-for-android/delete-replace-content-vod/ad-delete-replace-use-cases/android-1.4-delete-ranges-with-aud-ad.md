---
description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-title: 範囲の削除
title: 範囲の削除
uuid: 2f4afa0d-69e3-4929-8dbd-b553c8a64d96
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# 範囲を削除{#delete-ranges}

localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。

>[!NOTE]
>
>コンテンツから特定の範囲のみを削除し、広告マップを広告サーバーの定義に従って使用する必要がある場合は、`CustomRangeMetadata`インスタンスを作成し、定義したカスタム範囲を持つDELETE操作としてタイプを指定します。

Adobe PrimetimeAd Decisioning広告の範囲を削除します。

```
{   
    "properties": [],
    "stream": {
        "manifests": [
            {
                "url": "https://xyz.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
                "type": "hls"
            }
        ],
     
        "metadata": {
            "time-ranges": {
                "type": "delete",
                "time-range-list": [
                    {
                        "begin": 0,
                        "end": 20000
                    },
                    {
                        "begin": 69000,
                        "end": 99000
                    },
                    {
                        "begin": 251000,
                        "end": 281000
                    },
                    {
                        "begin": 514000,
                        "end": 544000
                    }
                ]
     
            },
            "ad": {
                "targeting": [
                    {
                        "value": "MulAdsAvail12346",
                        "key": "osmfKeyMulAdsAvail12346"
                    }
                ],
                "domain": "sandbox2.auditude.com",
                "mediaid": "psdk_000105",
                "zoneid": "121781"
            }     
        }
    },   
    "title": "VOD - DELETE TimeRange with Primetime ad decisioning Ads",
    "thumbnail": {
        "large": "https://example.com",
        "small": "https://example.com"
    },
    "type": "vod",
    "id": "vod_003"
}
```

