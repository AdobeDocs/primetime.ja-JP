---
description: HLS ストリームの設定と再生操作を処理する PlaybackManager を作成します。 他の設定は必要ありません。
title: ビデオ再生を有効にする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# ビデオ再生を有効にする {#enable-video-playback}

HLS ストリームの設定と再生操作を処理する PlaybackManager を作成します。 他の設定は必要ありません。

1. 次のコードがに存在することを確認して、メディアプレーヤーオブジェクトを作成します。 [!DNL PlayerFragment.java]:

   ```java
   private MediaPlayer createMediaPlayer() { 
           MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
           return mediaPlayer;
   ```

   <!-- I've duplicated this information. It also exists in the PlayerFragment section, just before the Feature manager section. I figured that I should have it here as well, in case they jump directly to this section.-->

1. を使用して再生マネージャーを作成する `ManagerFactory`:

   ```java
   playbackManager = ManagerFactory.getPlaybackManager(config, mediaPlayer);
   ```

1. の実装 `PlaybackManagerEventListener` （内） `PlayerFragment` 再生イベントを処理するには：

   ```java
   private final PlaybackManagerEventListener playbackManagerEventListener =  
     new PlaybackManagerEventListener() 
   ```

1. イベントリスナーを `PlayerFragment`:

   ```
   playbackManager.addEventListener(playbackManagerEventListener);
   ```

1. ビデオリソースを設定します。

   ```
   playbackManager.setupVideo(url, adsManager); 
   ```

1. コントロールバーの操作を `PlayerFragment`:

   ```
   controlBar.pressPlay() { 
       playbackManager.play();  
   }
   ```

## 関連する API ドキュメント {#related-api-documentation}

* [クラス PlaybackManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.html)
* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)
* [mediacore.utils.TimeRange](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/utils/TimeRange.html)
* [mediacore.BufferControlParameters](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/BufferControlParameters.html)
* [mediacore.MediaPlayer.PlayerState](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/MediaPlayer.PlayerState.html)
