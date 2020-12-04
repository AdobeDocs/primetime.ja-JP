---
description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-title: 範囲の削除
title: 範囲の削除
uuid: 2aaea7a0-5d52-49a1-901c-f71e4b081d91
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# 範囲を削除{#delete-ranges}

`localTime`内の`begin`と`end`の間の`TimeRanges`は、タイムラインから削除できます。

>[!TIP]
>
>コンテンツから特定の範囲のみを削除するには、`CustomRangeMetadata`インスタンスを作成し、定義したカスタム範囲を持つ`DELETE`操作としてタイプを指定します。

広告マップは、広告サーバーの定義に従って使用する必要があります。

1. Adobe PrimetimeAd Decisioning広告の範囲を削除するには：

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [
               {
                   "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
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
       "title": "VOD - DELETE TimeRange with xm-replace_text Phrase Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   },
   ```
