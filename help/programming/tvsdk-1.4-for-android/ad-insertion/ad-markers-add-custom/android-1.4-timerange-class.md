---
description: カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連の TimeRange 指定を TVSDK に渡すことができます。
title: TimeRange クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# TimeRange クラス{#timerange-class}

カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連の TimeRange 指定を TVSDK に渡すことができます。

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

セット内の TimeRange の各指定は、TVSDK が内部的に管理し、広告関連の期間として適切にマークする必要がある再生タイムライン上のセグメントを表します。

The `TimeRange` クラスは、タイムライン上の開始位置と終了位置を表示する単純なデータ構造体です。 これら 2 つの読み取り専用プロパティは、再生タイムラインの時間範囲のアイデアを要約します。

>[!TIP]
>
>両方の値はミリ秒単位で表されます。

以下に、 `TimeRange` クラス：

```java
public final class TimeRange {
    // the start/end values are provided at construction time
    public static TimeRange createRange(long begin, long duration) {...} 

    // only getters are available
    public long getBegin() {...} 
    public long getEnd() {...} 
    public long getDuration() {...}
}
```
