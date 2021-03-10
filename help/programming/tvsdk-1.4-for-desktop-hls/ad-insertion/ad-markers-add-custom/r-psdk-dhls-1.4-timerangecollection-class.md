---
description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
title: TimeRangeCollectionクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '70'
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
