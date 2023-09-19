---
description: TVSDK は、不適切に定義された時間範囲の結合または並べ替えを行い、特定の問題に従って時間範囲エラーを処理します。
title: 広告の削除と置き換えのエラー処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 広告の削除と置き換えのエラー処理 {#ad-deletion-and-replacement-error-handling}

TVSDK は、不適切に定義された時間範囲の結合または並べ替えを行い、特定の問題に従って時間範囲エラーを処理します。

TVSDK が扱う操作 `timeRanges` デフォルトの結合と並べ替えを実行することによるエラー。 最初に、顧客定義の時間範囲を *開始* 時間。 この並べ替え順に基づいて、隣接する範囲が結合され、範囲間にサブセットや交差がある場合はそれらの範囲が結合されます。

TVSDK は、次のように時間範囲エラーを処理します。

* 順序が正しくありません — TVSDK は、時間範囲を並べ替えます。
* サブセット — 時間範囲サブセットを結合します。
* 交差 — 交差する時間範囲を結合します。
* 範囲の置き換えの競合 — TVSDK は最も早く現れる期間から置き換え期間を選択します `timeRange` 競合するグループ内。

TVSDK は、シグナリングモードの競合を次のように処理します。

* REPLACE 範囲が定義されている場合、 TVSDK はシグナリングモードを自動的に CUSTOM_RANGE に変更します。
* DELETE範囲または MARK 範囲が定義され、シグナリングモードが CUSTOM_RANGE の場合、 TVSDK はこれらの範囲を削除またはマークします。 この場合、広告挿入はありません。
* DELETE範囲または MARK 範囲で置き換え期間が定義されている場合、 TVSDK はこの期間を無視します。

サーバーが有効なを返さない場合 `AdBreaks`:

* TVSDK が `NOPTimelineOperation` 空の `AdBreak`. 広告は再生されません。

## 時間範囲エラーの例 {#time-range-error-examples}

TVSDK は、時間範囲を必要に応じて結合または置き換えることで、誤った時間範囲指定に応答します。

次の例では、交差する 4 つのDELETE時間範囲が定義されます。 TVSDK は、4 つの時間範囲を 1 つに結合し、実際の削除範囲が 0 ～ 50 秒になるようにします。

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

次の例では、4 つの REPLACE 時間範囲が、時間範囲が競合して定義されています。 この場合、 TVSDK は 0 ～ 50 秒を 25 秒の広告で置き換えます。 後続の範囲に競合があるので、並べ替え順の最初の置き換え期間に合わせます。

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
