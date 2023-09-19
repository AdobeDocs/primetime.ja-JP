---
description: この例では、再生タイムラインにカスタム広告マーカーを含める推奨方法を示します。
title: タイムラインへのカスタム広告マーカーの配置
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# タイムラインへのカスタム広告マーカーの配置 {#place-custom-ad-markers-on-the-timeline}

この例では、再生タイムラインにカスタム広告マーカーを含める推奨方法を示します。

1. 帯域外広告配置情報を `RepaceTimeRange` クラス。
1. のインスタンスを作成 `CustomRangeMetadata` クラスを使用し、その `setTimeRangeList` メソッドの時間範囲リストを設定するための引数として、list/array を使用します。
1. 使用方法 `setType` メソッドを使用してタイプをに設定します。 `MARK_RANGE`.
1. 以下を使用します。 `MediaPlayerItemConfig.setCustomRangeMetadata` メソッドの `CustomRangeMetadata` インスタンスを引数として使用し、カスタム範囲メタデータを設定します。
1. 以下を使用します。 `MediaPlayer.replaceCurrentResource` メソッドの `MediaPlayerItemConfig` 新しいリソースを現在のリソースに設定するための引数としてインスタンスを指定します。
1. 待機： `STATE_CHANGED` イベント。プレーヤーが `PREPARED` 状態。
1. を呼び出してビデオの再生を開始する `MediaPlayer.play`.

この例のタスクを完了すると、次のようになります。 /
* 次の場合、 `ReplaceTimeRange` は、再生タイムライン上で別のもの ( 例えば、 `ReplaceTimeRange` が、既に配置されている終了位置より前にある場合、 TVSDK は、問題の発生を静かに調整します `ReplaceTimeRange` 紛争を避けるために

  これにより、調整された `ReplaceTimeRange` 最初に指定された値より短い。 調整の期間がゼロになった場合、 TVSDK は、問題を黙って破棄します `ReplaceTimeRange`.

* TVSDK は、カスタム広告の時間に隣接する時間範囲を探し、それらを別々の広告の時間にクラスター化します。

  他の時間範囲と隣接しない時間範囲は、単一の広告を含む広告の時間に変換されます。
* 設定にが含まれるメディアリソースを読み込もうとした場合 `CustomRangeMetadata` これは、コンテキストのカスタム広告マーカーでのみ使用でき、基になるアセットのタイプが VOD でない場合、 TVSDK は例外をスローします。
* カスタム広告マーカーを扱う場合、 TVSDK は、他の広告解決メカニズム (Adobe Primetime ad decisioning など ) を非アクティブ化します。

  TVSDK の広告リゾルバーモジュールや、カスタム広告マーカーメカニズムを使用できます。 カスタム広告マーカーを使用する場合、広告コンテンツは解決されたものと見なされ、タイムラインに配置されます。

次のコードスニペットは、3 つの時間範囲をカスタム広告マーカーとしてタイムラインに配置します。

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
