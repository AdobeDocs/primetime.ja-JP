---
description: VODコンテンツの時間間隔を広告の時間として指定できます。
seo-description: VODコンテンツの時間間隔を広告の時間として指定できます。
seo-title: 範囲のマーク
title: 範囲のマーク
uuid: fa6047dc-9a12-42fa-9e58-8ee3a55fa866
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 範囲のマーク {#mark-ranges}

VODコンテンツの時間間隔を広告の時間として指定できます。

との間 `TimeRanges` のが、タ `begin` イムラ `end` イン `localTime` で「」としてマ `AdBreak` ークされます。 その他の広告設定は無視されます。

>[!TIP]
>
>コンテンツ内の特定の範囲のみを広告としてマークし、動的な広告挿入を使用しない場合は、インスタンスを作成し、定義したカスタム範囲を使用する操作としてタ `CustomRangeMetadata``MARK` イプを指定します。

1. Tp範囲をマーク：

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
                   "type": "mark",
               "adjust-seek-position" : true,   
                   "time-range-list": [
                     {
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
                       }
                    ]
   
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
