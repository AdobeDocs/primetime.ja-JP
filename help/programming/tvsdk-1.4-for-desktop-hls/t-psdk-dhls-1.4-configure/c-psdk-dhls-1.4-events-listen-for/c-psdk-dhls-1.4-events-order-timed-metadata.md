---
description: TVSDKは、時間指定メタデータイベントをディスパッチし、デフォルトタグやカスタムタグが検出された場合、またはプレイリストがマニフェスト内で変更された場合に、時間指定メタデータを生成します。 イベントは、マニフェストに表示される順序でディスパッチされます。
title: 時間指定メタデータイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# 時間指定メタデータイベント{#timed-metadata-events}

TVSDKは、時間指定メタデータイベントをディスパッチし、デフォルトタグやカスタムタグが検出された場合、またはプレイリストがマニフェスト内で変更された場合に、時間指定メタデータを生成します。 イベントは、マニフェストに表示される順序でディスパッチされます。

プレイヤーは、次のイベントに基づいてアクションを実装します。

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`:ID3時間指定メタデータが処理された場合にディスパッチされます。
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`:時間指定メタデータが処理され、オポチュニティが検出されなかった場合にディスパッチされます。

