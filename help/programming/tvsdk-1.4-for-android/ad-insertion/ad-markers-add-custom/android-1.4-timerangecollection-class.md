---
description: TimeRangeCollection ユーティリティクラスは、TimeRange 指定の順序付きコレクションの概念を抽象化し、自身を Metadata インスタンスに変換するサービスを提供します。
title: TimeRangeCollection クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# TimeRangeCollection クラス{#timerangecollection-class}

TimeRangeCollection ユーティリティクラスは、TimeRange 指定の順序付きコレクションの概念を抽象化し、自身を Metadata インスタンスに変換するサービスを提供します。

<!--<a id="section_D87AA7BC628D458DAB12D5247AD34B41"></a>-->

```java
public final class TimeRangeCollection {
    // default constructor method
    public TimeRangeCollection(Type type) {...}

    // the list of timerange specifications provided at construction time 
    public TimeRangeCollection(Type type, List<TimeRange> timeRanges) {...}

    // timerange specs can also be added later
    public void addTimeRange(TimeRange timeRange) {...}

    // translate the set of timerange specs into a Metadata instance 
    public Metadata toMetadata(Metadata options) {...}
}
```

The `type` パラメータは、コンストラクタメソッドのシグネチャの最初の位置パラメータで、 `TimeRangeCollection#Type` 列挙。 これは、 `TimeRangeCollection` クラス。 この列挙で現在定義されている値は次のとおりです。 `MARK_RANGES`, `DELETE_RANGES`、および `REPLACE_RANGES`. 次の項目を作成できます。 `TimeRangeCollection` これら 3 つのタイプを使用するオブジェクト。
