---
description: TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。
seo-description: TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。
seo-title: 再生タイムラインの確認
title: 再生タイムラインの確認
uuid: d0fe7926-9b9a-4203-a1c7-e57ba25b882e
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 再生タイムラインの確認 {#inspect-the-playback-timeline}

TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。

次のスクリーンショットに示す実装例を示します。  ![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. メソッドを使 `Timeline` 用して、内のオブジ `MediaPlayer` ェクトにアクセ `getTimeline()` スします。

   このク `Timeline` ラスは、インスタンスによって現在読み込まれているメディア項目に関連付けられているタイムラインのコンテンツに関連する情報をカプセル化 `MediaPlayer` します。 このク `Timeline` ラスは、基になるタイムラインの読み取り専用ビューへのアクセスを提供します。 このク `Timeline` ラスは、オブジェクトのリストを介してイテレータを提供するgetterメソッドを提供 `TimelineMarker` します。

1. のリストを繰り返し処理し、返さ `TimelineMarkers` れた情報を使用してタイムラインを実装します。

       &#39;TimelineMarker&#39;オブジェクトには、次の2つの情報が含まれます。
   
   * タイムライン上のマーカーの位置（ミリ秒）
   * タイムライン上のマーカーの時間（ミリ秒）

1. インスタンスでイ `MediaPlayerEvent.TIMELINE_UPDATED` ベントをリッスン `MediaPlayer` し、コールバックを実装 `TimelineUpdatedEventListener.onTimelineUpdated()` します。

   このオブ `Timeline` ジェクトは、リスナーを呼び出すことで、再生タイムラインで発生する可能性のある変更をアプリケーションに通知で `OnTimelineUpdated` きます。

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
