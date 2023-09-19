---
title: 特別な使用例
description: 特別な使用例
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# 特別な使用例{#special-use-cases}

TVSDK は、標準の広告設定よりもカスタム範囲設定を優先します。 例えば、MARK 範囲が定義されている場合、広告の挿入設定は無視されます。 REPLACE 範囲が定義されている場合、 TVSDK は `CustomRanges` シグナリングモード。

1. `ReplaceRange` 置き換え時間なしで

   交換期間が指定されていない場合は、実際の交換期間がサーバーによって決定されます。 この中に配置された広告の数 `AdBreak` はサーバーによっても決まります。

   ```
   {
       "properties": [],
       "stream": {
           "manifests": [ {
               "url": "https://. . ./vanilla/index.m3u8",
               "type": "hls"
           } ],
           "metadata": {
               "signaling-mode": "custom time ranges",
               "time-ranges": {
                   "type": "replace",
                   "adjust-seek-position": true,
                   "time-range-list": [{
                   "begin": 0,
                   "end": 30000
               }, {
                   "begin": 60000,
                   "end": 75000
               }, {
                   "begin": 255000,
                   "end": 300000
               } ]
               },
               "ad": {             
                   "domain": "sandbox2.auditude.com",
                   "mediaid": "psdk_000105",
                   "zoneid": "121781"
               }     
           }
       },
       "title": "Verify 30Sec Pre-Roll, 15 Sec Mid roll Ad and 
       45 second Post-Roll can be replaced in one shot.",
       "thumbnail": {
           "large": "https://example.com",
           "small": "https://example.com"
       },
       "type": "vod",
       "id": "vod_001"
   }
   ```

1. 置き換え時間のある MARK およびDELETE範囲

   追加の置き換え期間は無視されます。
