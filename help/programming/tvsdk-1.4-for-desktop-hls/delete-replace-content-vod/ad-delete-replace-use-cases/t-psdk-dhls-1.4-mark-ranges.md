---
title: 範囲をマーク
description: 範囲をマーク
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '24'
ht-degree: 0%

---

# 範囲をマーク{#mark-ranges}

トンボ `TimeRanges` 次の期間 `begin` および `end` in `localTime` as a `AdBreak` タイムラインから。 その他の広告設定は無視されます。

1. 時間範囲をマークします。

   ```
   {   
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://d398890tia84ty.cloudfront.net/e2e-vod/cloudfront_vod_hls_tos_30fps.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "time-ranges": {
                   "type": "mark",
                   "adjust-seek-position" : true,   
                   "time-range-list": [ {
                       "begin": 0,
                       "end": 15000
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
                   } ]
   
               }
           }           
       },   
       "title": "VOD - MARK TimeRanges and no ads",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_004"
   }
   ```
