---
description: Primetime リファレンスの実装では、応答に JSON ベースのフィード形式が使用されます。 この形式は、IFeedItemAdapter インターフェイスの実装を使用して解析されます。
title: カタログ形式
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# カタログ形式 {#catalog-format}

Primetime リファレンスの実装では、応答に JSON ベースのフィード形式が使用されます。 この形式は、IFeedItemAdapter インターフェイスの実装を使用して解析されます。

>[!NOTE]
>
>このフィード形式は、参照実装で使用されるサンプル形式で、形式を解析してフィードインターフェイスにマッピングする方法の例として機能します。 独自のフィードインターフェイスの実装で、独自の入力フィード形式を使用できます。

高レベルでは、形式はコンテンツエントリの配列で構成されます。 各エントリは、ライブまたは VOD で公開されたビデオコンテンツを表します。

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

各フィードエントリは、次に示す一連の属性を持つ JSON オブジェクトです。

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
| `id` | フィードパブリッシングシステムによって設定されたコンテンツの一意の識別子またはガイドです。 |
| `title` | コンテンツのタイトル。 |
| `description` | コンテンツの説明。 |
| `categories` | コンテンツ用にタグ付けされたカテゴリのリストで、ユーザーのエクスペリエンスを強化するためにアプリケーションで使用できます。 コンテンツのプロパティを読み取ります。 |
| `keywords` | コンマ区切りのキーワードのリストは、ユーザーのエクスペリエンスを向上させるためにアプリケーションで使用できます。 コンテンツのプロパティを読み取ります。 |
| `isLive` | true または false。ライブストリームか VOD ストリームかを示します。 |
| `content` | コンテンツの代替形式と対応する URL を持つ JSON オブジェクトの配列。 例えば、f4m および m3u8 形式用の URL が存在する可能性があります。 JSON オブジェクトの属性については、後述します。 |
| `thumbnails` | 様々なサムネールサイズの URL を持つ JSON オブジェクトの配列。 JSON オブジェクトの属性は、以下で定義します。 |
| `metadata` | コンテンツのメタデータを定義する JSON オブジェクト。現在、このメタデータは広告関連のメタデータに限定されています。 メタデータオブジェクトは、以下で定義します。 |

次のコードブロックは、 **コンテンツオブジェクト**:

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
| 形式 | Android の場合は、m3u8 形式にする必要があります。 |
| url | 指定された形式のビデオストリームの URL。 |

次のコードブロックは、 **thumbnail オブジェクト**:

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
| 形式 | サムネールファイルの形式を示す文字列 ( 例：JPEG、PNG など )。 |
| 高さ | サムネールの高さです。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| 幅 | サムネールの幅。 参照アプリケーションでは、高さと幅が最も小さいサムネールが小さいサムネールとして返され、幅と高さが最も大きいサムネールが大きいサムネールとして返されます。 |
| url | サムネールファイルの URL。 |

次のコードブロックは、 **メタデータオブジェクト**:

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
| 広告 | 広告関連のメタデータ。 |
| type | 値には、Primetime 広告、ダイレクト広告ブレークまたはカスタム広告マーカーを使用できます。 <br/><br/>PSDK は、Primetime Ad Serving(Primetime Ads) のAuditude関連メタデータ、広告 URL を使用した直接広告ブレーク (Direct Ad Breaks)、および各広告マーカー (Custom Ad Markers) の TimeRange を提供するカスタム広告マーカーの各タイプのメタデータを組み込みでサポートしています。 各タイプには、メタデータを処理する PSDK に組み込まれている AdProvider があります。  <br/><br/>これらのそれぞれの JSON 形式は、以下で定義されています。 |
| 詳細 | 広告のメタデータ属性を含めます。 どちらのタイプの広告メタデータも、以下で定義する独自の属性セットを持ちます。 組み込み型の場合、含まれる属性は、その型の PSDK で想定されるデータを定義します。 |
| 権利付与 | 権利付与関連メタデータ |
| id | Adobe Primetime Pay-TV パスサービスに対する認証要求に使用されるメディアリソース ID。 この ID は、テキスト文字列またはHTMLエンコードされた mRSS 文字列です。 認証が必要なメディアコンテンツには、有効なリソース ID が含まれている必要があります。 |
