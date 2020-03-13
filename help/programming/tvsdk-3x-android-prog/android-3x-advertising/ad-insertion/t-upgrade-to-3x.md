---
description: 'com.adobe.mediacore.timeline.TimelineMarkerインターフェイスに新しいメソッドが追加されました '
seo-description: 'com.adobe.mediacore.timeline.TimelineMarkerインターフェイスに新しいメソッドが追加されました '
seo-title: '2.5.xの遅延広告解決から3.0.0の遅延広告解決へのアップグレード（API/ワークフローの変更） '
title: '2.5.xの遅延広告解決から3.0.0の遅延広告解決へのアップグレード（API/ワークフローの変更） '
uuid: 5870ceb4-93a8-4c8b-b716-673396122644
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 2.5.xの遅延広告解決から3.xの遅延広告解決へのアップグレード（API/ワークフローの変更）:{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

com.adobe.mediacore.timeline.TimelineMarkerインターフェイスに、次の新しいメソッドが追加されました。

**Placement.Type getPlacementType()**

このメソッドは、配置タイプがPlacement.Type.PRE_ROLL、Placement.Type.MID_ROLLまたはPlacement.Type.POST_ROLLであることを返します。 広告の時間が未解決の場合、TimelineMarkerインタ `getDuration()`ーフェイスのメソッドは0を返します。

>[!NOTE]
>
>このインターフェイスがまだ解決されていない場合、このインターフェイスは、常にcom.mediacore.timeline.advertising.AdBreakTimelineItem型にキャストされるとは限りません。 TimelineMarkerのメソッドが0より大きい場合は、 `getDuration()` キャストできます。

**イベントの変更：**

`kEventAdResolutionComplete` が減価され、プレイヤーがPREPAREDステータスに入った直後にトリガーされるようになりました。 以前はこのイベントのみをリッスンしてスクラブバーを描画していたアプリは、このイベントをリッスン専用に変更する必要があ `kEventTimelineUpdated` ります。 個々の広告の時間が解決された後、新しいイベ `kEventTimelineUpdated` ントがディスパッチされます。
