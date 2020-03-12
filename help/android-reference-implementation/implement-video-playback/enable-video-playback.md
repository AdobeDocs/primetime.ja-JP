---
description: HLSストリームの設定と再生操作を処理するPlaybackManagerを作成します。 その他の設定は不要です。
seo-description: HLSストリームの設定と再生操作を処理するPlaybackManagerを作成します。 その他の設定は不要です。
seo-title: ビデオ再生の有効化
title: ビデオ再生の有効化
uuid: ddc0defa-c40f-4ee6-a69f-d5eeca6c2fce
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# ビデオ再生の有効化 {#enable-video-playback}

HLSストリームの設定と再生操作を処理するPlaybackManagerを作成します。 その他の設定は不要です。

1. 次のコードがに存在することを確認して、メディアプレイヤーオブジェクトを作成しま [!DNL PlayerFragment.java]す。

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. 次の手順で再生マネージャーを作成しま `ManagerFactory`す。

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. でを実装し `PlaybackManagerEventListener` て、再 `PlayerFragment` 生イベントを処理します。

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. 次の場所にイベントリスナーを登録しま `PlayerFragment`す。

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. ビデオリソースの設定：

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. コントロールバーの操作は、次の場所で設定しま `PlayerFragment`す。

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## 関連するAPIドキュメント {#related-api-documentation}

* [PlaybackManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)