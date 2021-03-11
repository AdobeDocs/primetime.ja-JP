---
title: 直接広告の時間のJSONオブジェクト
description: タイプ値がダイレクト広告ブレークの場合のJSONオブジェクトの詳細
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# ダイレクト広告ブレークのJSONオブジェクト{#json-object-for-direct-ad-breaks}

次のコードブロックは、タイプ値が直接広告ブレークの場合のdetails JSONオブジェクトを定義します。

`IFeedItemAdapter:getStreamMetadata()`から返される`MetadataNode`には、`com.adobe.mediacore.metadata.DefaultMetadataKeys.JSON_METADATA_KEY`型のキーと、下の詳細JSONオブジェクト値の文字列表現の値を持つエントリが含まれます。

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
| `tag` | `com.adobe.mediacore.timeline.advertising.AdBreak`内のタグフィールドにマップする文字列。 |
| `time` | 広告の時間の開始時間を示し、`com.adobe.mediacore.timeline.advertising.AdBreak`の時間フィールドにマップします。 値0はプリロール広告を示します。 |
| `replace` | 広告の時間の置き換え時間を示し、`com.adobe.mediacore.timeline.advertising.AdBreak`の`replaceDuration`フィールドにマップします。 |
| `ad-list` | 特定の広告の時間中に再生される広告のリストは、`com.adobe.mediacore.timeline.advertising.AdBreak`の`List<Ad>`フィールドにマッピングされます。 |

次のコードブロックは、広告 —リスト配列のJSONオブジェクトを定義します。

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
| `url` | 広告コンテンツへのURLは、`com.adobe.mediacore.timeline.advertising.Ad`のurlフィールドにマップされます。 |
| `duration` | 広告の長さは、`com.adobe.mediacore.timeline.advertising.Ad`の継続時間フィールドにマップされます。 |
| `tag` | 説明文字列。 |

