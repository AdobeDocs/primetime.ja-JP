---
description: ReplaceTimeRange ユーティリティクラスは、CustomRangeMetadata で使用する TimeRange クラスの拡張です。
title: ReplaceTimeRange クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 0%

---

# ReplaceTimeRange クラス {#replacetimerange-class}

ReplaceTimeRange ユーティリティクラスは、CustomRangeMetadata で使用する TimeRange クラスの拡張です。

```java
public class ReplaceTimeRange extends TimeRange {
    // Default constructor method
    public ReplaceTimeRange() { 
        ... 
    }

    // Details of begining, duration and replaceDuration 
    // provided at construction time 
    public ReplaceTimeRange(long begin, long duration, long replaceDuration) { 
        ... 
    }

    // Replace duration
    public long getReplaceDuration() { 
        ... 
    }
}
```
