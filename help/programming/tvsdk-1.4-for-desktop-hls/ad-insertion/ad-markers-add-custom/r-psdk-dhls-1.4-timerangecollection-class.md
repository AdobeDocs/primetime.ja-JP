---
description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付けられたコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付けられたコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-title: TimeRangeCollectionクラス
title: TimeRangeCollectionクラス
uuid: da781df4-6b19-47e1-8dc5-ea83c139f061
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# TimeRangeCollectionクラス{#timerangecollection-class}

TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付けられたコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

コレクションのタイプに対して定義され `MARK_RANGES`た値は、、 `DELETE_RANGES`およびで `REPLACE_RANGES`す。 この3つのタイプを `TimeRangeCollection`使用して、を作成できます。
