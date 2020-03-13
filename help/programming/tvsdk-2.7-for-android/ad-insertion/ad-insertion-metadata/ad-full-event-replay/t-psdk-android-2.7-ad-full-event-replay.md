---
description: フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されるように、アプリケーションで手順を実行する必要があります。
seo-description: フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されるように、アプリケーションで手順を実行する必要があります。
seo-title: フルイベント再生での広告の有効化
title: フルイベント再生での広告の有効化
uuid: 69244069-ef61-42e4-b2f5-62ae2561d9e1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# フルイベント再生での広告の有効化 {#enable-ads-in-full-event-replay-overview}

フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されるように、アプリケーションで手順を実行する必要があります。

ライブコンテンツの場合、TVSDKは、マニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VODコンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、ラ `EXT-X-ENDLIST` イブマニフェストにタグが追加されます。 HLSの場合、タグは、ス `EXT-X-ENDLIST` トリームがVODストリームであることを意味します。 広告を正しく挿入するために、TVSDKは、このストリームを通常のVODストリームと自動的に区別することはできません。

アプリケーションは、コンテンツがライブかVODかをTVSDKに通知する必要があります。そのためには、 `AdSignalingMode`

FERストリームの場合、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストは、Adobe Primetime ad decisioningサーバーで提供されません。 これは、VODコンテンツの一般的なプロセスです。 代わりに、別のシグナリングモードを指定することで、TVSDKはFERマニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告の時間をリクエストします。 このプロセスは、ライブ/DVRコンテンツに似ています。

>[!TIP]
>
>キューポイントに関連付けられた各リクエストに加えて、TVSDKは、プリロール広告に対して追加の広告リクエストを作成します。

1. vCMSなどの外部ソースから、使用するシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、を使用して `AdSignalingMode` を指定しま `AdvertisingMetadata.setSignalingMode`す。

   有効な値は、、 `DEFAULT`およ `SERVER_MAP`びです `MANIFEST_CUES`。

   >[!IMPORTANT]
   >
   >呼び出す前に、広告シグナリングモードを設定する必要がありま `prepareToPlay`す。 TVSDKが広告の解決を開始し、広告をタイムラインに配置した後、広告シグナリングモードに対する変更は無視されます。 オブジェクトの作成時にモードを設定 `AuditudeSettings` します。

1. 再生を続けます。

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
