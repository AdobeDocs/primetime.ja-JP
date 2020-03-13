---
description: VODコンテンツの時間間隔を広告の時間として指定できます。
seo-description: VODコンテンツの時間間隔を広告の時間として指定できます。
seo-title: 範囲のマーク
title: 範囲のマーク
uuid: eb99a1c2-6c0c-40a4-bac2-98dce45acfad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 範囲のマーク{#mark-ranges}

VODコンテンツの時間間隔を広告の時間として指定できます。

この場合、との間に `TimeRanges` は、タイ `begin` ムライ `end` ンで「 `localTime` アン」とし `AdBreak` てマークされます。 その他の広告設定は無視されます。

>[!NOTE]
>
>コンテンツ内の特定の範囲のみを広告としてマークする場合（動的な広告挿入を使用しない場合）は、インスタンスを作成し、定義したカスタム範囲を使用してMARK操作としてタイプを指定します。 `CustomRangeMetadata`

1. 範囲をマークします。

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

