---
description: TVSDKは、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に対応します。
title: 時間範囲エラーの例
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# 時間範囲エラーの例{#time-range-error-examples}

TVSDKは、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に対応します。

**DELETE時間範囲**

次の例では、交差する4つのDELETE時間範囲が定義されています。 TVSDKは、4つの時間範囲を1つに結合するので、実際の削除範囲は0 ～ 50秒になります。

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

次の例では、時間範囲に矛盾がある4つのREPLACE時間範囲が定義されています。 この場合、TVSDKは0 ～ 50秒を25秒の広告で置き換えます。 後続の範囲に矛盾があるので、ソート順での最初の置換期間に合わせて変更されます。

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
