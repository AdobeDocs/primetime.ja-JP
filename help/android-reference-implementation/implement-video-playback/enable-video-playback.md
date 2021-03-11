---
description: HLSストリームの設定と再生操作を処理するPlaybackManagerを作成します。 その他の設定は不要です。
title: ビデオ再生の有効化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# ビデオ再生を有効にする{#enable-video-playback}

HLSストリームの設定と再生操作を処理するPlaybackManagerを作成します。 その他の設定は不要です。

1. [!DNL PlayerFragment.java]に次のコードが存在することを確認して、メディアプレイヤーオブジェクトを作成します。

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. `ManagerFactory`を使用して再生マネージャーを作成します。

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. `PlaybackManagerEventListener`を`PlayerFragment`に実装して、再生イベントを処理します。

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. イベントリスナーを`PlayerFragment`に登録します。

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. ビデオリソースの設定：

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. `PlayerFragment`のコントロールバー操作を設定します。

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## 関連するAPIドキュメント{#related-api-documentation}

* [PlaybackManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)