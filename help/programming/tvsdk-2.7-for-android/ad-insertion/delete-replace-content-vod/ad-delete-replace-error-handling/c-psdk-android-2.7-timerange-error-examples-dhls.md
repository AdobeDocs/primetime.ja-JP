---
description: TVSDKは、誤った時間範囲指定に対して、必要に応じて時間範囲を結合または置き換えることで応答します。
seo-description: TVSDKは、誤った時間範囲指定に対して、必要に応じて時間範囲を結合または置き換えることで応答します。
seo-title: 時間範囲エラーの例
title: 時間範囲エラーの例
uuid: f6cc1e61-8f42-4559-b643-2134180a8c5e
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 時間範囲エラーの例{#time-range-error-examples}

TVSDKは、誤った時間範囲指定に対して、必要に応じて時間範囲を結合または置き換えることで応答します。

**DELETE時間範囲**

次の例では、交差する4つのDELETE時間範囲が定義されています。 TVSDKは、4つの時間範囲を1つに結合し、実際の削除範囲が0 ～ 50秒になるようにします。

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000
        },
        {
            "begin": 20000,
            "end": 50000
        },
        {
            "begin": 0,
            "end": 30000
        },
        {
            "begin": 30000,
            "end": 40000
        }
    ]
}
```

**REPLACE時間範囲**

次の例では、4つのREPLACE時間範囲が矛盾する時間範囲で定義されています。 この場合、TVSDKは0 ～ 50秒を25秒の広告で置き換えます。 後続の範囲に矛盾があるので、並べ替え順の最初の置換期間に合わせます。

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [
        {
            "begin": 10000,
            "end": 35000,
            "replace-duration": 15000
        },
        {
            "begin": 20000,
            "end": 50000,
            "replace-duration": 20000
        },
        {
            "begin": 0,
            "end": 30000,
            "replace-duration": 25000
        },
        {
            "begin": 30000,
            "end": 40000,
            "replace-duration": 30000
        }
    ]
}
```

