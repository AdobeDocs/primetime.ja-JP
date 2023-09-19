---
description: TVSDK は、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に応答します。
title: 時間範囲エラーの例
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# 時間範囲エラーの例{#time-range-error-examples}

TVSDK は、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に応答します。

**DELETE時間範囲**

次の例では、交差する 4 つのDELETE時間範囲が定義されます。 TVSDK は、4 つの時間範囲を 1 つに結合し、実際の削除範囲が 0 ～ 50 秒になるようにします。

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

**時間範囲を置換**

次の例では、4 つの REPLACE 時間範囲が、時間範囲が競合して定義されています。 この場合、 TVSDK は 0 ～ 50 秒を 25 秒の広告で置き換えます。 後続の範囲に競合があるので、並べ替え順の最初の置き換え期間に合わせます。

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
