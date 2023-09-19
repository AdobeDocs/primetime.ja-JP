---
description: VOD コンテンツの時間間隔を広告の時間として指定できます。
title: 範囲をマーク
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# 範囲をマーク{#mark-ranges}

VOD コンテンツの時間間隔を広告の時間として指定できます。

この場合、 `TimeRanges` 次の期間 `begin` および `end` in `localTime` は、 `AdBreak` を使用します。 その他の広告設定は無視されます。

>[!NOTE]
>
>コンテンツ内の特定の範囲のみを広告としてマークする場合（動的な広告挿入を使用しない）、 `CustomRangeMetadata` インスタンスを作成し、定義されたカスタム範囲を持つ MARK 操作として型を指定します。

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
