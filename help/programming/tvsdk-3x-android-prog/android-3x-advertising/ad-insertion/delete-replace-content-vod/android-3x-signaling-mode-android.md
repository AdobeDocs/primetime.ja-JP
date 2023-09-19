---
description: 異なる広告シグナリングモードと広告メタデータの組み合わせを使用して、VOD ストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響 {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

異なる広告シグナリングモードと広告メタデータの組み合わせを使用して、VOD ストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。

>[!TIP]
>
>時間範囲と広告シグナリングモードの間に競合が発生した場合、 TVSDK は時間範囲を優先します。

次の表に、シグナリングモードとメタデータの組み合わせの動作の詳細を示します。

**サーバーマップ**

| **広告メタデータ** | **作成されたリゾルバー** | **`PlacementInformations`作成済み** | **結果の動作** |
|--- |--- |--- |--- |
|  | 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されました |
| 削除、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 範囲が削除され、広告が挿入されました |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 広告が挿入されました |
| 置換、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が置き換えられました |
| トンボ | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされました |
| マーク、Auditude | CustomAd、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |

**マニフェストキュー**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` 作成済み | 結果の動作 |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | 広告が挿入されました |
| 削除、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | 範囲が削除され、広告が挿入されました |
| マーク、Auditude | マーク、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されました |
| トンボ | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされました |
| 置換、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が置き換えられました |

**カスタム時間範囲**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` 作成済み | 結果の動作 |
|--- |--- |--- |--- |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されました |
| 削除、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除され、広告が挿入されません |
| Auditude | Auditude | なし | 広告が挿入されていません |
| 置換、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が広告で置き換えられました |
| トンボ | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされました |
| マーク、Auditude | カスタム広告、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |

**未設定（デフォルト）**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` 作成済み | 結果の動作 |
|--- |--- |--- |--- |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されました |
| 削除、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 範囲が削除され、広告が挿入されました |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 広告が挿入されました |
| 置換、Auditude | 削除、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が広告で置き換えられました |
| トンボ | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされました |
| マーク、Auditude | CustomAd、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされました |
