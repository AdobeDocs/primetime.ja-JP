---
description: この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。
seo-description: この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。
seo-title: タイムラインへのTimeRange広告マーカーの配置
title: タイムラインへのTimeRange広告マーカーの配置
uuid: cbcc4c84-0d56-4331-b555-b8e59f7d52d4
translation-type: tm+mt
source-git-commit: fd21a29bb186238142d43e0277bbf92f8406f6f7
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# TimeRange広告マーカーをタイムラインに配置{#place-timerange-ad-markers-on-the-timeline}

この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。

1. 帯域外の広告位置情報を`TimeRange`仕様（つまり、`TimeRange`クラスのインスタンス）のリストに変換します。
1. `TimeRange`仕様のセットを使用して、`TimeRangeCollection`クラスのインスタンスを設定します。
1. `TimeRangeCollection`インスタンスから取得できるMetadataインスタンスを`replaceCurrentItem`メソッド（`MediaPlayer`インターフェイスの一部）に渡します。
1. `PlaybackEventListener#onPrepared`コールバックがトリガーされるのを待って、TVSDKがPREPARED状態にトランジションするのを待ちます。
1. `play()`メソッド（`MediaPlayer`インターフェイスの一部）を呼び出して、開始ビデオを再生します。

* タイムラインの競合を処理する：一部の`TimeRange`仕様が再生タイムラインで重なる場合があります。 例えば、`TimeRange`仕様に対応する開始位置の値が、既に配置されている終了位置の値より小さい場合があります。 この場合、TVSDKは、タイムラインの競合を回避するために、不適切な`TimeRange`仕様の開始位置をサイレントに調整します。 この調整により、新しい`TimeRange`は、元々指定された値より短くなります。 調整が過剰に行われ、長さ0ミリ秒の`TimeRange`が発生すると、TVSDKは問題の`TimeRange`仕様を黙ってドロップします。

* カスタム広告の時間の`TimeRange`指定が提供されると、TVSDKは、これらの指定を広告の時間内にグループ化された広告に変換しようとします。 TVSDKは、隣接する`TimeRange`仕様を探し、それらを別々の広告の時間にクラスター化します。 他の時間範囲に隣接しない時間範囲がある場合は、単一の広告を含む広告の時間に変換されます。

* 読み込まれるメディアプレイヤー項目は、VODアセットを指していると見なされます。 TVSDKは、カスタム広告マーカー機能のコンテキストでのみ使用できる`TimeRange`仕様をメタデータに含むメディアリソースを読み込もうとするたびに、この項目をチェックします。 基になるアセットのタイプがVODでない場合、TVSDKライブラリは例外をスローします。

* カスタム広告マーカーを処理する場合、TVSDKは、(Adobe Primetime広告決定（旧称Auditude）または他の広告プロビジョニングシステムを介した)他の広告解決メカニズムを非アクティブにします。 TVSDKが提供する様々な広告リゾルバーモジュールのいずれか、またはカスタム広告マーカーメカニズムのいずれかを使用できます。 カスタム広告マーカーAPIを使用する場合、広告コンテンツは既に解決済みで、タイムライン上に配置されていると見なされます。

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

次のコードスニペットは、3つの`TimeRange`仕様のセットがカスタム広告マーカーとしてタイムラインに配置される簡単な例を示しています。

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
