---
description: カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。
seo-description: カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。
seo-title: TimeRangeクラス
title: TimeRangeクラス
uuid: af3ce5e6-44b5-457f-a6e7-aa232defb91e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# TimeRangeクラス {#timerange-class}

カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

セッ `TimeRange` ト内の各指定は、TVSDKによって内部的に維持され、広告関連の期間として適切にマークされる必要のある、再生タイムライン上のセグメントを表します。

このク `TimeRange` ラスは、タイムライン上の開始位置と終了位置を公開する単純なデータ構造です。 これら2つの読み取り専用プロパティは、再生タイムラインの時間範囲の概念を抽象化します。

>[!TIP]
>
>どちらの値もミリ秒で表されます。

次に、クラスの概要を示し `TimeRange` ます。

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
