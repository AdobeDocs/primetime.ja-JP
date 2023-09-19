---
description: この例では、 TimeRange 指定を再生タイムラインに含める推奨方法を示します。
title: タイムラインに TimeRange 広告マーカーを配置
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# タイムラインに TimeRange 広告マーカーを配置 {#place-timerange-ad-markers-on-the-timeline}

この例では、 TimeRange 指定を再生タイムラインに含める推奨方法を示します。

1. 帯域外広告配置情報を次のリストに変換 `TimeRange` 仕様 ( つまり、 `TimeRange` クラス ) です。
1. 次のセットを使用： `TimeRange` のインスタンスに入力する仕様 `TimeRangeCollection` クラス。
1. Metadata インスタンスを渡します。このインスタンスは、 `TimeRangeCollection` インスタンス、 `replaceCurrentItem` メソッド ( `MediaPlayer` インターフェイス )。
1. TVSDK が PREPARED 状態に移行するのを待つには、 `PlaybackEventListener#onPrepared` コールバックをトリガーします。
1. を呼び出してビデオの再生を開始する `play()` メソッド ( `MediaPlayer` インターフェイス )。

* タイムラインの競合の処理：一部の `TimeRange` 仕様は、再生タイムライン上で重なります。 例えば、 `TimeRange` 指定は、既に配置された終了位置の値より小さい可能性があります。 この場合、 TVSDK は、問題の発生位置を静かに調整します `TimeRange` タイムラインの競合を回避するための仕様です。 この調整を通じて、新しい `TimeRange` は、最初に指定したよりも短くなります。 調整が極端で、結果として `TimeRange` 時間が 0 ミリ秒の場合、 TVSDK は問題をサイレントにドロップします。 `TimeRange` 仕様。

* 条件 `TimeRange` カスタム広告の時間の仕様が提供されている場合、 TVSDK は、これらを広告の時間内にグループ化された広告に変換しようとします。 TVSDK が隣接する `TimeRange` 仕様を作成し、それらを別々の広告の時間に分割します。 他の時間範囲と隣接しない時間範囲がある場合、それらは単一の広告を含む広告の時間に変換されます。

* 読み込まれるメディアプレーヤーアイテムは VOD アセットを指していると想定されます。 TVSDK は、アプリケーションが、メタデータにが含まれるメディアリソースの読み込みを試みるたびに、これをチェックします `TimeRange` カスタム広告マーカー機能のコンテキストでのみ使用できる仕様。 基になるアセットのタイプが VOD でない場合、 TVSDK ライブラリは例外をスローします。

* カスタム広告マーカーを扱う場合、 TVSDK は、(Adobe Primetime Ad Decisioning( 旧称：Auditude) または他の広告プロビジョニングシステムを介して ) 他の広告解決メカニズムを非アクティブ化します。 TVSDK が提供する様々な広告リゾルバーモジュールのいずれか、またはカスタム広告マーカーメカニズムのいずれかを使用できます。 カスタム広告マーカー API を使用する場合、広告コンテンツは、既に解決済みであると見なされ、タイムラインに配置されます。

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

次のコードスニペットは、3 つの `TimeRange` 仕様は、カスタム広告マーカーとしてタイムラインに配置されます。

```
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
var timeRanges:TimeRangeCollection = new TimeRangeCollection(); 
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
  
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                             timeRanges.toMetadata(null));
```
