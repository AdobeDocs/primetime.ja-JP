---
description: すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、閲覧者はメインコンテンツにすばやくアクセスできます。 この機能は、ライブ DVR にのみ適用でき、VOD アセットなどでは機能しません。
title: 遅延広告読み込みを有効にする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 遅延広告読み込みを有効にする{#enable-lazy-ad-loading}

すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、閲覧者はメインコンテンツにすばやくアクセスできます。 この機能は、ライブ DVR にのみ適用でき、VOD アセットなどでは機能しません。

1. Boolean プロパティを使用します。 `delayAdLoading` in `AdvertisingMetadata`.

   * false の場合、 TVSDK は、すべての広告が解決され、配置されてから、PREPARED ステータスに移行します。 デフォルトでは false です。
   * true の場合、 TVSDK は最初の広告のみを解決し、PREPARED ステータスに移行します。 残りの広告は、再生中に解決され、配置されます。

1. Adobe Primetime Ad Decisioning で遅延広告読み込みもアクティブ化するには、これを `true` 作成時に `AuditudeSettings`.

   The `AuditudeSettings` クラスは、このプロパティを継承します。 `AdvertisingMetadata`を使用しますが、現在の値は継承されません。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. 広告をスクラブバーのキューとして正確に反映させるには、 `TimelineEvent`. `TIMELINE_UPDATED` イベントを受け取るたびに、スクラブバーを再描画してください。

   VoD ストリームで遅延広告読み込みが使用されると、プレーヤーが PREPARED ステータスになったときにすべての広告がタイムラインに配置されないので、スクラブバーを明示的に再描画する必要があります。

   TVSDK は、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要がある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムラインに配置する広告の時間の数とは関係ありません。 例えば、5 つの広告の時間がある場合、5 つのイベントを正確に受け取ることはありません。

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```
