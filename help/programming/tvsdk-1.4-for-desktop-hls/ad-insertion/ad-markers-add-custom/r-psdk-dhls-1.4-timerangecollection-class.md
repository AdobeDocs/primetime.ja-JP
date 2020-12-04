---
description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-title: TimeRangeCollectionクラス
title: TimeRangeCollectionクラス
uuid: da781df4-6b19-47e1-8dc5-ea83c139f061
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# TimeRangeCollectionクラス{#timerangecollection-class}

TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

コレクションのタイプに対して定義されている値は、`MARK_RANGES`、`DELETE_RANGES`、`REPLACE_RANGES`です。 これらの3つのタイプを使って`TimeRangeCollection`を作成できます。
