---
description: VOD コンテンツの時間間隔を広告の時間として指定できます。
title: 範囲をマーク
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# 範囲をマーク {#mark-ranges}

VOD コンテンツの時間間隔を広告の時間として指定できます。

The `TimeRanges` 次の期間 `begin` および `end` in `localTime` は、 `AdBreak` を使用します。 その他の広告設定は無視されます。

>[!TIP]
>
>コンテンツ内の特定の範囲のみを広告としてマークし、動的な広告挿入を使用しない場合は、 `CustomRangeMetadata` インスタンスを作成し、型を as として指定します。 `MARK` 演算を指定します。

1. 範囲を上限マーク：

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
