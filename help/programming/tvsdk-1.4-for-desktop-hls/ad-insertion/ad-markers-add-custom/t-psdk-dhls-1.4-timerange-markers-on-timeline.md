---
description: この例は、再生タイムラインにTimeRange指定を含める推奨方法を示しています。
seo-description: この例は、再生タイムラインにTimeRange指定を含める推奨方法を示しています。
seo-title: TimeRange広告マーカーをタイムラインに配置する
title: TimeRange広告マーカーをタイムラインに配置する
uuid: cbcc4c84-0d56-4331-b555-b8e59f7d52d4
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# TimeRange広告マーカーをタイムラインに配置する {#place-timerange-ad-markers-on-the-timeline}

この例は、再生タイムラインにTimeRange指定を含める推奨方法を示しています。

1. 帯域外の広告配置情報を、仕様のリスト(つまり、ク `TimeRange` ラスのインスタンス)に変換 `TimeRange` します。
1. 一連の仕様を使用し `TimeRange` て、クラスのインスタンスを設定 `TimeRangeCollection` します。
1. インスタンスから取得できるMetadataインスタンスを `TimeRangeCollection` メソッド(インター `replaceCurrentItem` フェイスの一部)に渡 `MediaPlayer` します。
1. TVSDKがPREPARED状態に移行するのを待ちます。このとき、コールバックがトリガーさ `PlaybackEventListener#onPrepared` れるのを待ちます。
1. メソッド(インターフェイスの一 `play()` 部)を呼び出して、ビデオ再生 `MediaPlayer` を開始します。

* タイムラインの競合の処理：一部の仕様が再生タイムライン上で重な `TimeRange` っている場合があります。 例えば、指定に対応する開始位置の値が、既に配置さ `TimeRange` れている終了位置の値より低い場合があります。 この場合、TVSDKは、タイムラインの競合を避けるために、問題のある指定の開 `TimeRange` 始位置を自動的に調整します。 この調整により、新しい要素は元々指定され `TimeRange` ていたよりも短くなります。 調整が非常に長く、長さが0ミリ秒になると、TVSDKは `TimeRange` 問題のある仕様を黙って削除し `TimeRange` ます。

* カスタ `TimeRange` ム広告の時間の仕様が提供されると、TVSDKは、これらを広告の時間内にグループ化された広告に変換しようとします。 TVSDKは、隣接する仕様を探し `TimeRange` 、それらを別々の広告の時間にクラスタリングします。 他の時間範囲に隣接しない時間範囲がある場合は、単一の広告を含む広告の時間に変換されます。

* 読み込まれるメディアプレイヤー項目がVODアセットを指していると見なされます。 TVSDKは、カスタム広告マーカー機能のコンテキストでのみ使用できる仕様を含むメタデータを持つメディアリソースを、アプリケーションが読み込もうとするたびに、これをチェックします。 `TimeRange` 基になるアセットのタイプがVODでない場合、TVSDKライブラリは例外をスローします。

* カスタム広告マーカーを扱う場合、TVSDKは、(Adobe Primetime ad decisioning（旧称Auditude）または他の広告プロビジョニングシステムを介して)他の広告解決メカニズムを非アクティブにします。 TVSDKが提供する様々な広告リゾルバーモジュールのいずれか、またはカスタム広告マーカーメカニズムのいずれかを使用できます。 カスタム広告マーカーAPIを使用する場合、広告コンテンツは既に解決済みと見なされ、タイムラインに配置されています。
>
><!--<a id="example_639BD1B66CE74F3DB65ED06CAD23EB09"></a>-->


次のコードスニペットは、3つの仕様のセットをカスタム広告マーカ `TimeRange` ーとしてタイムラインに配置する簡単な例を示しています。

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
