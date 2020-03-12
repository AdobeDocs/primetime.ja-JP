---
description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-description: localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。
seo-title: 範囲の削除
title: 範囲の削除
uuid: 637829a7-efa8-4b83-9a04-ef01c043621f
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 範囲の削除{#delete-ranges}

localTimeでbeginからendまでのTimeRangesは、タイムラインから削除できます。

>[!TIP]
>
>コンテンツから特定の範囲のみを削除するには、インスタンスを作 `CustomRangeMetadata` 成し、定義済みのカスタム範囲を持つ操 `DELETE` 作としてタイプを指定します。

広告マップは、広告サーバーの定義に従って使用する必要があります。

1. Adobe Primetime ad decisioning広告の範囲を削除するには：

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

