---
title: Primetime広告のJSONオブジェクト
description: 以下のコードブロックは、タイプ値がPrimetime adsの場合に、details JSONオブジェクトを定義します。
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---


# Primetime広告のJSONオブジェクト{#json-object-for-primetime-ads}

以下のコードブロックは、タイプ値がPrimetime adsの場合に、details JSONオブジェクトを定義します。

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
| domain | 広告リクエストに使用するPrimetime広告ドメイン。 |
| mediaid | このコンテンツ用にPrimetime広告で設定されたメディア。 |
| zoneid | Primetime広告はzoneidです。 詳しくは、Primetime広告のドキュメントを参照してください。 |
| ターゲット | コンテンツの特定の広告をターゲット設定するために使用されるキー/値のペアの配列。 |

これらの属性の値の詳細については、[com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html)を参照してください。