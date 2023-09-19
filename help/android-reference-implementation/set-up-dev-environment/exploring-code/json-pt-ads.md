---
title: Primetime 広告の JSON オブジェクト
description: 以下のコードブロックは、タイプ値が Primetime 広告の場合の詳細 JSON オブジェクトを定義します。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Primetime 広告の JSON オブジェクト {#json-object-for-primetime-ads}

以下のコードブロックは、タイプ値が Primetime 広告の場合の詳細 JSON オブジェクトを定義します。

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
| ドメイン | 広告リクエストに使用する Primetime 広告ドメイン。 |
| mediaid | このコンテンツに対して Primetime 広告で設定された mediaid。 |
| zoneid | Primetime は、zoneid を広告します。 詳しくは、 Primetime 広告のドキュメントを参照してください。 |
| ターゲティング | コンテンツの特定の広告のターゲティングに使用されるキーと値のペアの配列。 |

詳しくは、 [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) を参照してください。
