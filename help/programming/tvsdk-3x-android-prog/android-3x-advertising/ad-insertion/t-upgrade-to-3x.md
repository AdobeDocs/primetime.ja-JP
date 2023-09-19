---
description: com.adobe.mediacore.timeline.TimelineMarker インターフェイスに新しいメソッドが含まれるようになりました。
title: 2.5.x の遅延広告解決から 3.0.0 の遅延広告解決へのアップグレード（API/ワークフローの変更）
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 2.5.x の遅延広告解決から 3.x の遅延広告解決（API/Workflow の変更）へのアップグレード：{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

com.adobe.mediacore.timeline.TimelineMarker インターフェイスに、次の新しいメソッドが含まれるようになりました。

**Placement.Type getPlacementType()**

このメソッドは、Placement.Type.PRE_ROLL、Placement.Type.MID_ROLL または Placement.Type.Placement_ROLL の配置タイプを返します。POSTタイプは以下の通りです。 広告ブレークが未解決の場合、 `getDuration()`メソッドを呼び出すと、0 が返されます。

>[!NOTE]
>
>このインターフェイスは、まだ解決されていない場合、 com.mediacore.timeline.advertising.AdBreakTimelineItem タイプにキャストされないことがあります。 次の場合にキャストできます： `getDuration()` TimelineMarker のメソッドが 0 より大きい値です。

**イベントの変更：**

`kEventAdResolutionComplete` が廃止され、プレーヤーが PREPARED ステータスになった直後にトリガーされるようになりました。 以前にこのイベントをスクラブバーを描画するためにリッスンしたアプリケーションは、これを変更して `kEventTimelineUpdated` のみ。 個々の広告の時間が解決された後、 `kEventTimelineUpdated` イベントが発行されます。
