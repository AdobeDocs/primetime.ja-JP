---
title: カスタム広告マーカーのJSONオブジェクト
description: カスタム広告マーカーのJSONオブジェクト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# カスタム広告マーカー{#json-object-for-custom-ad-markers}のJSONオブジェクト

下のコードブロックは、タイプがカスタム広告マーカーの場合に、「details」 JSONオブジェクトを定義します。

IFeedItemAdapter:getStreamMetadata()が返すMetadataNodeには、次の2つのエントリが含まれています。
1. キーが`com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY`で、`TimeRangeCollection.toMetadata()`が返すMetadataNodeのインスタンスの値を持つエントリ。
1. 2番目のエントリは、`com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED`型のキーで、下の&#x200B;*adjust-seek-position*&#x200B;属性の値を持ちます。

```
“metadata”: {
    “ad” :  {
        “type”: “custom ad markers”,
        “details”: {
            "adjust-seek-position": true,
            "time-ranges": [
                {
                    "begin": 5000,
                    "end":15000
                },
                {
                    "begin": 120000,
                    "end":135000
                }
            ]
        }
    }
}
```

| プロパティ | 説明 |
|---|---|
| adjust-seek-position | trueまたはfalse。MetadataNodeのキーcom.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLEDの値を設定するために使用されます。 |
| 時間範囲 | 各広告マーカーの時間範囲を示すJSONオブジェクトの配列。 各JSONオブジェクトエントリは、com.adobe.mediacore.utils.TimeRangeのインスタンスにマップされます。 |
| time-ranges.begin | 広告マーカーの開始時間を示すミリ秒単位の値。 |
| time-ranges.end | 広告マーカーの終了時間を示すミリ秒単位の値。 |

カスタム広告マーカーの動作方法について詳しくは、TVSDKのドキュメントを参照してください。
