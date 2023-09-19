---
description: localTime で begin から end までの TimeRanges をタイムラインから削除できます。
title: 範囲を削除
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 0%

---

# 範囲を削除{#delete-ranges}

localTime で begin から end までの TimeRanges をタイムラインから削除できます。

>[!NOTE]
>
>コンテンツから特定の範囲のみを削除し、広告マップを広告サーバーで定義されたとおりに使用する必要がある場合は、 `CustomRangeMetadata` インスタンスを作成し、定義されたカスタム範囲を持つDELETE操作として型を指定します。

Adobe Primetime Ad Decisioning 広告を含む範囲を削除します。

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
