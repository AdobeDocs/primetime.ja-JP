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

各 `TimeRange` set の仕様は、 TVSDK が内部的に管理する再生タイムライン上のセグメントで、広告関連の期間として適切にマークする必要があるものを表します。

The `TimeRange` クラスは、タイムライン上の開始位置と終了位置を表示する単純なデータ構造体です。 これら 2 つの読み取り専用プロパティは、再生タイムラインの時間範囲のアイデアを要約します。

>[!TIP]
>
>両方の値はミリ秒単位で表されます。

TimeRange クラスの概要を次に示します。

```
public final class TimeRange {
    // the start/end values are provided at construction 
    public static function createRange(begin:Number, duration:Number {…}
 
    public function get begin():Number {…}
    public function get end():Number {…}
    public function get duration():Number {…}
}
```
