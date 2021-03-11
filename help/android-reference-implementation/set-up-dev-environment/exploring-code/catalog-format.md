---
description: Primetimeリファレンスの実装では、応答にJSONベースのフィード形式が使用されます。 この形式は、IFeedItemAdapterインターフェイスの実装を使用して解析されます。
title: カタログ形式
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---


# カタログ形式{#catalog-format}

Primetimeリファレンスの実装では、応答にJSONベースのフィード形式が使用されます。 この形式は、IFeedItemAdapterインターフェイスの実装を使用して解析されます。

>[!NOTE]
>
>このフィード形式は、参照の実装で使用されるサンプル形式で、形式を解析してフィードインターフェイスにマッピングする方法の例として機能します。 独自のフィードインターフェイス実装で、独自の入力フィード形式を使用できます。

高レベルでは、形式はコンテンツエントリの配列で構成されます。 各エントリは、ライブまたはVODで公開されたビデオコンテンツを表します。

```
{
    "entries": [
        {
        },
        {
        },
        ...
    ]
}
```

各フィードエントリは、指定された属性のセットを持つJSONオブジェクトです。

```
{
    "entries": [
        
            "id": "episode1",
            "title": "My episode1",
            "description": "This is an episode.",
            "categories": "documentary, educational, children",
            "keywords": "List, of, comma, separated, keywords",
            "isLive": false,
            "content":  [
                
                },
                
                },
            ],
            "thumbnails": [
                
                },
                
                }
            ]
            "metadata": 
            } 
        }
    ]
}
```

| プロパティ | 説明 |
|---|---|
| `id` | フィードパブリッシングシステムによって設定される、コンテンツの一意の識別子/ガイドです。 |
| `title` | コンテンツのタイトル。 |
| `description` | 内容の説明。 |
| `categories` | コンテンツに対してタグ付けされたカテゴリのリストで、ユーザーの体験を高めるためにアプリケーションで使用できます。 コンテンツのプロパティを読み取ります。 |
| `keywords` | カンマ区切りのキーワードのリストは、ユーザーの操作性を高めるためにアプリで使用できます。 コンテンツのプロパティを読み取ります。 |
| `isLive` | trueまたはfalse。これは、それがライブストリームかVODストリームかを示します。 |
| `content` | コンテンツの代替形式と対応するURLを持つJSONオブジェクトの配列。 例えば、f4mおよびm3u8形式のURLがあるとします。 JSONオブジェクト属性については、以下で説明します。 |
| `thumbnails` | 様々なサムネールサイズのURLを持つJSONオブジェクトの配列。 JSONオブジェクト属性は以下に定義します。 |
| `metadata` | コンテンツのメタデータを定義するJSONオブジェクト。現在、このメタデータは広告関連のメタデータに制限されています。 メタデータオブジェクトは次のように定義します。 |

次のコードブロックは、**contentオブジェクト**&#x200B;の配列を形成するJSONオブジェクトを定義します。

```
"content":  [
    {
        "format": "M3U8",
        "url": "https://adobeprimetime-f.akamaihd.net/i/
<i>longstringofcharacters</i>/
                 Episode_,640x360_1000,640x360_700,_b.mp4.csmil/master.m3u8",
        "language": "en"
    }  
],
```

| プロパティ | 説明 |
|--- |--- |
| 形式 | Androidの場合は、m3u8形式である必要があります。 |
| url | 指定した形式のビデオストリームへのURL。 |

次のコードブロックは、**thumbnailオブジェクト**&#x200B;の配列を形成するJSONオブジェクトを定義します。

```
"thumbnails": [
    {
        "format": "JPEG",
        "height":  "90",
        "width": "160",
        "url": "https://example.com/small.jpg"
    },
    {
        "format": "JPEG",
        "height": "450",
        "width": "800",
        "url": "https://example.com/large.jpg"
    }
],
```

| プロパティ | 説明 |
|---|---|
| 形式 | サムネールファイルの形式を示す文字列（JPEG、PNGなど）。 |
| height | サムネールの高さ。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| width | サムネールの幅。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| url | サムネールファイルのURLです。 |

次のコードブロックは、**metadataオブジェクト**&#x200B;を定義します。

```
"metadata" : {
    "ad" : {
        "type" : "",
        "details" : {
        }
    }
    "entitlement" : {
        "id" : ""
    }
}
```

| プロパティ | 説明 |
|--- |--- |
| ad | 広告関連のメタデータ。 |
| type | 値には、Primetime広告、ダイレクト広告の時間またはカスタム広告マーカーを使用できます。 <br/><br/>PSDKは、次のタイプのメタデータを組み込みでサポートします。Primetime広告配信(Primetime Ads)用のAuditude関連のメタデータ、広告URLを使用する直接広告の時間(Direct Ad Breaks)、および各広告マーカー（カスタム広告マーカー）のTimeRangeを提供するカスタム広告マーカー。各型には、メタデータを処理するPSDKに組み込まれているAdProviderがあります。  <br/><br/>これらの各JSON形式は、次のように定義されています。 |
| details | 広告メタデータ属性が含まれます。 広告メタデータの両方のタイプには、以下に定義する独自の属性セットがあります。 組み込み型の場合、含まれる属性は、その型に対してPSDKが予期するデータを定義します。 |
| 権利付与 | エンタイトルメント関連のメタデータ |
| id | Adobe Primetime有料テレビパスサービスに対する承認要求に使用されるメディアリソースID。 IDは、テキスト文字列またはHTMLエンコードされたmRSS文字列のいずれかです。 認証が必要なメディアコンテンツには、有効なリソースIDが含まれている必要があります。 |

