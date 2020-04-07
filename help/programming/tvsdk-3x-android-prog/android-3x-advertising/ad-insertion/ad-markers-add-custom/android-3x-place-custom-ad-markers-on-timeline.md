---
description: この例は、再生タイムラインにカスタム広告マーカーを含める推奨方法を示しています。
seo-description: この例は、再生タイムラインにカスタム広告マーカーを含める推奨方法を示しています。
seo-title: タイムラインへのカスタム広告マーカーの配置
title: タイムラインへのカスタム広告マーカーの配置
uuid: 47e31a97-e5da-46f3-bdcc-327c159c4355
translation-type: tm+mt
source-git-commit: 2a6ea34968ee7085931f99a24dfb23d097721b89

---


# タイムラインへのカスタム広告マーカーの配置 {#place-custom-ad-markers-on-the-timeline}

この例は、再生タイムラインにカスタム広告マーカーを含める推奨方法を示しています。

1. 帯域外の広告配置情報をクラスのリスト/配列に変換し `RepaceTimeRange` ます。
1. クラスのインスタンス `CustomRangeMetadata` を作成し、そのメソッ `setTimeRangeList` ドを引数としてリスト/配列と共に使用して、時間範囲のリストを設定します。
1. このメソッド `setType` を使用して、タイプをに設定しま `MARK_RANGE`す。
1. このメソッドを `MediaPlayerItemConfig.setCustomRangeMetadata` 引数としてイ `CustomRangeMetadata` ンスタンスと共に使用し、カスタム範囲のメタデータを設定します。
1. 新しいリソー `MediaPlayer.replaceCurrentResource` スを現在のリソ `MediaPlayerItemConfig` ースに設定するには、インスタンスを引数としてメソッドを使用します。
1. プレイヤーが `STATE_CHANGED` イベント中であることが報告されるまで待 `PREPARED` ちます。
1. 開始ビデオの再生を呼び出しま `MediaPlayer.play`す。

次に、この例のタスクを完了した結果を示します。

* 例えば、 `ReplaceTimeRange` aの開始位置が既に配置されている終了位置よりも前にある場合、TVSDKは競合を避けるために、問題の開始を何も示さずに調 `ReplaceTimeRange``ReplaceTimeRange` 整します。

   これにより、調整後の画像が元々指定 `ReplaceTimeRange` されていた画像より短くなります。 調整の結果期間がゼロになった場合、TVSDKは問題を黙ってドロップしま `ReplaceTimeRange`す。

* TVSDKは、隣接する時間範囲を探してカスタム広告の時間を探し、それらを別々の広告の時間にクラスター化します。

他の時間範囲に隣接しない時間範囲は、単一の広告を含む広告の時間に変換されます。

* コンテキストカスタム広告マーカーでのみ使用できる設定を含むメディアリソースをアプリケーションが読み込もうとすると、基になるアセットのタイプがVODでない場合、TVSDKは例外をスローします。 `CustomRangeMetadata`

* カスタム広告マーカーを扱う場合、TVSDKは他の広告解決メカニズム（Adobe Primetime ad decisioningなど）を非アクティブにします。

   TVSDKの広告リゾルバーモジュールや、カスタム広告マーカーメカニズムを使用できます。 カスタム広告マーカーを使用する場合、広告コンテンツは解決されたと見なされ、タイムラインに配置されます。

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
