---
description: TVSDKは、特定の問題に従って時間範囲エラーを処理し、不適切に定義された時間範囲を結合または並べ替えます。
seo-description: TVSDKは、特定の問題に従って時間範囲エラーを処理し、不適切に定義された時間範囲を結合または並べ替えます。
seo-title: 広告の削除と置換のエラー処理
title: 広告の削除と置換のエラー処理
uuid: ab153591-0011-44b4-87f9-be0302c2295e
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 広告の削除と置換のエラー処理 {#ad-deletion-and-replacement-error-handling}

TVSDKは、特定の問題に従って時間範囲エラーを処理し、不適切に定義された時間範囲を結合または並べ替えます。

TVSDKは、デフォルトの結 `timeRanges` 合と順序変更を行うことでエラーを処理します。 まず、顧客定義の時間範囲を開始時間で並べ *替え* ます。 この並べ替え順に基づいて、隣接する範囲を結合し、範囲間にサブセットや交差がある場合は範囲を結合します。

TVSDKは、次のように時間範囲エラーを処理します。

* 順序が正しくありません — TVSDKは時間範囲を並べ替えます。
* サブセット — 時間範囲のサブセットを結合します。
* 交差 — 交差する時間範囲を結合します。
* 置換範囲の競合 — 競合するグループに表示される最も古いものから置換期間 `timeRange` を選択します。

TVSDKは、シグナリングモードの競合を次のように処理します。

* REPLACE範囲が定義されている場合、TVSDKはシグナリングモードをCUSTOM_RANGEに自動的に変更します。
* DELETE範囲またはMARK範囲が定義され、シグナリングモードがCUSTOM_RANGEの場合、TVSDKはこれらの範囲を削除またはマークします。 この場合、広告挿入はありません。
* DELETE範囲またはMARK範囲で置換期間が定義されている場合、TVSDKはこの期間を無視します。

サーバーが有効な値を返さない場合 `AdBreaks`:

* TVSDKは、空ののを生成し、 `NOPTimelineOperation` 処理します `AdBreak`。 広告は再生されません。

## 時間範囲エラーの例 {#time-range-error-examples}

TVSDKは、誤った時間範囲指定に対して、必要に応じて時間範囲を結合または置き換えることで応答します。

次の例では、交差する4つのDELETE時間範囲が定義されています。 TVSDKは、4つの時間範囲を1つに結合し、実際の削除範囲が0 ～ 50秒になるようにします。

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

次の例では、4つのREPLACE時間範囲が矛盾する時間範囲で定義されています。 この場合、TVSDKは0 ～ 50秒を25秒の広告で置き換えます。 後続の範囲に矛盾があるので、並べ替え順の最初の置換期間に合わせます。

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
