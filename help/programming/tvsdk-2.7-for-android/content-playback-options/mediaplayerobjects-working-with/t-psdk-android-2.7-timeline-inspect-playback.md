---
description: TVSDK が再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役に立ちます。
title: Inspect再生タイムライン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Inspect再生タイムライン {#inspect-the-playback-timeline}

TVSDK が再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役に立ちます。

次のスクリーンショットに示す実装例を次に示します。  ![](assets/inspect-playback.jpg){width="368.641pt"}

1. 次にアクセス： `Timeline` オブジェクトを `MediaPlayer` の使用 `getTimeline()` メソッド。

   The `Timeline` クラスは、現在、 `MediaPlayer` インスタンス。 The `Timeline` クラスは、基になるタイムラインの読み取り専用ビューにアクセスできます。 The `Timeline` クラスは、 `TimelineMarker` オブジェクト。

1. 次のリストを繰り返し処理： `TimelineMarkers` 返された情報を使用してタイムラインを実装します。

       「TimelineMarker」オブジェクトには、次の 2 つの情報が含まれます。
   
   * タイムライン上のマーカーの位置（ミリ秒）
   * タイムライン上のマーカーの時間（ミリ秒）

1. をリッスンします。 `MediaPlayerEvent.TIMELINE_UPDATED` イベント `MediaPlayer` インスタンスを作成し、実装します。 `TimelineUpdatedEventListener.onTimelineUpdated()` コールバック。

   The `Timeline` オブジェクトは、 `OnTimelineUpdated` リスナー。

```java
// access the timeline object 
Timeline timeline = mediaPlayer.getTimeline(); 
 
// Iterate through the list of TimelineMarkers 
Iterator<TimelineMarker> iterator = timeline.timelineMarkers(); 
 
while (iterator.hasNext()) { 
    TimelineMarker marker = iterator.next(); 
    // the start position of the marker 
    long startPos = marker.getTime(); 
    // the duration of the marker 
    long duration = marker.getDuration(); 
}
```
