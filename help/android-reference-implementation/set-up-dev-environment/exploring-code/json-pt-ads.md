---
seo-title: Primetime広告のJSONオブジェクト
title: Primetime広告のJSONオブジェクト
uuid: acf968d2-9856-4ed6-a046-1ac17d176571
description: 次のコードブロックは、タイプ値がPrimetime広告の場合の詳細JSONオブジェクトを定義します。
seo-description: 次のコードブロックは、タイプ値がPrimetime広告の場合の詳細JSONオブジェクトを定義します。
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Primetime広告のJSONオブジェクト {#json-object-for-primetime-ads}

次のコードブロックは、タイプ値がPrimetime広告の場合の詳細JSONオブジェクトを定義します。

```
“metadata”: {
    “ad” :  {
        “type”: “Primetime ads”,
        “details”: {
            "domain": "sandbox2.auditude.com",
            "mediaid": "rom_asset_case_1",
            "zoneid": "109754",
            "targeting": [
                {
                    "key": "osmfKeyMulAdsAvail12346",
                    "value": "MulAdsAvail12346"
                }
            ]
        }
    }
}
```

| プロパティ | 説明 |
|---|---|
| ドメイン | 広告リクエストに使用するPrimetime広告ドメイン。 |
| mediaid | このコンテンツのPrimetime広告で設定されたメディア。 |
| ゾニード | Primetimeはzoneidを広告します。 詳しくは、Primetime広告のドキュメントを参照してください。 |
| ターゲット | コンテンツの特定の広告をターゲット設定するために使用されるキーと値のペアの配列。 |

これ [らの属性の値について詳しくは、com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) を参照してください。