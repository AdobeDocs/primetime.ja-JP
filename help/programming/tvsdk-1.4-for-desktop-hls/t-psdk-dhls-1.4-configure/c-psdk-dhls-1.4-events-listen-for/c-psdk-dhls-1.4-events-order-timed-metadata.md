---
description: TVSDK は、デフォルトのタグやカスタムタグが見つかった場合、またはプレイリストがマニフェスト内で変更された場合に、時間指定メタデータイベントをディスパッチし、時間指定メタデータを生成します。 イベントは、マニフェストに表示される順序でディスパッチされます。
title: 時間指定メタデータイベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# 時間指定メタデータイベント{#timed-metadata-events}

TVSDK は、デフォルトのタグやカスタムタグが見つかった場合、またはプレイリストがマニフェスト内で変更された場合に、時間指定メタデータイベントをディスパッチし、時間指定メタデータを生成します。 イベントは、マニフェストに表示される順序でディスパッチされます。

プレーヤーは、次のイベントに基づいてアクションを実装します。

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`:ID3 の時間指定メタデータが処理された際にディスパッチされます。
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`：時間指定メタデータが処理され、オポチュニティが検出されなかった場合にディスパッチされます。
