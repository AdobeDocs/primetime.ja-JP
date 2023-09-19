---
description: フルイベント再生 (FER) は、ライブ/DVR アセットとして機能する VOD アセットなので、広告が正しく配置されるように、アプリケーションが手順を実行する必要があります。
title: フルイベント再生での広告の有効化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# フルイベント再生での広告の有効化 {#enable-ads-in-full-event-replay-overview}

フルイベント再生 (FER) は、ライブ/DVR アセットとして機能する VOD アセットなので、広告が正しく配置されるように、アプリケーションが手順を実行する必要があります。

ライブコンテンツの場合、 TVSDK はマニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VOD コンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、 `EXT-X-ENDLIST` タグがライブマニフェストに追加されます。 HLS の場合、 `EXT-X-ENDLIST` タグは、ストリームが VOD ストリームであることを意味します。 広告を正しく挿入するために、 TVSDK は、このストリームを一般的な VOD ストリームと自動的に区別することはできません。

コンテンツがライブか VOD かを TVSDK に知らせるには、 `AdSignalingMode`.

FER ストリームの場合、Adobe Primetime Ad Decisioning サーバーは、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストを提供しないでください。 これは、VOD コンテンツの一般的な手順です。 代わりに、異なるシグナリングモードを指定することで、 TVSDK は FER マニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告ブレークをリクエストします。 このプロセスは、ライブ/DVR コンテンツに似ています。

>[!TIP]
>
>TVSDK は、キューポイントに関連付けられた各リクエストに加えて、プリロール広告に対する追加の広告リクエストを作成します。

1. vCMS などの外部ソースから、使用するシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、 `AdSignalingMode` 使用によって `AdvertisingMetadata.setSignalingMode`.

   有効な値は次のとおりです。 `DEFAULT`, `SERVER_MAP`、および `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >を呼び出す前に、広告シグナリングモードを設定する必要があります `prepareToPlay`. TVSDK が広告の解決を開始し、広告をタイムラインに配置し始めると、広告シグナリングモードへの変更は無視されます。 モードを設定する ( `AuditudeSettings` オブジェクト。

1. 再生を続行します。

<!--<a id="example_6DECA71C3C3B4551805C09A80686552F"></a>-->

```java
MediaPlayer mediaPlayer =  
  new MediaPlayer(getActivity.().getApplicationContext()); 
 
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings.setSignalingMode(AdSignalingMode.MANIFEST_CUES); 
auditudeSettings.setDomain("your-auditude-domain"); 
auditudeSettings.setZoneId("your-auditude-zone-id"); 
auditudeSettings.setMediaId("your-media-id"); 
// set additional targeting parameters or custom parameters 
 
MediaPlayerItemConfig itemConfig =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
MediaResource mediaResource =  
  new MediaResource("https://example.com/media/test_media.m3u8",  
                    MediaResource.Type.HLS, Metadata); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
            // TVSDK is in the PREPARED state, so start the playback 
            mediaPlayer.play(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.COMPLETE ) { 
            // playback has reached the end of stream ( ads included ) 
            // if we want to rewind we can call 
            mediaPlayer.seek(mediaPlayer.getSeekableRange().getBegin()); 
        } 
    } 
}); 
 
mediaPlayer.replaceCurrentResource(mediaResource, itemConfig); 
```
