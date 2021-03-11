---
description: VODコンテンツの時間間隔を広告の時間として指定できます。
title: 範囲をマーク
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# 範囲をマーク{#mark-ranges}

VODコンテンツの時間間隔を広告の時間として指定できます。

この場合、`localTime`の`begin`と`end`の間の`TimeRanges`は、タイムラインで`AdBreak`としてマークされます。 その他の広告設定は無視されます。

>[!NOTE]
>
>コンテンツ内の特定の範囲のみを広告としてマークする場合（動的な広告挿入なし）は、`CustomRangeMetadata`インスタンスを作成し、タイプをMARK操作として指定して、定義したカスタム範囲を指定します。

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

