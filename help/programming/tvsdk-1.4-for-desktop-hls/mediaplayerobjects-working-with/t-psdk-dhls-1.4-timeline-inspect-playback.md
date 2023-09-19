---
description: TVSDK が再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役に立ちます。
title: Inspect再生タイムライン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Inspect再生タイムライン{#inspect-the-playback-timeline}

TVSDK が再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションが表示する場合に最も役に立ちます。

次のスクリーンショットに示す実装例を次に示します。
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width="368.641pt"}

1. 次にアクセス： `Timeline` オブジェクトを `MediaPlayer` の使用 `get` メソッド。

   The `Timeline` クラスは、現在、 `MediaPlayer` インスタンス。 The `Timeline` クラスは、基になるタイムラインの読み取り専用ビューにアクセスできます。 The `Timeline` クラスは、配置されたすべてのを取得するためのゲッターメソッドを提供します `TimelineMarker` オブジェクト。

1. 次のリストを繰り返し処理： `TimelineMarkers` 返された情報を使用してタイムラインを実装します。

       「TimelineMarker」オブジェクトには、次の 2 つの情報が含まれます。
   
   * タイムライン上のマーカーの位置（ミリ秒）
   * タイムライン上のマーカーの時間（ミリ秒）

<!--<a id="example_BA936629E82B4082A2E2C548E3FC3357"></a>-->

```
// access the timeline object 
var timeline:Timeline = mediaPlayer.timeline; 
 
// iterate through the list of TimelineMarkers 
var markers:Vector.<TimelineMarker> = timeline.timelineMarkers; 
markers.forEach(function(item:TimelineMarker,  
                         index:int,  
                         vector:Vector.<TimelineMarker>):void { 
    
    // the start position of the marker 
    var startPos:Number = item.time; 
 
    // the duration of the marker 
    var duration:Number = item.duration; 
 
    // draw the marker on the scrub-bar 
}
```
