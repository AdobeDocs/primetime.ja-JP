---
description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作も異なります。
seo-description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作も異なります。
seo-title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
uuid: 49abab49-4e52-477d-b7ed-688ee63e7473
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# 広告シグナリングモードと広告メタデータの組み合わせ{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}からの広告挿入および削除への影響

様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作も異なります。

>[!TIP]
>
>時間範囲と広告シグナリングモードの間に矛盾がある場合、TVSDKは時間範囲を優先します。

シグナリングモードとメタデータの組み合わせの動作の詳細を次の表に示します。

**サーバーマップ**

| **広告メタデータ** | **作成されたリゾルバー** | **`PlacementInformations`created** | **結果の動作** |
|--- |--- |--- |--- |
|  | 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されます |
| Delete、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 範囲が削除される、広告が挿入される |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 広告が挿入される |
| Replace、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が置換される |
| マーク | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされる |
| Mark、Auditude | CustomAd、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |

**マニフェストキュー**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` created | 結果の動作 |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | 広告が挿入される |
| Delete、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | 範囲が削除される、広告が挿入される |
| Mark、Auditude | Mark、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されます |
| マーク | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされる |
| Replace、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が置換される |

**カスタム時間範囲**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` created | 結果の動作 |
|--- |--- |--- |--- |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されます |
| Delete、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除される、広告は挿入されない |
| Auditude | Auditude | なし | 広告は挿入されません |
| Replace、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が広告で置き換えられます |
| マーク | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされる |
| Mark、Auditude | Custom Ad、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされ、広告は挿入されません |

**未設定（デフォルト）**

| 広告メタデータ | 作成されたリゾルバー | `PlacementInformations` created | 結果の動作 |
|--- |--- |--- |--- |
| 削除 | 削除 | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | 範囲が削除されます |
| Delete、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 範囲が削除される、広告が挿入される |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | 広告が挿入される |
| Replace、Auditude | Delete、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | 範囲が広告で置き換えられます |
| マーク | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされる |
| Mark、Auditude | CustomAd、Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | 範囲がマークされる |