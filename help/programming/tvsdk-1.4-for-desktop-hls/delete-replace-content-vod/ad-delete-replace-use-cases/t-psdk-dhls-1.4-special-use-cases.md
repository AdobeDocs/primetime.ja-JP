---
description: 'null'
seo-description: 'null'
seo-title: 特殊な使用例
title: 特殊な使用例
uuid: 066bc256-4fdf-4083-b23e-0a916b3b532f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 特殊な使用例{#special-use-cases}

TVSDKは、標準の広告設定よりもカスタム範囲設定を優先します。 例えば、MARK範囲が定義されている場合、広告の挿入設定は無視されます。 REPLACE範囲が定義されている場合、TVSDKは自動的にシグナリングモード `CustomRanges` を使用します。

1. `ReplaceRange` 置き換え時間なしで

   置換期間がない場合、実際の置換期間はサーバーによって決定されます。 この中に配置される広告の数は、サ `AdBreak` ーバーによっても決まります。

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

1. 置換期間を含むMARK範囲とDELETE範囲

   余分な置換期間は無視されます。
