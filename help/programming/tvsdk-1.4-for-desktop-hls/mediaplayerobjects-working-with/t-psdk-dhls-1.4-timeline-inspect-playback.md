---
description: TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。
seo-description: TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。
seo-title: 再生タイムラインの確認
title: 再生タイムラインの確認
uuid: 2f903493-2d88-4af2-ac71-36300b49735b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 再生タイムラインの確認{#inspect-the-playback-timeline}

TVSDKが再生中の、現在選択されているアイテムに関連付けられたタイムラインの説明を取得できます。 これは、広告コンテンツに対応するコンテンツセクションが識別されるカスタムスクラブバーコントロールをアプリケーションで表示する場合に最も役立ちます。

次のスクリーンショットに示す実装例を示します。
<!--<a id="fig_6D9FB3764F3947A38B8E7726187BD461"></a>-->

![](assets/inspect-playback.jpg){width=&quot;368.641pt&quot;}

1. メソッドを使 `Timeline` 用して、内のオブジ `MediaPlayer` ェクトにアクセ `get` スします。

   このク `Timeline` ラスは、インスタンスによって現在読み込まれているメディア項目に関連付けられているタイムラインのコンテンツに関連する情報をカプセル化 `MediaPlayer` します。 このク `Timeline` ラスは、基になるタイムラインの読み取り専用ビューへのアクセスを提供します。 このクラ `Timeline` スは、すべての配置されたオブジェクトを取得するgetterメソッドを提 `TimelineMarker` 供します。

1. のリストを繰り返し処理し、返さ `TimelineMarkers` れた情報を使用してタイムラインを実装します。

       &#39;TimelineMarker&#39;オブジェクトには、次の2つの情報が含まれます。
   
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

