---
title: カスタム広告マーカー用の JSON オブジェクト
description: カスタム広告マーカー用の JSON オブジェクト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# カスタム広告マーカー用の JSON オブジェクト {#json-object-for-custom-ad-markers}

以下のコードブロックは、タイプがカスタム広告マーカーの場合の「details」JSON オブジェクトを定義します。

IFeedItemAdapter:getStreamMetadata() が返す MetadataNode には、次の 2 つのエントリが含まれます。
1. タイプのキーを持つエントリ `com.adobe.mediacore.metadata.DefaultMetadataKeys.CUSTOM_AD_MARKERS_METADATA_KEY` と、が返す MetadataNode のインスタンスの値 `TimeRangeCollection.toMetadata()`.
1. 2 つ目のエントリはタイプのキーを持ちます `com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` の値を *adjust-seek-position* 属性を以下に示します。

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
| adjust-seek-position | true または false。MetadataNode でキー com.adobe.mediacore.metadata.DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED の値を設定するために使用します。 |
| 時間範囲 | 各広告マーカーの時間範囲を示す JSON オブジェクトの配列。 各 JSON オブジェクトエントリは、 com.adobe.mediacore.utils.TimeRange のインスタンスにマッピングされます。 |
| time-ranges.begin | 広告マーカーの開始時間を示すミリ秒単位の値。 |
| time-ranges.end | 広告マーカーの終了時間を示すミリ秒単位の値。 |

カスタム広告マーカーの動作について詳しくは、 TVSDK のドキュメントを参照してください。
