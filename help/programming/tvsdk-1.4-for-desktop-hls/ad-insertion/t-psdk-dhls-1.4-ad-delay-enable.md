---
description: すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、メインコンテンツへのビューアのアクセスが速くなります。 この機能はライブDVRにのみ適用され、VODアセットなどでは動作しません。
seo-description: すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、メインコンテンツへのビューアのアクセスが速くなります。 この機能はライブDVRにのみ適用され、VODアセットなどでは動作しません。
seo-title: 遅延広告読み込みの有効化
title: 遅延広告読み込みの有効化
uuid: ac7c8801-7fa2-4f17-b79c-c603b3236948
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# 遅延広告読み込みを有効にする{#enable-lazy-ad-loading}

すべての広告が読み込まれてタイムラインに配置される前に再生を許可するかどうかを指定できます。 この方法で再生を開始すると、メインコンテンツへのビューアのアクセスが速くなります。 この機能はライブDVRにのみ適用され、VODアセットなどでは動作しません。

1. `AdvertisingMetadata`内のブール型プロパティ`delayAdLoading`を使用します。

   * falseの場合、TVSDKは、すべての広告が解決され、配置されてから、PREPAREDステータスに移行します。 デフォルトではfalseです。
   * trueの場合、TVSDKは、最初の広告とトランジションのみをPREPAREDステータスに解決します。 残りの広告は再生中に解決され、配置されます。

1. Adobe Primetimead decisioningでも遅延広告読み込みをアクティブにするには、`AuditudeSettings`を作成する際にこれを`true`に設定します。

   `AuditudeSettings`クラスは、`AdvertisingMetadata`からこのプロパティを継承しますが、現在の値を継承しません。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. 広告をスクラブバーのキューとして正確に反映させるには、`TimelineEvent`をリッスンします。 `TIMELINE_UPDATED` このイベントを受け取るたびに、イベントを設定し、スクラブバーを再描画します。

   VoDストリームで遅延広告読み込みを使用する場合、プレイヤーがPREPAREDステータスになったときにすべての広告がタイムラインに配置されるわけではないので、スクラブバーを明示的に再描画する必要があります。

   TVSDKは、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要がある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムライン上に配置される広告の時間の数とは関係ありません。 例えば、広告の時間が5つある場合、厳密には5つのイベントを受け取らないことがあります。

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```

