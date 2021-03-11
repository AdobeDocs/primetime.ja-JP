---
description: 'com.adobe.mediacore.timeline.TimelineMarkerインターフェイスに、新しいメソッドが含まれるようになりました '
title: '2.5.xの遅延広告解決から3.0.0の遅延広告解決へのアップグレード（API/ワークフローの変更） '
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# 2.5.xの遅延広告解決から3.xの遅延広告解決へのアップグレード（API/ワークフローの変更）:{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

com.adobe.mediacore.timeline.TimelineMarkerインターフェイスに、新しいメソッドが追加されました。

**Placement.Type getPlacementType()**

このメソッドは、配置タイプPlacement.Type.PRE_ROLL、Placement.Type.MID_ROLLまたはPlacement.Type.POST_ROLLを返します。 広告の時間が未解決の場合、TimelineMarkerインターフェイスの`getDuration()`メソッドは0を返します。

>[!NOTE]
>
>このインターフェイスがまだ解決されていない場合、このインターフェイスは、常にcom.mediacore.timeline.advertising.AdBreakTimelineItem型にキャストされるわけではありません。 TimelineMarkerの`getDuration()`メソッドが0より大きい場合は、キャストできます。

**イベントの変更：**

`kEventAdResolutionComplete` が減価され、プレイヤーがPREPAREDステータスになった直後にトリガーされるようになりました。以前はこのイベントを聞いてスクラブバーを描くだけだったアプリケーションは、`kEventTimelineUpdated`のみをリッスンするように変更する必要があります。 個々の広告の時間が解決されると、新しい`kEventTimelineUpdated`イベントがディスパッチされます。
