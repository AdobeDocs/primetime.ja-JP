---
description: TimeRangeCollection ユーティリティクラスは、TimeRange 指定の順序付きコレクションの概念を抽象化し、自身を Metadata インスタンスに変換するサービスを提供します。
title: TimeRangeCollection クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---

# TimeRangeCollection クラス{#timerangecollection-class}

TimeRangeCollection ユーティリティクラスは、TimeRange 指定の順序付きコレクションの概念を抽象化し、自身を Metadata インスタンスに変換するサービスを提供します。

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```
public final class TimeRangeCollection { 
    public static const MARK_RANGES:String = "mark_ranges"; 
  
    public function TimeRangeCollection(timeRanges:Vector.<TimeRange>) {…} 
    public function addTimeRange(timeRange:TimeRange):void {…} 
    public function toMetadata(options:Metadata):Metadata {…} 
}
```

コレクションのタイプに定義された値は次のとおりです `MARK_RANGES`, `DELETE_RANGES`、および `REPLACE_RANGES`. 次の項目を作成できます。 `TimeRangeCollection`では、これら 3 つのタイプを使用します。
