---
description: TVSDKは、不適切に定義された時間範囲を結合または順序変更することで、特定の問題に従って時間範囲エラーを処理します。
title: 広告の削除と置換のエラー処理
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# 広告の削除と置換のエラー処理{#ad-deletion-and-replacement-error-handling}

TVSDKは、不適切に定義された時間範囲を結合または順序変更することで、特定の問題に従って時間範囲エラーを処理します。

TVSDKは、`timeRanges`エラーを処理するために、デフォルトの結合と並べ替えを行います。 まず、顧客定義の時間範囲を&#x200B;*begin*&#x200B;時間で並べ替えます。 この並べ替え順に基づいて、隣接する範囲を結合し、範囲間にサブセットや交差がある場合は範囲を結合します。

TVSDKは、時間範囲エラーを次のように処理します。

* 順序が正しくありません — 時間範囲を並べ替えます。
* サブセット — 時間範囲のサブセットを結合します。
* 交差 — 交差する時間範囲を結合します。
* 置換範囲の競合 — 競合するグループ内で最も古い`timeRange`から置換期間を選択します。

TVSDKは、シグナリングモードの競合を次のように処理します。

* REPLACE範囲が定義されている場合、シグナリングモードが自動的にCUSTOM_RANGEに変更されます。
* DELETE範囲またはMARK範囲が定義され、シグナリングモードがCUSTOM_RANGEの場合、TVSDKはこれらの範囲を削除またはマークします。 この場合、広告挿入はありません。
* DELETE範囲またはMARK範囲が置換期間を定義している場合、TVSDKはこの期間を無視します。

サーバが有効な`AdBreaks`を返さない場合：

* TVSDKは、空の`AdBreak`の`NOPTimelineOperation`を生成して処理します。 広告は再生されません。

## 時間範囲エラーの例{#time-range-error-examples}

TVSDKは、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に対応します。

次の例では、交差する4つのDELETE時間範囲が定義されています。 TVSDKは、4つの時間範囲を1つに結合するので、実際の削除範囲は0 ～ 50秒になります。

```
"time-ranges": {
    "type": "delete",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000
    }, {
        "begin": 20000,
        "end": 50000
    }, {
        "begin": 0,
        "end": 30000
    }, {
        "begin": 30000,
        "end": 40000
    } ]
}
```

次の例では、時間範囲に矛盾がある4つのREPLACE時間範囲が定義されています。 この場合、TVSDKは0 ～ 50秒を25秒の広告で置き換えます。 後続の範囲に矛盾があるので、ソート順での最初の置換期間に合わせて変更されます。

```
"time-ranges": {
    "type": "replace",
    "time-range-list": [ {
        "begin": 10000,
        "end": 35000,
        "replace-duration": 15000
    }, {
        "begin": 20000,
        "end": 50000,
        "replace-duration": 20000
    }, {
        "begin": 0,
        "end": 30000,
        "replace-duration": 25000
    }, {
        "begin": 30000,
        "end": 40000,
        "replace-duration": 30000
    } ]
}
```
