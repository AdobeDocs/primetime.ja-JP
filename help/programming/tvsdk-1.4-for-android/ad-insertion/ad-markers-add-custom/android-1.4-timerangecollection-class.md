---
description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-description: TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。
seo-title: TimeRangeCollectionクラス
title: TimeRangeCollectionクラス
uuid: 5705dc9d-4325-44b0-b5aa-196d09c3a67e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---


# TimeRangeCollectionクラス{#timerangecollection-class}

TimeRangeCollectionユーティリティクラスは、TimeRange指定の順序付きコレクションの概念を抽象化し、自身をMetadataインスタンスに変換するサービスを提供します。

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

`type`パラメーターは、コンストラクターメソッドの署名の中で最初の位置パラメーターで、`TimeRangeCollection#Type`定義済みリストーのインスタンスです。 これは`TimeRangeCollection`クラスの一部です。 この定義済みリストで現在定義されている値は`MARK_RANGES`、`DELETE_RANGES`、`REPLACE_RANGES`です。 これらの3つのタイプを使用して`TimeRangeCollection`オブジェクトを作成できます。
