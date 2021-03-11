---
description: この例は、カスタム広告マーカーを再生タイムラインに含めるための推奨される方法を示しています。
title: カスタム広告マーカーをタイムラインに配置する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# タイムライン{#place-custom-ad-markers-on-the-timeline}にカスタム広告マーカーを配置する

この例は、カスタム広告マーカーを再生タイムラインに含めるための推奨される方法を示しています。

1. 帯域外の広告配置情報を`RepaceTimeRange`クラスのリスト/配列に変換します。
1. `CustomRangeMetadata`クラスのインスタンスを作成し、`setTimeRangeList`メソッドとリスト/配列を引数として使用して、時間範囲のリストを設定します。
1. `setType`メソッドを使用して、型を`MARK_RANGE`に設定します。
1. `MediaPlayerItemConfig.setCustomRangeMetadata`メソッドを`CustomRangeMetadata`インスタンスの引数として使用し、カスタム範囲メタデータを設定します。
1. `MediaPlayer.replaceCurrentResource`メソッドを`MediaPlayerItemConfig`インスタンスを引数として使用し、新しいリソースを現在のリソースに設定します。
1. `STATE_CHANGED`イベントが`PREPARED`状態にあると報告されるのを待ちます。
1. `MediaPlayer.play`を呼び出してビデオを開始再生します。

次に、この例でタスクを完了した結果を示します。>
* 例えば、`ReplaceTimeRange`が再生タイムライン上で別の`ReplaceTimeRange`と重なる場合、の開始位置が既に配置されている終了位置より前にあると、TVSDKは、競合を回避するために、問題の`ReplaceTimeRange`の開始を静かに調整します。

   これにより、調整された`ReplaceTimeRange`が、元々指定された値より短くなります。 調整の結果、長さが0になると、TVSDKは問題の`ReplaceTimeRange`を黙ってドロップします。

* TVSDKは、カスタム広告の時間に関して、隣接する時間範囲を探し、それらを別々の広告の時間にクラスター化します。

   他の時間範囲に隣接しない時間範囲は、単一の広告を含む広告の時間に変換されます。
* コンテキストカスタム広告マーカーでのみ使用できる設定`CustomRangeMetadata`を含むメディアリソースを読み込もうとすると、基になるアセットのタイプがVODでない場合、TVSDKは例外をスローします。
* カスタム広告マーカーを処理する場合、TVSDKは他の広告解決メカニズム(Adobe Primetime広告決定など)を非アクティブにします。

   TVSDKの広告リゾルバーモジュールや、カスタム広告マーカーメカニズムを使用できます。 カスタム広告マーカーを使用する場合、広告コンテンツは解決済みと見なされ、タイムラインに配置されます。

次のコードスニペットでは、3つの時間範囲をカスタム広告マーカーとしてタイムラインに配置します。

```java
// Assume that the 3 time ranges are obtained through external means 
// Use them to populate the ReplaceTimeRange instance 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 0)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.MARK_RANGE); 
 
//Create a MediaResource instance 
MediaResource mediaResource = MediaResource.createFromUrl( 
        "www.example.com/video/test_video.m3u8", timeRanges.toMedatada(null)); 
 
// Create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// Prepare the content for playback by calling replaceCurrentResource 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentResource(mediaResource, config); 
 
// wait for TVSDK to reach the PREPARED state 
mediaPlayer.addEventListener(MediaPlayerEvent.STATE_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
 
    if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
        // TVSDK is in the PREPARED state, so start the playback  
        mediaPlayer.play(); 
    } 
    ... 
}
```
