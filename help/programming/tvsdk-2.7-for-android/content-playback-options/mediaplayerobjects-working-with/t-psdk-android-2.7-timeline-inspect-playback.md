---
description: TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションを識別するカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役立ちます。
title: 再生タイムラインのInspect
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 再生タイムラインのInspect{#inspect-the-playback-timeline}

TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションを識別するカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役立ちます。

以下のスクリーンショットに示す実装例を示します。  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. `getTimeline()`メソッドを使用して、`MediaPlayer`の`Timeline`オブジェクトにアクセスします。

   `Timeline`クラスは、`MediaPlayer`インスタンスによって現在読み込まれているメディア項目に関連付けられているタイムラインのコンテンツに関連する情報をカプセル化します。 `Timeline`クラスは、基になるタイムラインの読み取り専用表示へのアクセスを提供します。 `Timeline`クラスは、`TimelineMarker`オブジェクトのリストを介してイテレーターを提供するgetterメソッドを提供します。

1. `TimelineMarkers`のリストを繰り返し処理し、返された情報を使用してタイムラインを実装します。

       &#39;TimelineMarker&#39;オブジェクトには、次の2つの情報が含まれます。
   
   * タイムライン上のマーカーの位置（ミリ秒）
   * タイムライン上のマーカーの時間（ミリ秒）

1. `MediaPlayerEvent.TIMELINE_UPDATED`イベントを`MediaPlayer`インスタンスでリッスンし、`TimelineUpdatedEventListener.onTimelineUpdated()`コールバックを実装します。

   `Timeline`オブジェクトは、`OnTimelineUpdated`リスナーを呼び出すことで、再生タイムラインで発生する可能性がある変更をアプリケーションに知らせることができます。

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
