---
description: すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、ビューアはメインコンテンツにすばやくアクセスできます。 この機能はライブDVRにのみ適用され、VODアセットなどでは機能しません。
seo-description: すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、ビューアはメインコンテンツにすばやくアクセスできます。 この機能はライブDVRにのみ適用され、VODアセットなどでは機能しません。
seo-title: 遅延広告読み込みの有効化
title: 遅延広告読み込みの有効化
uuid: ac7c8801-7fa2-4f17-b79c-c603b3236948
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 遅延広告読み込みの有効化{#enable-lazy-ad-loading}

すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、ビューアはメインコンテンツにすばやくアクセスできます。 この機能はライブDVRにのみ適用され、VODアセットなどでは機能しません。

1. のBooleanプロパティを使 `delayAdLoading` 用しま `AdvertisingMetadata`す。

   * falseの場合、TVSDKは、すべての広告が解決され、配置されてから、PREPAREDステータスに移行するまで待ちます。 デフォルトではfalseです。
   * trueの場合、TVSDKは初期広告のみを解決し、PREPAREDステータスに移行します。 残りの広告は、再生中に解決され、配置されます。

1. Adobe Primetime ad decisioningでも遅延広告読み込みをアクティブにするには、作成時にこれをに `true` 設定してくださ `AuditudeSettings`い。

   クラス `AuditudeSettings` は、このプロパティをか `AdvertisingMetadata`ら継承しますが、現在の値は継承しません。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. 広告をスクラブバーのキューとして正確に反映するには、をリッスンしま `TimelineEvent`す。 `TIMELINE_UPDATED` イベントを追加し、このイベントを受け取るたびにスクラブバーを再描画します。

   VoDストリームが遅延広告読み込みを使用する場合、プレイヤーがPREPAREDステータスになったときに、すべての広告がタイムラインに配置されるわけではないので、スクラブバーを明示的に再描画する必要があります。

   TVSDKは、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要のある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムライン上に配置される広告の時間の数とは関係ありません。 例えば、5つの広告の時間がある場合、正確に5つのイベントを受け取らない可能性があります。

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```

