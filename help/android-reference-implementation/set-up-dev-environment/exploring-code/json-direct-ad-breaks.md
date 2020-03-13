---
seo-title: ダイレクト広告の時間のJSONオブジェクト
title: ダイレクト広告の時間のJSONオブジェクト
uuid: ffb901f4-0a8b-40fe-b6ba-5ffebc324cf2
description: タイプ値がダイレクト広告の時間の場合にJSONオブジェクトの詳細を表示します
seo-description: タイプ値がダイレクト広告の時間の場合にJSONオブジェクトの詳細を表示します
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ダイレクト広告の時間のJSONオブジェクト{#json-object-for-direct-ad-breaks}

次のコードブロックは、タイプ値がダイレクト広告の時間の場合の詳細JSONオブジェクトを定義します。

が返 `MetadataNode` すエ `IFeedItemAdapter:getStreamMetadata()` ントリには、次の詳細JSONオブジェ `com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY` クト値を表す文字列表現のキーと値のエントリが含まれます。

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
| `tag` | のタグフィールドにマップする文字列 `com.adobe.mediacore.timeline.advertising.AdBreak`。 |
| `time` | 広告の時間の開始時間を示し、の時間フィールドにマップしま `com.adobe.mediacore.timeline.advertising.AdBreak`す。 値0はプリロール広告を示します。 |
| `replace` | 広告の時間の置き換えの時間を示し、内のフィールドにマ `replaceDuration` ップしま `com.adobe.mediacore.timeline.advertising.AdBreak`す。 |
| `ad-list` | 特定の広告の時間中に再生される広告のリストは、のフィールドにマッピ `List<Ad>` ングされま `com.adobe.mediacore.timeline.advertising.AdBreak`す。 |

次のコードブロックは、ads-list配列のJSONオブジェクトを定義します。

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
| `url` | 広告コンテンツのURLは、のurlフィールドにマップされま `com.adobe.mediacore.timeline.advertising.Ad`す。 |
| `duration` | 広告の期間は、の期間フィールドにマップされます `com.adobe.mediacore.timeline.advertising.Ad`。 |
| `tag` | 説明文字列。 |

