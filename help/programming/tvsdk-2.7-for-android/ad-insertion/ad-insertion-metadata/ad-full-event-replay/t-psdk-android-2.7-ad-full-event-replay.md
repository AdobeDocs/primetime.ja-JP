---
description: フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されていることを確認する手順をアプリケーションで実行する必要があります。
seo-description: フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されていることを確認する手順をアプリケーションで実行する必要があります。
seo-title: フルイベント再生での広告の有効化
title: フルイベント再生での広告の有効化
uuid: 69244069-ef61-42e4-b2f5-62ae2561d9e1
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# フルイベント再生で広告を有効にする{#enable-ads-in-full-event-replay-overview}

フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されていることを確認する手順をアプリケーションで実行する必要があります。

ライブコンテンツの場合、TVSDKは、マニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VODコンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、ライブマニフェストに`EXT-X-ENDLIST`タグが追加されます。 HLSの場合、`EXT-X-ENDLIST`タグは、ストリームがVODストリームであることを意味します。 広告を正しく挿入するために、TVSDKは、このストリームを一般的なVODストリームと自動的に区別できません。

アプリケーションは、TVSDKに対して、コンテンツがライブかVODかを`AdSignalingMode`を指定して通知する必要があります。

FERストリームの場合、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストは、Adobe Primetimead decisioningサーバーで提供しないでください。 これは、VODコンテンツの一般的なプロセスです。 代わりに、別のシグナリングモードを指定することで、TVSDKは、FERマニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告の時間をリクエストします。 このプロセスは、ライブ/DVRコンテンツと似ています。

>[!TIP]
>
>キューポイントに関連付けられている各リクエストに加えて、TVSDKは、プリロール広告に対して追加の広告リクエストを行います。

1. vCMSなどの外部ソースから、使用する必要があるシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、`AdvertisingMetadata.setSignalingMode`を使用して`AdSignalingMode`を指定します。

   有効な値は`DEFAULT`、`SERVER_MAP`、`MANIFEST_CUES`です。

   >[!IMPORTANT]
   >
   >`prepareToPlay`を呼び出す前に、広告シグナリングモードを設定する必要があります。 TVSDK開始が広告を解決してタイムラインに配置した後、広告シグナリングモードに対する変更は無視されます。 `AuditudeSettings`オブジェクトを作成する際にモードを設定します。

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
