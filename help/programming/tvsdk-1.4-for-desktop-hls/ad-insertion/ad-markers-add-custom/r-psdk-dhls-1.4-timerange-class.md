---
description: カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。
seo-description: カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。
seo-title: TimeRangeクラス
title: TimeRangeクラス
uuid: 5d0c979e-cc63-4fdd-becc-b0e3987b0891
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# TimeRangeクラス{#timerange-class}

カスタム広告マーカーを使用すると、タイムラインセグメントを表す一連のTimeRange指定をTVSDKに渡すことができます。

<!--<a id="section_42EB6D62627A424ABA250E3246EFEFC3"></a>-->

セット内の各`TimeRange`仕様は、TVSDKが内部的に保持し、広告関連の期間として適切にマークする必要がある再生タイムライン上のセグメントを表します。

`TimeRange`クラスは、開始の位置とタイムライン上の終了位置を公開する単純なデータ構造です。 これら2つの読み取り専用プロパティは、再生タイムラインの時間範囲の概念を抽象化します。

>[!TIP]
>
>どちらの値もミリ秒で表されます。

TimeRangeクラスの概要を次に示します。

```
public final class TimeRange {
    // the start/end values are provided at construction 
    public static function createRange(begin:Number, duration:Number {…}
 
    public function get begin():Number {…}
    public function get end():Number {…}
    public function get duration():Number {…}
}
```

