---
description: この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。
title: タイムラインへのTimeRange広告マーカーの配置
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# TimeRange広告マーカーをタイムラインに配置{#place-timerange-ad-markers-on-the-timeline}

この例では、再生タイムラインにTimeRange指定を含めるための推奨される方法を示します。

1. 帯域外の広告位置情報を`TimeRange`仕様（つまり、`TimeRange`クラスのインスタンス）のリストに変換します。
1. `TimeRange`仕様のセットを使用して、`TimeRangeCollection`クラスのインスタンスを設定します。
1. `TimeRangeCollection`インスタンスから取得できるMetadataインスタンスを`replaceCurrentItem`メソッド（MediaPlayerインターフェイスの一部）に渡します。
1. `PlaybackEventListener#onPrepared`コールバックがトリガーされるのを待って、TVSDKが`PREPARED`状態にトランジションするのを待ちます。
1. `play()`メソッド（`MediaPlayer`インターフェイスの一部）を呼び出して、開始ビデオを再生します。

* タイムラインの競合を処理する：一部の`TimeRange`仕様が再生タイムラインで重なる場合があります。 例えば、`TimeRange`仕様に対応する開始位置の値が、既に配置されている終了位置の値より小さい場合があります。 この場合、TVSDKは、タイムラインの競合を回避するために、不適切な`TimeRange`仕様の開始位置をサイレントに調整します。 この調整により、新しい`TimeRange`は、元々指定された値より短くなります。 調整が過剰に行われ、長さ0ミリ秒の`TimeRange`が発生すると、TVSDKは問題の`TimeRange`仕様を黙ってドロップします。
* カスタム広告の時間の`TimeRange`指定が提供されると、TVSDKは、これらの指定を広告の時間内にグループ化された広告に変換しようとします。 TVSDKは、隣接する`TimeRange`仕様を探し、それらを別々の広告の時間にクラスター化します。 他の時間範囲に隣接しない時間範囲がある場合は、単一の広告を含む広告の時間に変換されます。
* 読み込まれるメディアプレイヤー項目は、VODアセットを指していると見なされます。 TVSDKは、カスタム広告マーカー機能のコンテキストでのみ使用できる`TimeRange`仕様をメタデータに含むメディアリソースを読み込もうとするたびに、この項目をチェックします。 基になるアセットのタイプがVODでない場合、TVSDKライブラリは例外をスローします。
* カスタム広告マーカーを処理する場合、TVSDKは、(Adobe Primetime広告決定（旧称Auditude）または他の広告プロビジョニングシステムを介した)他の広告解決メカニズムを非アクティブにします。 TVSDKが提供する様々な広告リゾルバーモジュールのいずれか、またはカスタム広告マーカーメカニズムのいずれかを使用できます。 カスタム広告マーカーAPIを使用する場合、広告コンテンツは既に解決済みで、タイムライン上に配置されていると見なされます。

次のコードスニペットに、カスタム広告マーカーとして3つのTimeRange指定をタイムラインに配置する簡単な例を示します。

```java>
// Assume that the 3 timerange specs are obtained through external means: CMS, etc. 
// Use these 3 timerange specs to populate the TimeRangeCollection instance 
TimeRangeCollection timeRanges = new TimeRangeCollection();  
timeRanges.addTimeRange(new TimeRange(0,10000)); 
timeRanges.addTimeRange(new TimeRange(15000,20000)); 
timeRanges.addTimeRange(new TimeRange(25000,30000)); 
 
// create and configure a MediaResource instance 
MediaResource mediaResource =  
  MediaResource.createFromUrl("www.example.com/video/test_video.m3u8",  
                               timeRanges.toMetadata(null)); 
 
// prepare the content for playback by creating 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentItem(mediaResource); 
// wait for TVSDK to reach the PREPARED state 
... 
MediaPlayer.PlaybackEventListener playbackEventListener = new 
  MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // TVSDK in in the PREPARED state. We are allowed to start the playback  
        mediaPlayer.play(); 
    } 
} 
```
