---
seo-title: カスタム広告マーカーのJSONオブジェクト
title: カスタム広告マーカーのJSONオブジェクト
uuid: 2c05d9ce-a22f-4829-bfea-9dcf0dc7cd6d
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# カスタム広告マーカーのJSONオブジェクト {#json-object-for-custom-ad-markers}

以下のコードブロックは、タイプがカスタム広告マーカーの場合に、「details」JSONオブジェクトを定義します。

IFeedItemAdapter:getStreamMetadata()によって返されるMetadataNodeには、次の2つのエントリが含まれます。
1. によって返されるMetadataNodeのイ `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` ンスタンスのタイプと値のキーを持つエントリ `TimeRangeCollection.toMetadata()`。
1. 2つ目のエントリは、下の `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` adjust-seek-position属性の値を持つタ *イプのキー* です。

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
| 時間範囲 | 各広告マーカーの時間範囲を示すJSONオブジェクトの配列です。 各JSONオブジェクトエントリは、com.adobe.mediacore.utils.TimeRangeのインスタンスにマップされます。 |
| time-ranges.begin | 広告マーカーの開始時間を示すミリ秒単位の値。 |
| time-ranges.end | 広告マーカーの終了時間を示すミリ秒単位の値。 |

カスタム広告マーカーの動作方法について詳しくは、TVSDKのドキュメントを参照してください。
