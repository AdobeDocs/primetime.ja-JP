---
description: VOD コンテンツに広告を挿入できます。
title: 時間範囲を広告で置き換える
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# 時間範囲を広告で置き換える {#replace-time-ranges-with-an-ad}

VOD コンテンツに広告を挿入できます。

The `TimeRanges` 次の期間 `begin` および `end` in `localTime` がタイムラインから削除されました。 これらの範囲は、 `AdBreak` / `begin` から `begin+replaceDuration`. 次の場合、 `replacement-duration` がパラメーターとして存在しない場合、サーバーは返された `Adbreak`.

>[!TIP]
>
>常に `replacement-duration` カスタム範囲の場合。 このカスタム範囲を置き換える広告がない場合は、 `replacement-duration` / 0

1. 範囲を Primetime ad decisioningads に置き換えるには：

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
