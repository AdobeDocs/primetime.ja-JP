---
description: VODコンテンツに広告を挿入できます。
seo-description: VODコンテンツに広告を挿入できます。
seo-title: 時間範囲を広告に置換
title: 時間範囲を広告に置換
uuid: 8f09560c-bca3-4662-bc58-6c9cd0892476
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# 時間範囲を広告に置換 {#replace-time-ranges-with-an-ad}

VODコンテンツに広告を挿入できます。

との間 `TimeRanges` のがタ `begin` イムラ `end` インか `localTime` ら削除されます。 これらの範囲は、「～」に置き換 `AdBreak` えら `begin` れま `begin+replaceDuration`す。 がパラメータ `replacement-duration` ーとして存在しない場合、サーバーは返された値に基づいて判断を行いま `Adbreak`す。

>[!TIP]
>
>カスタム範囲には、常にを指定 `replacement-duration` する必要があります。 このカスタム範囲を置き換える広告がない場合は、0を指 `replacement-duration` 定します。

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

