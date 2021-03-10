---
title: 特殊な使用例
description: 特殊な使用例
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# 特殊な使用例{#special-use-cases}

TVSDKは、標準の広告設定よりもカスタム範囲設定を優先します。 例えば、MARK範囲が定義されている場合、広告の挿入設定は無視されます。 REPLACE範囲が定義されている場合、TVSDKは自動的に`CustomRanges`シグナリングモードを使用します。

1. `ReplaceRange` 置き換え時間なしで

   置き換え期間がない場合、実際の置き換え期間はサーバーによって決定されます。 この`AdBreak`に配置される広告の数もサーバーによって決定されます。

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

1. 置換期間のあるMARK範囲とDELETE範囲

   余分な置換期間は無視されます。
