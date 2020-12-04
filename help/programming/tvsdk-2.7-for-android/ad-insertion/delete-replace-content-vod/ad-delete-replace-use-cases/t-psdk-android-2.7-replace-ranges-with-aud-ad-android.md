---
description: VODコンテンツに広告を挿入できます。
seo-description: VODコンテンツに広告を挿入できます。
seo-title: 時間範囲の広告への置換
title: 時間範囲の広告への置換
uuid: 8f09560c-bca3-4662-bc58-6c9cd0892476
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# 時間範囲を広告{#replace-time-ranges-with-an-ad}に置換

VODコンテンツに広告を挿入できます。

`localTime`内の`begin`と`end`の間の`TimeRanges`は、タイムラインから削除されます。 これらの範囲は、`begin`から`begin+replaceDuration`の`AdBreak`に置き換えられます。 `replacement-duration`がパラメータとして存在しない場合、サーバは返される`Adbreak`に対して判断を行います。

>[!TIP]
>
>カスタム範囲には常に`replacement-duration`を指定する必要があります。 このカスタム範囲を置き換える広告がない場合は、0の`replacement-duration`を指定します。

1. 範囲をPrimetime ad decisioningadsに置き換えるには：

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
                   "type": "replace",
                   "time-range-list": [
                       {
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
       "title": "VOD - Replace TimeRange with Auditude Ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_003"
   }
   ```

