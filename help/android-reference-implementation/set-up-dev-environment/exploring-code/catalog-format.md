---
description: Primetimeリファレンスの実装では、応答にJSONベースのフィード形式を使用します。 この形式は、IFeedItemAdapterインターフェイスの実装を使用して解析されます。
seo-description: Primetimeリファレンスの実装では、応答にJSONベースのフィード形式を使用します。 この形式は、IFeedItemAdapterインターフェイスの実装を使用して解析されます。
seo-title: カタログ形式
title: カタログ形式
uuid: 6e1a526f-c0bb-403d-a792-666caf5479a5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# カタログ形式 {#catalog-format}

Primetimeリファレンスの実装では、応答にJSONベースのフィード形式を使用します。 この形式は、IFeedItemAdapterインターフェイスの実装を使用して解析されます。

>[!NOTE]
>
>このフィード形式は、参照実装で使用されるサンプル形式で、形式を解析し、フィードインターフェイスにマッピングする方法の例として機能します。 独自のフィードインターフェイス実装で独自の入力フィード形式を使用できます。

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

各フィードエントリは、次の特定の属性のセットを持つJSONオブジェクトです。

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
| `id` | フィードパブリッシングシステムによって設定される、コンテンツの一意の識別子/ガイド。 |
| `title` | コンテンツのタイトル。 |
| `description` | コンテンツの説明。 |
| `categories` | ユーザーの体験を高めるためにアプリケーションで使用できる、コンテンツのタグ付けされたカテゴリのリストです。 コンテンツのプロパティを読み取ります。 |
| `keywords` | コンマ区切りのキーワードのリスト。ユーザーの体験を高めるために、アプリケーションで使用できます。 コンテンツのプロパティを読み取ります。 |
| `isLive` | trueまたはfalse。ライブストリームかVODストリームかを示します。 |
| `content` | コンテンツの代替形式と対応するURLを持つJSONオブジェクトの配列。 例えば、f4mおよびm3u8形式のURLが存在する場合があります。 JSONオブジェクトの属性については、後述します。 |
| `thumbnails` | 様々なサムネールサイズのURLを持つJSONオブジェクトの配列です。 JSONオブジェクト属性は以下に定義します。 |
| `metadata` | コンテンツのメタデータを定義するJSONオブジェクト。現在、このメタデータは広告関連のメタデータに限定されています。 メタデータオブジェクトは以下で定義します。 |

次のコードブロックは、コンテンツオブジェクトの配列を形成するJSONオブジェクト **を定義しま**&#x200B;す。

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
| url | 指定した形式のビデオストリームのURL。 |

次のコードブロックは、thumbnailオブジェクトの配列を形成するJSONオブジェクトを **定義します**。

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
| 形式 | サムネールファイルの形式を示す文字列（例：JPEG、PNGなど）。 |
| height | サムネールの高さ。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| width | サムネールの幅。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| url | サムネールファイルのURL。 |

次のコードブロックは、メタデータオブジェクト **を定義しま**&#x200B;す。

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
| type | 値には、Primetime広告、ダイレクト広告の時間またはカスタム広告マーカーを使用できます。 <br/><br/>PSDKは、次のタイプのメタデータを組み込みでサポートします。Primetime広告サービング（Primetime広告）用のAuditude関連のメタデータ、広告URLを使用する直接広告の時間（ダイレクト広告の時間）、および各広告マーカー（カスタム広告マーカー）のTimeRangeを提供するカスタム広告マーカー。 各タイプには、メタデータを処理するPSDKに組み込みのAdProviderがあります。  <br/><br/>各JSON形式は、以下のように定義されています。 |
| details | 広告メタデータ属性を含めます。 両方のタイプの広告メタデータには、以下に定義する独自の属性セットがあります。 組み込み型の場合、含まれる属性は、その型に対してPSDKが期待するデータを定義します。 |
| 権利付与 | エンタイトルメント関連のメタデータ |
| id | Adobe Primetime pay-TVパスサービスに対する認証要求に使用されるメディアリソースID。 IDは、テキスト文字列またはHTMLエンコードされたmRSS文字列です。 認証が必要なメディアコンテンツには、有効なリソースIDが含まれている必要があります。 |

