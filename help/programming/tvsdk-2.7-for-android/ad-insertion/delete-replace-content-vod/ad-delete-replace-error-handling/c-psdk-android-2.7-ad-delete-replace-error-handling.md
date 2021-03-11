---
description: TVSDKは、不適切に定義された時間範囲を結合または順序変更することで、特定の問題に従って時間範囲エラーを処理します。
title: 広告の削除と置換のエラー処理
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# 概要{#ad-deletion-and-replacement-error-handling-overview}

TVSDKは、不適切に定義された時間範囲を結合または順序変更することで、特定の問題に従って時間範囲エラーを処理します。

TVSDKは、デフォルトの結合と順序変更によって`timeRanges`エラーを管理します。 まず、プレイヤは、顧客定義の時間範囲を&#x200B;*begin*&#x200B;時間で並べ替えます。 この並べ替え順に基づいて、範囲間にサブセットや交差がある場合、TVSDKは隣接する範囲を結合し、それらの範囲を結合します。

TVSDKは、次のオプションを使用して、時間範囲エラーを処理します。

* **順序が正しくないTVSDKは、** 時間範囲を並べ替えます。

* **時間範囲のサブセットを** 結合します。

* **IntersectTVSDKは、交差する時間範囲を結合し** ます。

* **置換範囲の** conflictTVSDKは、競合するグループに表示される最も古い期間 `timeRange` から置換期間を選択します。

TVSDKは、広告メタデータとのシグナリングモード競合を次の方法で処理します。

* 広告シグナリングモードが時間範囲メタデータと競合する場合、時間範囲メタデータは常に優先されます。

   例えば、広告シグナリングモードがサーバーマップまたはマニフェストキューとして設定され、広告メタデータにもMARK時間範囲がある場合、結果として生じる動作は範囲がマークされ、広告は挿入されないことです。
* REPLACE範囲の場合、シグナリングモードがサーバーマップまたはマニフェストキューとして設定されている場合、範囲はREPLACE範囲で指定されたとおりに置換され、サーバーマップまたはマニフェストキューを介した広告挿入はありません。

   詳しくは、[広告シグナリングモードからの広告挿入および削除への影響の&#x200B;*シグナリングモード/メタデータ組み合わせの動作*&#x200B;の表を参照してください。](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android)。

次の点に注意してください。

* サーバーが有効な`AdBreaks`を返さない場合、TVSDKは空のAdBreakの`NOPTimelineOperation`を生成して処理し、広告は再生されません。

* C3広告の削除/置換はVODに対してのみサポートされることを意図していますが、広告メタデータで指定した場合、時間範囲もライブストリーム用に処理されます。

