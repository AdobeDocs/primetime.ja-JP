---
title: 直接広告ブレークの JSON オブジェクト
description: タイプ値がダイレクト広告ブレークの場合に、JSON オブジェクトの詳細を説明します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 直接広告ブレークの JSON オブジェクト{#json-object-for-direct-ad-breaks}

次のコードブロックは、タイプ値が直接広告ブレークの場合の詳細 JSON オブジェクトを定義します。

The `MetadataNode` 返送者： `IFeedItemAdapter:getStreamMetadata()` タイプのキーを持つエントリが含まれます `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` および以下の詳細 JSON オブジェクト値の文字列表現の値。

```
“metadata”: { 
    “ad” :  { 
        “type”: “direct ad breaks”, 
        “details”: { 
            "ad-breaks": [ 
                { 
                    "tag": "break-001", 
                    "time": 0, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        }, 
                        { 
                        } 
                    ] 
                }, 
                { 
                    "tag": "break-002", 
                    "time": 300000, 
                    "replace": 0, 
                    "ad-list": [ 
                        { 
                        } 
                    ] 
                } 
            ] 
        } 
    } 
} 
```

| プロパティ | 説明 |
|---|---|
| `tag` | のタグフィールドにマッピングする文字列 `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `time` | 広告ブレークの開始時間を示し、の時間フィールドにマッピングされます。 `com.adobe.mediacore.timeline.advertising.AdBreak`. 値 0 はプリロール広告を示します。 |
| `replace` | 広告ブレークの置き換え時間を示し、 `replaceDuration` ～に入る `com.adobe.mediacore.timeline.advertising.AdBreak`. |
| `ad-list` | 特定の広告ブレーク中に再生される広告のリストは、 `List<Ad>` ～に入る `com.adobe.mediacore.timeline.advertising.AdBreak`. |

次のコードブロックは、ads-list 配列の JSON オブジェクトを定義します。

```
"ad-list": [ 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 15000, 
        "tag": "1st break - 1st ad" 
    }, 
    { 
        "url": "https://cdn.auditude.com/player/downloads/data/espn/ads/csx/prog_index.m3u8", 
        "duration": 30000, 
        "tag": "1st break - 2nd ad" 
    } 
], 
```

| プロパティ | 説明 |
|---|---|
| `url` | 広告コンテンツの URL は、の url フィールドにマッピングされます。 `com.adobe.mediacore.timeline.advertising.Ad`. |
| `duration` | 広告の期間は、 `com.adobe.mediacore.timeline.advertising.Ad`. |
| `tag` | 説明文字列。 |
