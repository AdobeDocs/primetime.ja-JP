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


# タイムラインへのTimeRange広告マーカーの配置 {#place-timerange-ad-markers-on-the-timeline}

この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。

1. 帯域外の広告配置情報を、 `TimeRange` 仕様(つまり、クラスのインスタンス `TimeRange` )のリストに変換します。
1. 一連の `TimeRange` 仕様を使用して、クラスのインスタンスを設定し `TimeRangeCollection` ます。
1. インスタンスから取得できるMetadataインスタンスを `TimeRangeCollection` メソッド（インターフェイスの一部）に渡し `replaceCurrentItem``MediaPlayer` ます。
1. TVSDKがPREPARED状態にトランジションするまで待ちます。この `PlaybackEventListener#onPrepared` コールバックがトリガーされるのを待ちます。
1. 開始（インターフェイスの一部）を呼び出して、 `play()` メソッドビデオを再生 `MediaPlayer` します。

* タイムラインの競合を処理する：一部の `TimeRange` 仕様が再生タイムラインで重なる場合があります。 例えば、 `TimeRange` 仕様に対応する開始位置の値が、既に配置されている終了位置の値より小さい場合があります。 この場合、TVSDKは、タイムラインの競合を回避するために、問題のある `TimeRange` 仕様の開始位置を微調整します。 この調整により、新しい要素は、元々指定されていた値より短くな `TimeRange` ります。 調整が過剰に行われ、長さ0ミリ秒に達すると、TVSDKは問題のある `TimeRange``TimeRange` 仕様を黙ってドロップします。

* カスタム広告の時間の `TimeRange` 指定が指定されている場合、TVSDKは、これらの指定を、広告の時間内にグループ化された広告に変換しようとします。 TVSDKは、隣接する `TimeRange` 仕様を探し、それらを別々の広告の時間にクラスター化します。 他の時間範囲に隣接しない時間範囲がある場合は、単一の広告を含む広告の時間に変換されます。

* 読み込まれるメディアプレイヤー項目は、VODアセットを指していると見なされます。 TVSDKは、この項目をチェックします。このメタデータには、カスタム広告マーカー機能のコンテキストでのみ使用できる `TimeRange` 仕様が含まれています。 基になるアセットのタイプがVODでない場合、TVSDKライブラリは例外をスローします。

* カスタム広告マーカーを処理する場合、TVSDKは、(Adobe Primetime広告決定（旧称Auditude）または他の広告プロビジョニングシステムを介した)他の広告解決メカニズムを非アクティブにします。 TVSDKが提供する様々な広告リゾルバーモジュールのいずれか、またはカスタム広告マーカーメカニズムのいずれかを使用できます。 カスタム広告マーカーAPIを使用する場合、広告コンテンツは既に解決済みで、タイムライン上に配置されていると見なされます。

<!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->

次のコードスニペットに、カスタム広告マーカーとして3つの `TimeRange` 指定をタイムラインに配置する簡単な例を示します。

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
